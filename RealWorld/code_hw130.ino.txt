// Motor A connections
int enA = 6;
int in1 = 7;
int in2 = 4;

// Motor B connections
int enB = 3;
int in3 = 5;
int in4 = 2;

// Motor C connections
int enC = 10;
int in5 = 8;
int in6 = 9;

// Motor D connections
int enD = 11;
int in7 = 12;
int in8 = 13;

void setup() {
    // Set all the motor control pins to outputs
    pinMode(enA, OUTPUT);
    pinMode(enB, OUTPUT);
    pinMode(enC, OUTPUT);
    pinMode(enD, OUTPUT);
    pinMode(in1, OUTPUT);
    pinMode(in2, OUTPUT);
    pinMode(in3, OUTPUT);
    pinMode(in4, OUTPUT);
    pinMode(in5, OUTPUT);
    pinMode(in6, OUTPUT);
    pinMode(in7, OUTPUT);
    pinMode(in8, OUTPUT);

    // Turn off motors - Initial state
    stopMotors();
}

void loop() {
    // 1. Forward for 30 seconds
    moveForward();
    delay(30000);

    // 2. Backward for 1 minute
    moveBackward();
    delay(60000);

    // 3. Alternate right and left for 1 minute
    alternateRightLeft();
}

void moveForward() {
    analogWrite(enA, 255);
    analogWrite(enB, 255);
    analogWrite(enC, 255);
    analogWrite(enD, 255);

    digitalWrite(in1, HIGH);
    digitalWrite(in2, LOW);
    digitalWrite(in3, HIGH);
    digitalWrite(in4, LOW);
    digitalWrite(in5, HIGH);
    digitalWrite(in6, LOW);
    digitalWrite(in7, HIGH);
    digitalWrite(in8, LOW);
}

void moveBackward() {
    analogWrite(enA, 255);
    analogWrite(enB, 255);
    analogWrite(enC, 255);
    analogWrite(enD, 255);

    digitalWrite(in1, LOW);
    digitalWrite(in2, HIGH);
    digitalWrite(in3, LOW);
    digitalWrite(in4, HIGH);
    digitalWrite(in5, LOW);
    digitalWrite(in6, HIGH);
    digitalWrite(in7, LOW);
    digitalWrite(in8, HIGH);
}

void turnRight() {
    analogWrite(enA, 255);
    analogWrite(enB, 255);
    analogWrite(enC, 255);
    analogWrite(enD, 255);

    digitalWrite(in1, HIGH);
    digitalWrite(in2, LOW);
    digitalWrite(in3, HIGH);
    digitalWrite(in4, LOW);
    digitalWrite(in5, LOW);
    digitalWrite(in6, HIGH);
    digitalWrite(in7, LOW);
    digitalWrite(in8, HIGH);
}

void turnLeft() {
    analogWrite(enA, 255);
    analogWrite(enB, 255);
    analogWrite(enC, 255);
    analogWrite(enD, 255);

    digitalWrite(in1, LOW);
    digitalWrite(in2, HIGH);
    digitalWrite(in3, LOW);
    digitalWrite(in4, HIGH);
    digitalWrite(in5, HIGH);
    digitalWrite(in6, LOW);
    digitalWrite(in7, HIGH);
    digitalWrite(in8, LOW);
}

void stopMotors() {
    digitalWrite(in1, LOW);
    digitalWrite(in2, LOW);
    digitalWrite(in3, LOW);
    digitalWrite(in4, LOW);
    digitalWrite(in5, LOW);
    digitalWrite(in6, LOW);
    digitalWrite(in7, LOW);
    digitalWrite(in8, LOW);
}

void alternateRightLeft() {
    unsigned long startTime = millis();
    while (millis() - startTime < 60000) { // Run for 1 minute
        turnRight();
        delay(1000); // Turn right for 1 second
        stopMotors();
        delay(500);  // Pause for 0.5 seconds
        turnLeft();
        delay(1000); // Turn left for 1 second
        stopMotors();
        delay(500);  // Pause for 0.5 seconds
    }
}