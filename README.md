# Water-Leakage-Detection-System
This project is an automated safety system designed to identify unintended water presence in homes or industrial environments
// Define Pins
const int sensorPin = 2; // Digital Output from Rain Sensor
const int ledPin = 3;    // LED Pin
const int buzzerPin = 4; // Buzzer Pin

void setup() {
  pinMode(sensorPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
  
  Serial.begin(9600); // For debugging via Serial Monitor
  Serial.println("System Initialized. Monitoring for leaks...");
}

void loop() {
  // Read sensor state: LOW usually means water is detected
  int sensorState = digitalRead(sensorPin);

  if (sensorState == LOW) {
    // Alert: Water Leak Detected!
    digitalWrite(ledPin, HIGH);
    digitalWrite(buzzerPin, HIGH);
    Serial.println("ALERT: Water Leakage Detected!");
  } else {
    // No leak detected
    digitalWrite(ledPin, LOW);
    digitalWrite(buzzerPin, LOW);
  }
  
  delay(200); // Brief delay for stability
}
