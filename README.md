// กำหนด Pin ที่จะใช้งาน

#define trig 13
#define echo 12
#define MAX_DISTANCE 150  //(in centimeters).
#define BUZZER_PIN 2



#define NOTE_B0  31
#define NOTE_C1  33
#define NOTE_CS1 35
#define NOTE_D1  37
#define NOTE_DS1 39
#define NOTE_E1  41
#define NOTE_F1  44
#define NOTE_FS1 46
#define NOTE_G1  49
#define NOTE_GS1 52
#define NOTE_A1  55
#define NOTE_AS1 58
#define NOTE_B1  62
#define NOTE_C2  65
#define NOTE_CS2 69
#define NOTE_D2  73
#define NOTE_DS2 78
#define NOTE_E2  82
#define NOTE_F2  87
#define NOTE_FS2 93
#define NOTE_G2  98
#define NOTE_GS2 104
#define NOTE_A2  110
#define NOTE_AS2 117
#define NOTE_B2  123
#define NOTE_C3  131
#define NOTE_CS3 139
#define NOTE_D3  147
#define NOTE_DS3 156
#define NOTE_E3  165
#define NOTE_F3  175
#define NOTE_FS3 185
#define NOTE_G3  196
#define NOTE_GS3 208
#define NOTE_A3  220
#define NOTE_AS3 233
#define NOTE_B3  247
#define NOTE_C4  262
#define NOTE_CS4 277
#define NOTE_D4  294
#define NOTE_DS4 311
#define NOTE_E4  330
#define NOTE_F4  349
#define NOTE_FS4 370
#define NOTE_G4  392
#define NOTE_GS4 415
#define NOTE_A4  440
#define NOTE_AS4 466
#define NOTE_B4  494
#define NOTE_C5  523
#define NOTE_CS5 554
#define NOTE_D5  587
#define NOTE_DS5 622
#define NOTE_E5  659
#define NOTE_F5  698
#define NOTE_FS5 740
#define NOTE_G5  784
#define NOTE_GS5 831
#define NOTE_A5  880
#define NOTE_AS5 932
#define NOTE_B5  988
#define NOTE_C6  1047
#define NOTE_CS6 1109
#define NOTE_D6  1175
#define NOTE_DS6 1245
#define NOTE_E6  1319
#define NOTE_F6  1397
#define NOTE_FS6 1480
#define NOTE_G6  1568
#define NOTE_GS6 1661
#define NOTE_A6  1760
#define NOTE_AS6 1865
#define NOTE_B6  1976
#define NOTE_C7  2093
#define NOTE_CS7 2217
#define NOTE_D7  2349
#define NOTE_DS7 2489
#define NOTE_E7  2637
#define NOTE_F7  2794
#define NOTE_FS7 2960
#define NOTE_G7  3136
#define NOTE_GS7 3322
#define NOTE_A7  3520
#define NOTE_AS7 3729
#define NOTE_B7  3951
#define NOTE_C8  4186
#define NOTE_CS8 4435
#define NOTE_D8  4699
#define NOTE_DS8 4978

// ประกาศตัวแปร
long duration;  // สำหรับเก็บค่าเวลาที่เสียงเดินทาง
int distance;   // สำหรับเก็บค่าระยะทางที่คำนวณได้


int melody3[] = {
  NOTE_G3, NOTE_C7, NOTE_G3, NOTE_A3, NOTE_F7, NOTE_E6, NOTE_B3, NOTE_C4
};
int melody[] = {
  NOTE_C4, NOTE_G3, NOTE_G3, NOTE_A3, NOTE_G3, 0, NOTE_B3, NOTE_C4
};
int melody2[] = {
  NOTE_E7, NOTE_E7, 0, NOTE_E7,
  0, NOTE_C7, NOTE_E7, 0,
  NOTE_G7, 0, 0,  0,
  NOTE_G6, 0, 0, 0,

  NOTE_C7, 0, 0, NOTE_G6,
  0, 0, NOTE_E6, 0,
  0, NOTE_A6, 0, NOTE_B6,
  0, NOTE_AS6, NOTE_A6, 0,

  NOTE_G6, NOTE_E7, NOTE_G7,
  NOTE_A7, 0, NOTE_F7, NOTE_G7,
  0, NOTE_E7, 0, NOTE_C7,
  NOTE_D7, NOTE_B6, 0, 0,

  NOTE_C7, 0, 0, NOTE_G6,
  0, 0, NOTE_E6, 0,
  0, NOTE_A6, 0, NOTE_B6,
  0, NOTE_AS6, NOTE_A6, 0,

  NOTE_G6, NOTE_E7, NOTE_G7,
  NOTE_A7, 0, NOTE_F7, NOTE_G7,
  0, NOTE_E7, 0, NOTE_C7,
  NOTE_D7, NOTE_B6, 0, 0
};
// note durations: 4 = quarter note, 8 = eighth note, etc.:
// int noteDurations[] = {
//   4, 8, 8, 4, 4, 4, 4, 4
// };
int noteDurations[] = {
  4, 4, 4, 4, 4, 4, 4, 4
};


