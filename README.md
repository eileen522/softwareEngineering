# Software Engineering e-portfolio on Selenium

## Was ist Selenium
Selenium ist ein weit verbreitetes Automatisierungswerkzeug für das Testen von Webanwendungen. Es ermöglicht Entwicklern und Testern, Tests von Webseiten über verschiedene Browser und Plattformen hinweg zu automatisieren und sicherzustellen, dass die Anwendung wie erwartet funktioniert. 

## UI-Testing
UI-Tests sind Tests, die die Benutzeroberfläche einer Anwendung überprüfen, um sicherzustellen, dass sie korrekt funktioniert. Man unterscheidet zwischen manuellen und automatisierten Tests. <br>
Das User Interface (UI) oder auch die Benutzeroberfläche bezieht sich auf den Teil einer Softwareanwendung, mit dem ein Benutzer interagieren kann. Es besteht aus 
einer Reihe von visuellen und interaktiven Elementen, die dem Benutzer helfen, Aufgaben auszuführen und Informationen zu erhalten. 
UI-Tests simulieren Benutzerinteraktionen, um sicherzustellen, dass alle Funktionen und Elemente der Benutzeroberfläche ordnungsgemäß funktionieren, einschließlich Schaltflächen, Eingabefelder, Menüs und andere Benutzeroberflächenelemente. Diese Tests werden häufig durchgeführt, um sicherzustellen, dass die Anwendung den Erwartungen der Benutzer entspricht und keine Probleme bei der Interaktion mit der Anwendung auftreten. <br> <br>
**Vorteile von UI-Testing** <br> 
• Defekte frühzeitig im Entwicklungsprozess zu erkennen, was das Beheben einfacher und weniger kostspielig macht. <br>
• Das Risiko von Fehlern und Problemen, die in der Produktion auftreten können, zu reduzieren, was zu einer besseren Stabilität und Zuverlässigkeit der Anwendung führt. <br> <br>
Die Automatisierung von UI-Testing mit beispielsweise Selenium spart zudem Zeit und Ressourcen. <br>
Die Bedeutung von UI-Tests kann nicht genug betont werden, da sie dazu beitragen, Probleme zu identifizieren und zu beheben, bevor sie die Endbenutzer erreichen und somit eine bessere User Experience bieten.

## Selenium
Selenium ist ein Open-Source-Automatisierungstool zum Testen von Webanwendungen. Es unterstützt verschiedene Programmiersprachen wie Java, Python, C# und mehr. Selenium ist darauf ausgelegt, Browseraktionen zu automatisieren und bietet eine Reihe von Funktionen zur Unterstützung von UI-Tests. Einige seiner Funktionen umfassen die Fähigkeit, Benutzeraktionen wie Klicken, Tippen und Scrollen zu simulieren, sowie die Fähigkeit, Webseiteninhalte, Formulare und andere UI-Elemente zu validieren. Selenium besteht aus mehreren Komponenten, die zusammenarbeiten, um UI-Tests durchzuführen. Selenium ist ein 
Dachprojekt und besteht aus folgenden Komponenten: 
1. Selenium WebDriver: Dies ist die Kernkomponente von Selenium, die eine 
Programmierschnittstelle zur Steuerung von Browsern und zur Ausführung 
von Testskripten bereitstellt. Selenium WebDriver kann dazu verwendet 
werden, um auf Webseiten zu navigieren und mit ihnen zu interagieren. Das 
Tool greift dazu auf die nativen Automatisierungsschnittstellen der Browser zu 
und stellt diese über die WebDriver Application Programming Interface (API) 
für verschiedene Programmiersprachen zur Verfügung. Wenn ein Test 
ausgeführt wird, interagiert der entsprechende Selenium Browser Driver (z.B. 
ChromeDriver) mit dem Browser, um die Anweisungen im Test auszuführen.
1. Selenium Grid: Ein Tool, mit dem Tests auf mehreren Browsern, 
Betriebssystemen und Geräten parallel ausgeführt werden können, um die 
Testgeschwindigkeit zu verbessern.
2. Selenium IDE: Eine integrierte Entwicklungsumgebung, die die Erstellung von 
Testskripten ohne Programmcode ermöglicht. Es handelt sich um ein Plugin 
für Firefox- und Chrome-Browser. Selenium IDE bietet mehrere nützliche 
Funktionen für UI-Tests, wie z.B. Aufzeichnung von Benutzerinteraktionen, 
Bearbeitung und Debugging von Testskripten sowie Export von Skripten in 
verschiedenen Programmiersprachen. Es ist ein ausgezeichnetes Werkzeug 
für Anfänger im Bereich UI-Tests und für die Erstellung von schnellen und 
einfachen Testskripten. Für komplexere Test-Szenarien wird jedoch die 
Verwendung von Selenium WebDriver empfohlen.
3. Selenium Remote Control: Auch Selenium 1, wird nicht mehr supported. 
Älteres Werkzeug, das größtenteils durch WebDriver ersetzt wurde. Es 
ermöglicht die Durchführung von UI-Tests durch die Übermittlung von 
Befehlen an den Browser, der auf einem anderen System ausgeführt wird.

