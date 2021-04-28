# Questions & answers related to AIS, Postman Samples, RA, MobileID, Billing, etc.

**1.	Die Firma X will jetzt von AIS Preprod auf die AIS Prod umstellen da sie mit dem Testen fertig sind. Kannst du mir bitte sagen 
von vertraglichen her welche Schritte die Firma X machen muss und wie das im Allgemeinen abläuft, was muss da unterschrieben werden, etc.?**
 
* Sales, in diesem Fall Marcel (Marcel.Kurz@swisscom.com), gibt uns den Auftrag, den gewünschten Vertrag zu erstellen: 
* https://collaboration.swisscom.com/communities/swisscom-digital-certificate-services/SDCS_Collab/Forms/AllItems.aspx?RootFolder=%2Fcommunities%2Fswisscom%2Ddigital%2Dcertificate%2Dservices%2FSDCS%5FCollab%2F10%5FAIS%5FOperations%2FAuftr%C3%A4geSales&FolderCTID=0x0120009F4F9BE777BD6F4F823759ED2E7DEC76&View=%7BE5CCB974%2D9EE8%2D4087%2DAE09%2DB90602A14D5E%7D 

* Des Weiteren ist zu klären ob die Firma X erst einen Testaccount hat. 
 
 
**2.  Abrechnung Modelle für den MobileID/AIS Benutzer: wie läuft das ab? Welches Modelle gibt es? Wie wird die Signatur Flatrate benutzt? Kann 
der Benutzer nach dem er X mal (z.B. 3 mal) signiert hat weiter die Flatrate benutzen? Was sind die Rahmenbedingungen bzgl. entsendenden Kosten, 
wie läuft das spezifisch ab?**

* Die Abrechnungsvariante wählt der Kunde im entsprechenden Vertrag, die Möglichkeit von Abrechnung pro User/Monat steht aber nur noch Resellern oder bei Bestellung via Partner zur Verfügung, für Endkunden gibt es nur noch "pro Signatur". Du findest sämtliche Vertragstemplates im DMIS: 
* https://internal.bizdocs.swisscom.com/dmis/start/SitePages/ProductDetail.aspx?PURL=https://internal.bizdocs.swisscom.com/dmis/1000255-All-in-Signing-Service
 
 
**3.	Nach dem für einen Benutzer ein AIS Signatur-Link generiert wurde um dann mit diesen signieren zu können, wie lange ist dieser Link gültig, wie viele tage?**
 
* Falls damit die SAS Bestätigung per SAS gemeint ist, dann findest du die Antwort in der Installation Guidance, Abschnitt 5.7.3: ist konfigurierbar, Default sind 10 Minuten. Mehr weiß ich dazu nicht, da wir für unsere Testumgebung keine SAS-Anbindung haben und das deshalb nicht testen.
* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf
https://trustservices.swisscom.com/downloads/
 
 
**4.	Kosten entstehen bei der Video Authentifizierung nach dem der User sich authentifiziert hat oder nach dem dieser AIS Link generiert wurde? Die Firma X 
will genau wissen wann kosten auf sie zukommen.**
 
* Bitte bei Marietta Heule (Marietta.Heule@swisscom.com) und/oder Marcel (Marcel.Kurz@swisscom.com) im Detail nachfragen. 

**5.	Please check in the Postman samples that : is replaced with .**
 
* For example if you have in the Postman Sample: "sc:SignatureStandard" replace it with "sc.SignatureStandard".
 
 
**6.	Bei einen Template basierten Call muss immer ein Benutzer Name angegeben werde oder kann man da auch einen Namen Place holder benutzen? Ist es dann später
bei der Signierung möglich den Namen noch zu ergänzen?**
 
