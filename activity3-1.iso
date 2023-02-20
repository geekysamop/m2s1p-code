const byte LED_PIN = 13;
const byte METER_PIN = A4;
void startTimer();
void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(METER_PIN, INPUT);
  Serial.begin(9600);
   startTimer();
}
void loop() {
  // Nothing to do here
}
void startTimer() {
  noInterrupts();
  // Set timer1 to CTC mode with prescaler 1024
  TCCR1A = 0;
  TCCR1B = 0;
  TCNT1  = 0;
  OCR1A = 31249; // 16MHz / (1024 * 2) - 1 = 15624
  TCCR1B |= (1 << WGM12);
  TCCR1B |= (1 << CS12) | (1 << CS10); // Set prescaler to 1024
  TIMSK1 |= (1 << OCIE1A); // Enable timer compare interrupt
  interrupts();
}
ISR(TIMER1_COMPA_vect) {
  digitalWrite(LED_PIN, digitalRead(LED_PIN) ^ 1);
}
