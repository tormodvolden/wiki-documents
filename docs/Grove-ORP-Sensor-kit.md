---
name: Grove - ORP Sensor Kit
category: Sensor
bzurl: 
oldwikiname: 
prodimagename:
surveyurl: 
sku: 110020293
tags:
---

![](https://files.seeedstudio.com/wiki/Grove-ORD-Sensor/IMG/07(1).png)



<p style="text-align:center"><a href="https://www.seeedstudio.com/Grove-ORP-Sensor-Kit-501Z-p-4575.html" target="_blank"><img src="https://files.seeedstudio.com/wiki/Seeed-WiKi/docs/images/get_one_now.png" border=0 /></a></p> 


An Oxidation Reduction Potential (ORP) Sensor measures the activity of oxidizers and reducers in an aqueous solution, it measures the ability of a lake or river to cleanse itself or break down waste products. The Grove OPR sensor works for both 3.3V and 5V system, the Grove connector and BNC probe interface make it easy to use and very suitable for Arduino and Raspberry Pi project

!!!Note
    This product is non-RoHS certified.

## Feature

- Work efficiently under 3.3V and 5V.
- Support with both Arduino and Rasberry Pi .
- Compact size for easy deployment.

## Specification
|Items|Values|
|---|---|
|Electrode potential|	245-270mv(15-30℃)|
|RangeReference electrode internal resistance	|≤10k|
|Resolution Electrode stability	|±8mv/24|
|Indicator electrode	|Good continuity|
|Work voltage|	3.3V/5V|
|Work temperature|	5℃-70℃|

## Platform Supported
| Arduino                                                                                             | Raspberry Pi                                                                                             | BeagleBone                                                                                      | Wio                                                                                               | LinkIt ONE                                                                                         |
|-----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/arduino_logo.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/raspberry_pi_logo_n.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/bbg_logo_n.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/wio_logo_n.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/linkit_logo_n.jpg) |


## Getting Started

#### Materials Requied

