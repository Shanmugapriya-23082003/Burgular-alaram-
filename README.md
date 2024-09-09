// Pin configuration
const int irSensorPin = 2; // IR Sensor input pin
const int ledPin = 13;     // LED output pin
const int buzzerPin = 12;  // Buzzer output pin
const int relayPin = 10;   // Relay output pin

void setup() {
  pinMode(irSensorPin, INPUT); // IR sensor as input
  pinMode(ledPin, OUTPUT);     // LED as output
  pinMode(buzzerPin, OUTPUT);  // Buzzer as output
  pinMode(relayPin, OUTPUT);   // Relay as output

  Serial.begin(9600); // Initialize serial communication for debugging
}

void loop() {
  int irSensorValue = digitalRead(irSensorPin); // Read IR sensor value

  if (irSensorValue == HIGH) { // If movement is detected
    digitalWrite(ledPin, HIGH);   // Turn on LED
    digitalWrite(buzzerPin, HIGH); // Turn on buzzer
    digitalWrite(relayPin, HIGH);  // Activate relay
    Serial.println("Motion Detected!");
    delay(1000); // Keep the alarm on for a second
  } else {
    digitalWrite(ledPin, LOW);    // Turn off LED
    digitalWrite(buzzerPin, LOW);  // Turn off buzzer
    digitalWrite(relayPin, LOW);   // Deactivate relay
  }

  delay(200); // Short delay before next sensor read
}