## Praxis
[Selenium Dokumentation](https://www.selenium.dev/documentation/) <br> <br> 

1. Für die gewählte Programmiersprache die Selenium-Bibliothek installieren. [Überblick](https://www.selenium.dev/documentation/webdriver/getting_started/install_library/) 
2. WebDriver für den Browser, den man testen möchte, herunterladen und installieren. Beispiel: [ChromeDriver](https://chromedriver.chromium.org/downloads). Nach dem Herunterladen und Entpacken der Zip, kann man den Driver dann als Umgebungsvariable spezifizieren oder direkt im Code angeben. Die Angabe des Speicherorts im Code selbst hat den Vorteil, dass man keine Umgebungsvariablen auf dem System herausfinden muss, hat jedoch den Nachteil, dass der Code viel weniger flexibel wird. 

Testskript von der Präsentation ist hier zu finden. 

**Achtung** <br> 
Seit der Chrome-Version 111 gibt es Probleme eine Instanz des ChromeDrivers zu starten. Dies liegt daran, dass Selenium den Origin-Header bei einem Aufruf setzt. 
Dieser sagt aus woher eine Anfrage stammt und ist wichtig um Cross-Site-Request-Forgery (CSRF) zu verhindern. Ein Angriff auf ein System. Selenium scheint den 
Header so zu setzen, dass er nicht erkannt wird und zu Einschränkungen führt und die Seite nicht erkannt wird. Das wird gelöst durch die Erstellung des Drivers mit 
ChromeOptions. Diese werden so gesetzt, dass unbekannte Ursprünge nichtblockiert, sondern zugelassen werden. 

## Best Practices für Selenium-Testing
1. Die Wartung von Selenium-Testskripten ein fortlaufender Prozess, der 
Aufmerksamkeit und Mühe erfordert. Am besten nach jeder User Story mit UI-Anteil Selenium-Test erstellen und überprüfen ob alte noch funktionieren. (kann man auch durch CI/CD abdecken, z.B. mit Jenkins)
2. Wie immer beschreibende Namenskonventionen für Testfälle, Testdaten 
und Seitenobjekte wählen, um die Skripte lesbarer und verständlicher zu machen.
3. Vermeidung von festcodierten Werten in den Testskripten (wie IDs, XPaths, etc) 
und stattdessen Variablen oder Konfigurationsdateien verwenden, um die 
Skripte flexibler zu machen.
4. Verwendung expliziter statt impliziter Wartezeiten, da diese genauer und 
vorhersehbarer sind
5. Schreiben der Tests nach [Page Object Pattern](https://www.selenium.dev/documentation/test_practices/encouraged/page_object_models/). Einem Entwurfsmuster, das 
zwischen Testcode Seitenspezifischem, wie dem finden von WebElementen 
trennt. Also eine Klasse mit Methoden zur Erstellung von WebDriver, dem 
finden von Elementen, etc. – bessere Wartbarkeit
<br> <br> <br> 
**kleine Erinnerung** <br> 
Selenium-Tests sind viel Bastelei und manchmal echt nervig. Selenium ist aber trotzdem ein gutes Tool für UI-Testing, also lohnt es sich dran zu bleiben. :)
