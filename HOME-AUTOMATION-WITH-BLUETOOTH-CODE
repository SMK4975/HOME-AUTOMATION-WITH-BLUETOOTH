char data = 0;

void setup() {
  Serial.begin(9600);
  Serial.println("Bluetooth Simulation Ready");
  pinMode(2, OUTPUT);  // LED 1
  pinMode(3, OUTPUT);  // LED 2
}

void loop() {
  if (Serial.available()) {
    data = Serial.read();
    if (data == 'A')       digitalWrite(2, HIGH);
    else if (data == 'a')  digitalWrite(2, LOW);
    else if (data == 'B')  digitalWrite(3, HIGH);
    else if (data == 'b')  digitalWrite(3, LOW);
  }
}
