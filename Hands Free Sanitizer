
/* Sketch to dispense Sanitizer/handwash from bottle without contact. 
  Utilizes some basic code and fucntions from New Ping Library of Ultrasonic sensor and Servo motor library
*/
#include <NewPing.h>
#include <Servo.h>

#define TRIGGER_PIN  12  // Arduino pin tied to trigger pin on the ultrasonic sensor.
#define ECHO_PIN     11  // Arduino pin tied to echo pin on the ultrasonic sensor.
#define MAX_DISTANCE 200 // Maximum distance we want to ping for (in centimeters). Maximum sensor distance is rated at 400-500cm.

Servo myservo; //make a servo object

NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE); // NewPing setup of pins and maximum distance.

void setup() {
  Serial.begin(115200); // Open serial monitor at 115200 baud to see ping results.
  myservo.attach(9);    //telling the computer ,which pin is attached to the servo
}

void loop() {
  delay(50);                     // Wait 50ms between pings (about 20 pings/sec). 29ms should be the shortest delay between pings.
  Serial.print("Ping: ");
  Serial.print(sonar.ping_cm()); // Send ping, get distance in cm and print result (0 = outside set distance range)
  Serial.println("cm");

  myservo.write(80);//Initial angle of dispenser
  delay(200);
  
  if((sonar.ping_cm() < 15 ) && (sonar.ping_cm()!=0)) //Checking whether any object is near the ultrasonic sensor & perfrom dispensing if it is.
  {
    myservo.write(180); //Final angle at which sanitizer is dispensed
    //Serial.println("I'm here");
    delay(2000);
    
    }

}
