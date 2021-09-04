#include <Adafruit_NeoPixel.h>
#define PIN        6  // left side
#define NUMPIXELS 32 
#define PIN1        3  // left side 
#define NUMPIXELS1 32
#define swi  2
#define swi1  7
  int x =1; 
  int y =  1; 
int count = 0;
int count1 = 0;
int i;
Adafruit_NeoPixel pixels(NUMPIXELS, PIN, NEO_GRB + NEO_KHZ800);
Adafruit_NeoPixel pixels1(NUMPIXELS1, PIN1, NEO_GRB + NEO_KHZ800);


#define DELAYVAL 100 

void setup() 
{
  Serial.begin(9600);
  pixels.begin();
  pixels1.begin(); // left strip
  pinMode(swi,INPUT_PULLUP); // left indicator switch
  pinMode(swi1,INPUT_PULLUP); // right indicator switch
}

void loop() {

   // Set all pixel colors to 'off'
   x = digitalRead(swi); //left
  y = digitalRead(swi1); //right

         if(x == 0)
         {
          left();         
         }
         else if (y == 0)
         {
          right();
         }
         else if (x == 1 && y ==1)
         {
           red();
         }
  Serial.print("Left :"); Serial.println(x);
  Serial.print("right :"); Serial.println(y);
 pixels1.clear();
 pixels.clear(); 
}

 void left ()
 {
  while(count <=5)
      {
        for(i=0; i<=NUMPIXELS; i =i+8)
       {
        
        pixels.setPixelColor(i,   pixels.Color(225,225,0));
        pixels.setPixelColor(i+1, pixels.Color(225,225,0));
        pixels.setPixelColor(i+2, pixels.Color(225,225,0));
        pixels.setPixelColor(i+3, pixels.Color(225,225,0));
        pixels.setPixelColor(i+4, pixels.Color(225,225,0));
        pixels.setPixelColor(i+5, pixels.Color(225,225,0));
        pixels.setPixelColor(i+6, pixels.Color(225,225,0));
        pixels.setPixelColor(i+7, pixels.Color(225,225,0));  
        pixels.show();   
        delay(100);
        pixels.clear();  
        pixels1.clear();  
        }   
       count = count+1;
      }
   count = 0;
   pixels.clear();
 }
            
            
void right ()
{
   while(count1 <=5)
      {
        for(i=0; i<=NUMPIXELS ; i += 8) 
       {
         
        pixels1.setPixelColor(i, pixels1.Color(225,225,0));
        pixels1.setPixelColor(i+1, pixels.Color(225,225,0));
        pixels1.setPixelColor(i+2, pixels.Color(225,225,0));
        pixels1.setPixelColor(i+3, pixels.Color(225,225,0));
        pixels1.setPixelColor(i+4, pixels.Color(225,225,0));
        pixels1.setPixelColor(i+5, pixels.Color(225,225,0));
        pixels1.setPixelColor(i+6, pixels.Color(225,225,0));
        pixels1.setPixelColor(i+7, pixels.Color(225,225,0));  
        pixels1.show();   
        delay(100);
        pixels1.clear();   
        pixels.clear();
        }   
       count1 = count1+1;
      }
   count1 = 0;
 pixels1.clear();
  
}

void red()
{   
        for(i=0; i<=NUMPIXELS ; i += 8) 
       {
         
        pixels1.setPixelColor(i, pixels1.Color(225,0,0));
        pixels.setPixelColor(i, pixels1.Color(225,0,0));  
        
        pixels1.setPixelColor(i+1, pixels.Color(225,0,0));
        pixels.setPixelColor(i+1, pixels.Color(225,0,0));
        
        pixels1.setPixelColor(i+2, pixels.Color(225,0,0));
        pixels.setPixelColor(i+2, pixels.Color(225,0,0));
          
        pixels1.setPixelColor(i+3, pixels.Color(225,0,0));
        pixels.setPixelColor(i+3, pixels.Color(225,0,0));
        
        pixels1.setPixelColor(i+4, pixels.Color(225,0,0));
        pixels.setPixelColor(i+4, pixels.Color(225,0,0));
          
        pixels1.setPixelColor(i+5, pixels.Color(225,0,0));
        pixels.setPixelColor(i+5, pixels.Color(225,0,0));
          
        pixels1.setPixelColor(i+6, pixels.Color(225,0,0));
        pixels.setPixelColor(i+6, pixels.Color(225,0,0));
          
        pixels1.setPixelColor(i+7, pixels.Color(225,0,0));  
        pixels.setPixelColor(i+7, pixels.Color(225,0,0));   
        pixels1.show();
        pixels.show();  
          delay(100);
        pixels1.clear();   
        pixels.clear();
        x = digitalRead(swi); //left
          y = digitalRead(swi1); //right
        if(x == 0 || y == 0)
        {
          break;   
        }    
       
 pixels1.clear();
}
}         
            
