## 💡 Boilerplate Code Snippets & Templates

These snippets demonstrate the required output formats and provide reusable structural elements for any project using this skill.

### 1. Basic Wiring Guide Template (Table Format)
| Component | Pin Function | STM32 Nucleo Pin (GPIO #) | Connection Type | Notes |
| :--- | :--- | :--- | :--- | :--- |
| Sensor Power | VCC $\rightarrow$ 3.3V | N/A | Power | Must confirm voltage level from datasheet. |
| LCD Data Line | SDA | PB7 (I2C1) | I2C Bus | Check pull-up resistor requirements. |
| Button A | Signal Pin | PA0 (GPIO D1) | Digital Input | Use hardware pull-up/down if possible. |

### 2. Pseudo-Code Template: State Machine Example (For Prototyping)
```pseudo
// STATE MACHINE for HVAC Control
DEFINE ENUM States {
    INITIALIZING,
    READING_TEMP,
    CHECKING_THRESHOLD,
    ACTUATING_HEAT,
    WAITING_FOR_COOLDOWN
}

CurrentState = INITIALIZING

FUNCTION loop() {
    SWITCH(CurrentState) {
        CASE INITIALIZING:
            // Check basic hardware connections and initialize peripherals.
            setPinsAsOutput(); 
            CurrentState = READING_TEMP;
            break;

        CASE READING_TEMP:
            temperature = readSensorData(); // Calls sensor library function
            IF (IsReadingSuccessful(temperature)) {
                CurrentState = CHECKING_THRESHOLD;
            } ELSE {
                // Log error and wait.
                delay(100); 
            }
            break;

        CASE CHECKING_THRESHOLD:
            IF (temperature > MAX_SAFE_TEMP) {
                CurrentState = ACTUATING_HEAT;
            } ELSE {
                CurrentState = WAITING_FOR_COOLDOWN;
            }
            break;
        // ... other states ...
    }
}
```

### 3. Sample Minimal Working Sketch (`.ino` format)
```cpp
// Includes necessary headers based on Manifest (e.g., #include <Wire.h>)

const int BUTTON_PIN = PA0; // Defined in the manifest!
volatile bool buttonPressedFlag = false;

void setup() {
    Serial.begin(9600);
    pinMode(BUTTON_PIN, INPUT_PULLUP); // Uses hardware pull-up as per best practice
    // Attach interrupt handler for robust detection (preferred over delay())
    attachInterrupt(digitalPinToInterrupt(BUTTON_PIN), handleButtonInterrupt, FALLING);
}

void loop() {
    if (buttonPressedFlag) {
        Serial.println("Button detected and processed.");
        buttonPressedFlag = false;
    }
    // Main logic runs here, non-blocking...
}

// Interrupt Service Routine (ISR) - Must be fast!
void handleButtonInterrupt() {
    // Minimal code execution is critical here.
    buttonPressedFlag = true;
}
```