| Seeeduino Lotus | Grove-ORP Sensor kit | 
|--------------|--------------|
| ![enter image description here](https://files.seeedstudio.com/wiki/Seeeduino_Lotus_Cortex-M0-/img/thumbnail.jpg)| ![enter image description here](https://files.seeedstudio.com/wiki/Grove-ORD-Sensor/IMG/thumb.png)
|[Get ONE Now](https://www.seeedstudio.com/Seeeduino-Lotus-Cortex-M0-p-2896.html)|[Get ONE Now](https://www.seeedstudio.com/Grove-ORP-Sensor-Kit-501Z-p-4575.html)|

#### Hardware Connection

![](https://files.seeedstudio.com/wiki/Grove-ORD-Sensor/IMG/ORP_Connection.jpg)

!!!Tip
    Please plug the USB cable, Grove-ORP Sensor Interface into Seeeduino Lotus board Interface gently, otherwise you may damage the port.

- **Step 1.** Plug Grove-ORP Sensor into Interface **A2** of Seeeduino Lotus board with a Grove Cable.

- **Step 2.** Connect Seeeduino Lotus to PC via a USB cable.

- **Step 3.** Connect the interface of probe cable and then download the code, please refer to the software part.

- **Step 4.** Run the code and the outcome will display on the screen of **Serial Monitor** in your Arduino IDE .


#### Software

!!!Attention
        If this is the first time you work with Arduino, we strongly recommend you to see [Getting Started with Arduino](https://wiki.seeedstudio.com/Getting_Started_with_Arduino/) before the start.




- **Step 1.** Download the [Demo code](https://files.seeedstudio.com/wiki/Grove-ORP-Sensor/ORPSensorSample.zip).

- **Step 2.** Copy the whole **ORPSensorSample** file and paste it into your Arduino IDE library file.

- **Step 3.** Open the **ORPSensorSample.ino** file with your Arduino IDE.

- **Step 4.** Upload the demo. If you do not know how to upload the code, please check [How to upload code](https://wiki.seeedstudio.com/Upload_Code/).

#### Software Code
```C++
#define VOLTAGE 5.00    //system voltage
#define OFFSET 0        //zero drift voltage
#define LED 13         //operating instructions

double orpValue;

#define ArrayLenth  40    //times of collection
#define orpPin 2         //orp meter output,connect to Arduino controller ADC pin

int orpArray[ArrayLenth];
int orpArrayIndex=0;

double avergearray(int* arr, int number){
  int i;
  int max,min;
  double avg;
  long amount=0;
  if(number<=0){
    printf("Error number for the array to avraging!/n");
    return 0;
  }
  if(number<5){   //less than 5, calculated directly statistics
    for(i=0;i<number;i++){
      amount+=arr[i];
    }
    avg = amount/number;
    return avg;
  }else{
    if(arr[0]<arr[1]){
      min = arr[0];max=arr[1];
    }
    else{
      min=arr[1];max=arr[0];
    }
    for(i=2;i<number;i++){
      if(arr[i]<min){
        amount+=min;        //arr<min
        min=arr[i];
      }else {
        if(arr[i]>max){
          amount+=max;    //arr>max
          max=arr[i];
        }else{
          amount+=arr[i]; //min<=arr<=max
        }
      }//if
    }//for
    avg = (double)amount/(number-2);
  }//if
  return avg;
}


void setup(void) {
  Serial.begin(9600);
  pinMode(LED,OUTPUT);
}

void loop(void) {
  static unsigned long orpTimer=millis();   //analog sampling interval
  static unsigned long printTime=millis();
  if(millis() >= orpTimer)
  {
    orpTimer=millis()+20;
    orpArray[orpArrayIndex++]=analogRead(orpPin);    //read an analog value every 20ms
    if (orpArrayIndex==ArrayLenth) {
      orpArrayIndex=0;
    }   
    orpValue=((30*(double)VOLTAGE*1000)-(75*avergearray(orpArray, ArrayLenth)*VOLTAGE*1000/1024))/75-OFFSET;   //convert the analog value to orp according the circuit
  }
  if(millis() >= printTime)   //Every 800 milliseconds, print a numerical, convert the state of the LED indicator
  {
	printTime=millis()+800;
	Serial.print("ORP: ");
	Serial.print((int)orpValue);
        Serial.println("mV");
        digitalWrite(LED,1-digitalRead(LED));
  }
}
```


!!!Attention
     - When measuring the electrode, the test part of the electrode (including platinum wire and reference junction) must be submerged at the same time.

     - The electrode standard solution-quinone hydroquinone saturated solution, the storage time is 48h. (Attachment: Preparation of quinone hydroquinone saturated solution: add excess quinone hydroquinone to the pH 4.00 buffer to make it saturated).

     - If the platinum wire of the electrode is stained with grease, it can be scrubbed with absorbent cotton and acetone or alcohol. And if it is dipped by insoluble inorganic substance, 30-50% hydrochloric acid works as well. Besides, it can also be cleaned by senior toilet paper once every day

     - The probe **MUST NOT** be dipped in any solution for a long time.


- **Step 5.** Take off the interface of probe cable and continuously press the **Black Button** on the sensor to reset.

![](https://files.seeedstudio.com/wiki/Grove-ORP-Sensor/IMG/Calibration_for_ORP.png)

- **Step 6.** From the chart above, we can figure out that the error is -11 mv, therefore the data of offset can be modified to -11 on **Line 2** in Demo Code.

- **Step 7.** After resetting the sensor, we can put it into a pointed calibration liquid with the specification of 204mv to figure out if it could work well. 

![](https://files.seeedstudio.com/wiki/Grove-ORP-Sensor/IMG/Calibration_Solution.png)

- **Step 8.** Finally, you are free to detect your own liquid.

## Schematic Online Viewer

<div class="altium-ecad-viewer" data-project-src="https://files.seeedstudio.com/wiki/Grove-ORP-Sensor/202002872_Grove-OPR Sensor_v1.0_SCH&PCB.zip" style="border-radius: 0px 0px 4px 4px; height: 500px; border-style: solid; border-width: 1px; border-color: rgb(241, 241, 241); overflow: hidden; max-width: 1280px; max-height: 700px; box-sizing: border-box;" />
</div>


## Resources

- **[ZIP]** [Demo Code library](https://files.seeedstudio.com/wiki/Grove-ORP-Sensor/ORPSensorSample.zip)


## Tech Support
Please submit any technical issue into our [forum](http://forum.seeedstudio.com/). <br /><p style="text-align:center"><a href="https://www.seeedstudio.com/act-4.html?utm_source=wiki&utm_medium=wikibanner&utm_campaign=newproducts" target="_blank"><img src="https://files.seeedstudio.com/wiki/Wiki_Banner/new_product.jpg" /></a></p>