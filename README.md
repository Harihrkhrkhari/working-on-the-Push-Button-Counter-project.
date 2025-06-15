#define BUTTON_PIN 2  // Button connected to digital pin 2

int counter = 0;
bool lastButtonState = HIGH;

void setup() {
    pinMode(BUTTON_PIN, INPUT_PULLUP); // Use internal pull-up resistor
    Serial.begin(9600);
    Serial.println("Push Button Counter Started");
}

void loop() {
    bool currentButtonState = digitalRead(BUTTON_PIN);

    // Detect falling edge: HIGH to LOW
    if (lastButtonState == HIGH && currentButtonState == LOW) {
        counter++;
        Serial.print("Button Pressed! Count: ");
        Serial.println(counter);
        delay(200); // Debounce delay
    }

    lastButtonState = currentButtonState;
}
