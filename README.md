# KI-Agent-skills
Sammelort für "Skills" Dateien für KI-Agenten und Chatbots. Bestehen üblicherweise aus Makrdown Text-Dateien (`.md`)

Diese Skills können in verschiedene Agenten/Harnesses eingefügt werden, wie zum Beispiel Claude code oder Opencode. 
Durch das erstellen von Skills, die:

* an unsere Bedürfnisse angepasst sind,

* unseren aktuellen Lernstand miteinbeziehen

* und wissen mit welcher Hardware und Software wir arbeiten, 

können wir KI besser in unseren Lern-Workflow integrieren.

## stm32-arduino-coder

Dieser Skill dient als spezialisierter **Embedded Coder** für die Entwicklung von Firmware-Sketches (`.ino` Format) für eingebettete Systeme auf Basis des **STM32 Nucleo 64 L152RE** Mikrocontrollers. Er hält sich strikt an den Workflow der Arduino IDE, während er gleichzeitig einen tiefen Blick auf die C-Programmierung ermöglicht.

**Kernprinzipien:**
*   **Verteidigungsprogrammierung (Defensive Coding):** Das Skript verlangt immer eine umfassende **Peripherie-Manifestdatei**, bevor mit dem Code begonnen wird.
*   **Effizienz:** Es priorisiert die Verwendung von Interrupts gegenüber Polling für zeitkritische Ereignisse, um deterministische Zeitsteuerung zu gewährleisten.
*   **Zuverlässigkeit:** Bei unsicherer Information (z.B. Pinbelegung, Library-Funktionen) zwingt der Skill das nutzende KI-Modell, einen strengen **Forschungsnachweis** über Web-Suchen und das Auslesen von Datasheets zu erbringen, bevor eine Tatsache als gegeben angenommen wird.

Zusammenfassend ist dies ein Tool für den Mikrokontroller, den wir (bisher) im Unterricht verwenden.