//Mario main them tempo
int tempo[] = {
  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,

  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,

  9, 9, 9,
  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,

  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,

  9, 9, 9,
  12, 12, 12, 12,
  12, 12, 12, 12,
  12, 12, 12, 12,
};
int underworld_melody[] = {
  NOTE_C4, NOTE_C5, NOTE_A3, NOTE_A4,
  NOTE_AS3, NOTE_AS4, 0,
  0,
  NOTE_C4, NOTE_C5, NOTE_A3, NOTE_A4,
  NOTE_AS3, NOTE_AS4, 0,
  0,
  NOTE_F3, NOTE_F4, NOTE_D3, NOTE_D4,
  NOTE_DS3, NOTE_DS4, 0,
  0,
  NOTE_F3, NOTE_F4, NOTE_D3, NOTE_D4,
  NOTE_DS3, NOTE_DS4, 0,
  0, NOTE_DS4, NOTE_CS4, NOTE_D4,
  NOTE_CS4, NOTE_DS4,
  NOTE_DS4, NOTE_GS3,
  NOTE_G3, NOTE_CS4,
  NOTE_C4, NOTE_FS4, NOTE_F4, NOTE_E3, NOTE_AS4, NOTE_A4,
  NOTE_GS4, NOTE_DS4, NOTE_B3,
  NOTE_AS3, NOTE_A3, NOTE_GS3,
  0, 0, 0
};

void setup() {
  pinMode(trig, OUTPUT);  // กำหนดขา trig เป็น output
  pinMode(echo, INPUT);
  pinMode(BUZZER_PIN, OUTPUT);  // กำหนดขา echo เป็น input
  Serial.begin(9600);
  while (!Serial)
    ;
  Serial.flush();
  // เริ่ม Serial เพื่อใช้ Serial Monitor
}