* Ich nehme an, du meinst die Platzhalter für Werte aus dem RA-Evidence im Subject von On-demand-Signaturen. Außer dass dem Escaping anhand der Regeln für DNs (RFC 2253) ist das im Wesentlichen eine Textersetzung. Die Templates bauen darauf auf und geben häufig gebrauchte Subjects mit Platzhaltern vor. Unsere Dokumentation dazu findest du in den Abschnitten 5.9.2 und 5.9.3 in der Installation Guidance. Zu deiner eigentlichen Frage: ja, man kann ein Subject mit Platzhaltern zusammenstellen und GIVENNAME oder CN dann mit einem eigenen Wert belegen.
* https://documents.swisscom.com/product/1000255-Digital_Signing_Service/Documents/Reference_Guide/Reference_Guide-All-in-Signing-Service-en.pdf
 
 
**7. Wenn der Benutzer Name bei einen Signatur-Request übergeben wird, wird der Name des Benutzer überprüft oder ist das egal? Die Frage geht in der 
Richtung, was passiert wenn der Benutzer seinen Namen falsch angegeben hat. Deshalb ist für eine erfolgreiche Signatur relevant das der Name richtig angegeben ist, oder?** 
 
* Es gibt zwei Prüfungen: Zum einen muss das fertige Subject zum DN-Pattern des On-demand Services passen. Falls es eine Qualifizierte Signatur ist, wird das Subject zudem dem RAS zur Prüfung gegeben ("Evidence Verify Call"). Wie die DN-Patterns bei euch aussehen und was der RAS genau prüft, kann man hier nachschauen unter Smart Registration Service.
* https://trustservices.swisscom.com/downloads/
 
 
**8.	Die Objekt vs. Objekten-Liste Problem, ist das zurzeit im AIS behoben? Man muss da an dieser Stelle immer bei dem Request eine Objekten-Liste mitsenden, oder? 
Wie funktioniert das zurzeit?**
 
* Nein. In AIS ist alles wie gehabt. Soweit ich weiß, in den PDFBox Client gibt es dafür einen Workaround. 
* Es geht nicht um den Request, sondern um die Response. Im Schema dafür gibt es einige Properties, die eine Liste sind -- so zum Beispiel die Liste der erstellten Signaturen oder die Liste der OCSP und CRL. Je nachdem, ob die kein, ein oder mehrere Elemente enthält, wird die Property im JSON als einzelner Wert oder als Liste von Werten serialisiert. Es sollte aber immer eine Liste sein. Wenn ich als Client mit der jeweiligen Property arbeiten will, muss ich deswegen immer zuerst prüfen, ob es ein einzelner Wert oder eine Liste von Werten ist. Deswegen geht die Welt nicht unter, es ist aber umständlich und ärgerlich. Mit SOAP gibt es dieses Problem nicht.
 
 
**9.	Bei einer Signatur ist es möglich für den Benutzer anzugeben ob er EIDAS oder ZertES werdenden will? In den JSON AIS Samples den wir haben kann ich das nicht gefunden. 
Wie ist es im AIS zurzeit implementiert? Eine kurze Beschreibung würde mir da viel weiter helfen.**
 
* Für die Signatur wählt der Client einen On-demand Service. Dieser verweist auf einen CA-Server. Der Level of Assurance und die Jurisdiktion für die Signatur wird aus dem Namen dieses CA-Servers abgeleitet. Wie, das ist unter anderem im Admin UI User Manual, Abschnitt 3.4.1 beschrieben. Die "Data Flow Issues" aktuel im bearbeitung bei uns, wollen genau das ändern, so dass diese Eigenschaften nicht mehr per Namenskonvention festgelegt sind, sondern explizit in der Datenbank landen. Nach der vorherigen Aussage zufolge kann man nicht EIDAS oder ZertES auswählen, wird dann sicherlich später einstellbar sein.

**10. POC Durchführung, auf was muss ich achten?**

* Ich muss eine Video Registrierung durchführen, dadurch kann ich nur in der EU signieren. 
* Das wird hier durchgeführt. 
* https://trustservices.swisscom.com/en/smart-registration-service/
* Ich muss mich im Swisscom Shop registrieren lassen, dadurch kann ich dann auch in der Schweiz signieren. 