void loop() {
  // เคลียร์ค่าขา trig ป้องกันกรณีสถานะค้างเก่าค้างอยู่
  digitalWrite(trig, LOW);


  // ให้ขา trig ส่งคลื่นออกไป 10 ไมโครวินาทีแล้วปิด (ตามสเปคการรับสัญญาณ)
  digitalWrite(trig, HIGH);
  digitalWrite(trig, LOW);

  // จับเวลาจนกว่าจะมีคลื่นเสียงมากระทบ echo โดยคำสั่ง pulseIn
  duration = pulseIn(echo, HIGH);

  // คำนวณหาระยะตามสูตรข้างต้น
  distance = (duration * 0.034) / 2;
 
  if (distance > MAX_DISTANCE) {
    Serial.println("ด้านหน้าไม่มีวัตถุในระยะ 180 ซม ");
    delay(1000);
    noTone(BUZZER_PIN);

  } else if (distance < MAX_DISTANCE) {
    if (distance < 50) {
      if (distance > 10 || distance < 50)
      Serial.println("ชนวัตถุแล้ว");  
      Serial.println(" 'Mario Theme'");

      int size = sizeof(melody3) / sizeof(int);
      for (int thisNote = 0; thisNote < size; thisNote++) {

        // to calculate the note duration, take one second
        // divided by the note type.
        //e.g. quarter note = 1000 / 4, eighth note = 1000/8, etc.
        int noteDuration = 1000 / tempo[thisNote];

        tone(BUZZER_PIN, melody3[thisNote], noteDuration);

        // to distinguish the notes, set a minimum time between them.
        // the note's duration + 30% seems to work well:
        int pauseBetweenNotes = noteDuration * 1.30;
        delay(pauseBetweenNotes);

        // stop the tone playing:
        tone(BUZZER_PIN, 0, noteDuration);

      }
    
          
          // tone(BUZZER_PIN, 494, 500);
          // delay(distance);
          // tone(BUZZER_PIN, 523, 300);
          // delay(distance);
          // for (i=d; i< 100 ; i++){
          //   digitalWrite(BUZZER_PIN, HIGH);
          //   delay(i);
          //   digitalWrite(BUZZER_PIN, LOW);
          //   delay(i);
          // }noTone(8);
 
        
    } else {
        
        Serial.println("ด้านหน้ามีวัตถุอยู่ใกล้มาก");
        delay(1000);
    }
  }

  // if((distance > 1)||(distance < 100)){
  //   Serial.print("จะชนแล้ว ");

  //   for (j=1; j<=100; j=j+1){
  //     digitalWrite(BUZZER_PIN, HIGH);
  //     delay(dt1);
  //     digitalWrite(BUZZER_PIN, LOW);
  //     delay(dt1);
  //   }
  //   for (j=1; j<=100; j=j+1){
  //     digitalWrite(BUZZER_PIN, HIGH);
  //     delay(dt2);
  //     digitalWrite(BUZZER_PIN, LOW);
  //     delay(dt2);
  //   }

  //   // tone( BUZZER_PIN, 0 );
  //   // digitalWrite(BUZZER_PIN, HIGH);
  //   // delay(100);
  //   // digitalWrite(BUZZER_PIN, LOW);
  //   // delay(d);

  //   // tone( BUZZER_PIN, 200 );
  //   // // tone( BUZZER_PIN, 355 );
  //   // digitalWrite(BUZZER_PIN,HIGH);   //ปิดเสียงเตือน
  //   // delay(1000);
  //   // digitalWrite(BUZZER_PIN,LOW);    //เปิดเสียงเตือน
  //   // delay(1000);
  //   // digitalWrite(BUZZER_PIN, LOW);
  //   // delayMicroseconds(2);
  //   // digitalWrite(BUZZER_PIN, HIGH);
  //   // delayMicroseconds(5);
  //   // digitalWrite(BUZZER_PIN, LOW);
  //   // digitalWrite(BUZZER_PIN,HIGH);   //ปิดเสียงเตือน
  //   // delay(distance*1);
  //   // tone( BUZZER_PIN, 0 );
  //   // pinMode( BUZZER_PIN, INPUT );
  //   // digitalWrite(BUZZER_PIN,LOW);
  //   // delay(distance*2);
  //   // tone( BUZZER_PIN, frequency( notes[noteNumber] ) );

  // } else if(distance  <= 150){
  //   Serial.print("ใกล้");
  //   //digitalWrite(BUZZER_PIN,HIGH);

  // } else if(distance > 150){
  //   Serial.print("มีวัตถุอยู่ด้านหน้า");
  //   // digitalWrite(BUZZER_PIN,HIGH);
  //   // tone( BUZZER_PIN, 200 );
  //   // digitalWrite(BUZZER_PIN,HIGH);   //ปิดเสียงเตือน
  //   // delay(500);
  //   // digitalWrite(BUZZER_PIN,LOW);    //เปิดเสียงเตือน
  //   // delay(500);

  // } else if (distance > 200 )
  // {
  //   Serial.print("ไม่พบวัตถุใน 300 ซม ระยะตรวจสอบ");
  //   tone( BUZZER_PIN, 0 );
  //   digitalWrite(BUZZER_PIN,HIGH);
  //   noteNumber = 0;
  // }


  // แสดงค่าทาง Serial Monitor
  Serial.print("\n Distance: ");
  Serial.println(distance);
  //  Serial.print("milli seconds : "     + String(millis()));
  //  Serial.println("\tmicro seconds : " + String(micros()));
  // หน่วงเวลา 1 วินาที
  // delay(1000);
}



int frequency(char note) {
  switch (note) {
    case 'c': return 262; break;
    case 'd': return 294; break;
    case 'e': return 330; break;
    case 'f': return 349; break;
    case 'g': return 392; break;
    case 'a': return 440; break;
    case 'b': return 494; break;
    case 'C': return 523; break;
    default: return 0; break;

  }  //switch
}


