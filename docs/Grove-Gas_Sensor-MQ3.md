---
name: Grove - Gas Sensor(MQ3)
category: Sensor
bzurl: https://seeedstudio.com/Grove-Gas-Sensor(MQ3)-p-1418.html
oldwikiname: Grove_-_Gas_Sensor(MQ3)
prodimagename: Grove_MQ3_Gas_Sensor.jpg
bzprodimageurl: https://statics3.seeedstudio.com/images/101020006 1.jpg
surveyurl: https://www.research.net/r/Grove-Gas_Sensor-MQ3
sku: 101020006
tags: grove_analog, io_5v, plat_duino
---

<div align=center><img src="https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/wiki.jpg"/></div>

The Grove - Gas Sensor(MQ3) module is useful for gas leakage detection (in home and industry). It is suitable for detecting <font color="Blue">Alcohol, Benzine, CH4, Hexane, LPG, CO.</font> Due to its high sensitivity and fast response time, measurements can be taken as soon as possible. The sensitivity of the sensor can be adjusted by using the potentiometer.

<div class="admonition danger">
<p class="admonition-title">Note</p>
The sensor value only reflects the approximated trend of gas concentration in a permissible error range, it DOES NOT represent the exact gas concentration. The detection of certain components in the air usually requires a more precise and costly instrument, which cannot be done with a single gas sensor. If your project is aimed at obtaining the gas concentration at a very precise level, then we do not recommend this gas sensor.
</div>

|Sensor|Gas Type|Get One Now|
|---|---|---|
|MQ2|Combustible Gas, Smoke|[![](https://files.seeedstudio.com/wiki/Seeed-WiKi/docs/images/300px-Get_One_Now_Banner-ragular.png)](https://www.seeedstudio.com/Grove-Gas-Sensor-MQ-p-937.html)|
|MQ3|Alcohol Vapor|[![](https://files.seeedstudio.com/wiki/Seeed-WiKi/docs/images/300px-Get_One_Now_Banner-ragular.png)](https://www.seeedstudio.com/Grove-Gas-Sensor-MQ-p-1418.html)|
|MQ5|LPG, Natural Gas, Town Gas|[![](https://files.seeedstudio.com/wiki/Seeed-WiKi/docs/images/300px-Get_One_Now_Banner-ragular.png)](https://www.seeedstudio.com/Grove-Gas-Sensor-MQ-p-938.html)|
|MQ9|Carbon Monoxide, Coal Gas, Liquefied Gas|[![](https://files.seeedstudio.com/wiki/Seeed-WiKi/docs/images/300px-Get_One_Now_Banner-ragular.png)](https://www.seeedstudio.com/Grove-Gas-Sensor-MQ-p-1419.html)|

!!!Tip
    We've released the [Seeed Gas Sensor Selection Guide](https://wiki.seeedstudio.com/Sensor_gas/), it will help you choose the gas sensor that best suits your needs.

## Features

- High sensitivity to alcohol and small sensitivity to Benzine
- Stable and long life
- Fast response and High sensitivity

!!!Tip
    More details about Grove modules please refer to [Grove System](https://wiki.seeedstudio.com/Grove_System/)

## Specification

| Item  | Parameter               | Min  | Typical    | Max | Unit |
|-------|-------------------------|------|------------|-----|------|
| VCC   | Working Voltage         | 4.9  | 5          | 5.1 | V    |
| PH    | Heating consumption     | 0.5  | -          | 750 | mW   |
| RL    | Load resistance         |      | adjustable |     |      |
| RH    | Heater resistance       | -    | 33         | -   | Ω    |
| Rs    | Sensing Resistance      | 1    | -          | 8   | MΩ   |
| Scope | Detecting Concentration | 0.05 | -          | 10  | mg/L |

## Application

- Alcohol checker.
- Breathalyser.
- Toys.

## Hardware Overview

This is an Analog output sensor. This needs to be connected to any one Analog socket in [Grove Base Shield](/Base_Shield_V2). The examples used in this tutorial makes uses of A0 analog pin. Connect this module to the A0 port of Base Shield.

It is possible to connect the Grove module to Arduino directly by using jumper wires by using the connection as shown in the table below:

| Arduino   | Gas Sensor |
|-----------|------------|
| 5V        | VCC        |
| GND       | GND        |
| NC        | NC         |
| Analog A0 | SIG        |

The output voltage from the Gas sensor increases when the concentration of gas increases. Sensitivity can be adjusted by varying the potentiometer. <font color="Red">Please note that the best preheat time for the sensor is above 24 hours</font>. For detailed information about the MQ-3 sensor, please refer to the data-sheet provided in **Resources** section.


## Platforms Supported

|Arduino|Raspberry|ArduPy|
|---|---|---|
|![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/arduino_logo.jpg)|![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/raspberry_pi_logo.jpg)|![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/ArduPy-Logo.png)|

!!!Caution
    The platforms mentioned above as supported is/are an indication of the module's software or theoritical compatibility. We only provide software library or code examples for Arduino platform in most cases. It is not possible to provide software library / demo code for all possible MCU platforms. Hence, users have to write their own software library.


## Getting Started

### Play With Arduino

| Seeeduino V4.2 | Base Shield | Grove - Gas Sensor(MQ3) |
|--------------|-------------|-----------------|
|![enter image description here](https://files.seeedstudio.com/wiki/Grove_Light_Sensor/images/gs_1.jpg)|![enter image description here](https://files.seeedstudio.com/wiki/Grove_Light_Sensor/images/gs_4.jpg)|![enter image description here](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/45d_small.jpg)|
|<a href="https://www.seeedstudio.com/Seeeduino-V4.2-p-2517.html" target="_blank">Get One Now</a>|<a href="https://www.seeedstudio.com/Base-Shield-V2-p-1378.html" target="_blank">Get One Now</a>|<a href="https://www.seeedstudio.com/Grove-Gas-Sensor-MQ-p-1418.html" target="_blank">Get One Now</a>|

![](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/Read_Gas_Sensor_data.jpg)

Connect the Grove - Gas Sensor(MQ3) to A0 port as shown in the picture above.

#### Gas Detection : Basic Example

In this example, the sensor is connected to A0 pin. The voltage read from the sensor is displayed. This value can be used as a threshold to detect any increase/decrease in gas concentration.

```cpp
void setup() {
  Serial.begin(9600);
}
 
void loop() {
  float sensor_volt;
  float sensorValue;
 
  sensorValue = analogRead(A0);
  sensor_volt = sensorValue/1024*5.0;
 
  Serial.print("sensor_volt = ");
  Serial.print(sensor_volt);
  Serial.println("V");
  delay(1000);
}
```

#### Measurement : Approximation

This examples demonstrates a way to know the approximate concentration of Gas. As per the data-sheet of the MQ3 sensors, these equations are tested for standard conditions and are not calibrated. It may vary based on change in temperature or humidity.

1. Keep the Gas Sensor in clean air environment. Upload the program below.

```cpp
void setup()
{
    Serial.begin(9600);
}

void loop()
{
    float sensor_volt;
    float RS_air; //  Get the value of RS via in a clear air
    float R0;  // Get the value of R0 via in Alcohol
    float sensorValue;

    /*--- Get a average data by testing 100 times ---*/
    for(int x = 0 ; x < 100 ; x++)
    {
        sensorValue = sensorValue + analogRead(A0);
    }
    sensorValue = sensorValue/100.0;
    /*-----------------------------------------------*/

    sensor_volt = sensorValue/1024*5.0;
    RS_air = (5.0-sensor_volt)/sensor_volt; // omit *RL
    R0 = RS_air/60.0; // The ratio of RS/R0 is 60 in a clear air from Graph (Found using WebPlotDigitizer)

    Serial.print("sensor_volt = ");
    Serial.print(sensor_volt);
    Serial.println("V");

    Serial.print("R0 = ");
    Serial.println(R0);
    delay(1000);

}
```

2. Then, open the serial monitor of Arduino IDE. Write down the value of R0 and this needs to be used in the next program. Please node down the R0 after the reading stabilizes.

<font color="Red">Replace the R0 below with value of R0 tested above </font>. Expose the sensor to any one of the gas listed above.

```cpp
void setup() {
    Serial.begin(9600);
}

void loop() {

    float sensor_volt;
    float RS_gas; // Get value of RS in a GAS
    float ratio; // Get ratio RS_GAS/RS_air
    int sensorValue = analogRead(A0);
    sensor_volt=(float)sensorValue/1024*5.0;
    RS_gas = (5.0-sensor_volt)/sensor_volt; // omit *RL

    /*-Replace the name "R0" with the value of R0 in the demo of First Test -*/
    ratio = RS_gas/R0;  // ratio = RS/R0
    /*-----------------------------------------------------------------------*/

    Serial.print("sensor_volt = ");
    Serial.println(sensor_volt);
    Serial.print("RS_ratio = ");
    Serial.println(RS_gas);
    Serial.print("Rs/R0 = ");
    Serial.println(ratio);

    Serial.print("\n\n");

    delay(1000);

}
```

Now, we can get the concentration of gas from the figure below.

![](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/GAS_Sensor_3.png)

According to the figure, we can see that the minimum concentration we can test is 0.1mg/L and the maximum is 10mg/L. However, we can't provide a formula because the relation between ratio and concentration is nonlinear.But also, we can convert mg/L to ppm, it's may convenient for us to watch the value.

### Play With Raspberry Pi (With Grove Base Hat for Raspberry Pi)

#### Hardware

- **Step 1**. Things used in this project:

| Raspberry pi | Grove Base Hat for RasPi| Grove - Gas Sensor(MQ3)|
|--------------|-------------|-----------------|
|![enter image description here](https://files.seeedstudio.com/wiki/wiki_english/docs/images/rasp.jpg)|![enter image description here](https://files.seeedstudio.com/wiki/Grove_Base_Hat_for_Raspberry_Pi/img/thumbnail.jpg)|![enter image description here](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/45d_small.jpg)|
|[Get ONE Now](https://www.seeedstudio.com/Raspberry-Pi-3-Model-B-p-2625.html)|[Get ONE Now](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi-p-3186.html)|[Get ONE Now](https://www.seeedstudio.com/Grove-Gas-Sensor-MQ-p-1418.html)|

- **Step 2**. Plug the Grove Base Hat into Raspberry.
- **Step 3**. Connect the Grove - Gas Sensor(MQ3) to port A0 of the Base Hat.
- **Step 4**. Connect the Raspberry Pi to PC through USB cable.


![](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/With_Hat.jpg)

!!! Note
    For step 3 you are able to connect the Grove - Gas Sensor(MQ3) to **any Analog Port** but make sure you change the command with the corresponding port number.


#### Software

- **Step 1**. Follow [Setting Software](https://wiki.seeedstudio.com/Grove_Base_Hat_for_Raspberry_Pi/#installation) to configure the development environment.
- **Step 2**. Download the source file by cloning the grove.py library. 

```sh
cd ~
git clone https://github.com/Seeed-Studio/grove.py

```

- **Step 3**. Excute below commands to write the code.

```sh
cd grove.py/grove
nano grove_gas_sensor_mq3.py
```
Then you should copy following code in this file and hit ++ctrl+x++ to quit and save.


```python
import math
import sys
import time
from grove.adc import ADC


class GroveGasSensorMQ3:

    def __init__(self, channel):
        self.channel = channel
        self.adc = ADC()

    @property
    def MQ3(self):
        value = self.adc.read(self.channel)
        return value

Grove = GroveGasSensorMQ3


def main():
    if len(sys.argv) < 2:
        print('Usage: {} adc_channel'.format(sys.argv[0]))
        sys.exit(1)

    sensor = GroveGasSensorMQ3(int(sys.argv[1]))

    print('Detecting...')
    while True:
        print('Gas value: {0}'.format(sensor.MQ3))
        time.sleep(.3)

if __name__ == '__main__':
    main()

```

- **Step 4**. Excute below commands to run code.

```python 
python grove_gas_sensor_mq3.py  0
```


!!!success
    If everything goes well, you will be able to see the following result

```python
pi@raspberrypi:~/grove.py/grove $ python grove_gas_sensor_mq3.py 0
Detecting...
Gas value: 564
Gas value: 564
Gas value: 564
Gas value: 565
Gas value: 565
Gas value: 565
Gas value: 566
Gas value: 566
Gas value: 566
Gas value: 566
Gas value: 566
^CTraceback (most recent call last):
  File "grove_gas_sensor_mq3.py", line 69, in <module>
    main()
  File "grove_gas_sensor_mq3.py", line 66, in main
    time.sleep(.3)
KeyboardInterrupt
```

You can quit this program by simply press ++ctrl+c++.

!!!Notice
        You may have noticed that for the analog port, the silkscreen pin number is something like **A0, A1**, however in the command we use parameter **0** and **1**, just the same as digital port. So please make sure you plug the module into the correct port, otherwise there may be pin conflicts.

### Play With Wio Terminal (ArduPy)

#### Hardware

- **Step 1.** Prepare the below stuffs:

| Wio Terminal | Grove - Gas Sensor(MQ3) |
|--------------|-----------------|
|![enter image description here](https://files.seeedstudio.com/wiki/Wio-Terminal/img/Wio-Terminal-thumbnail.png)|![enter image description here](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/45d_small.jpg)|
|[Get One Now](https://www.seeedstudio.com/Wio-Terminal-p-4509.html)|[Get One Now](https://www.seeedstudio.com/Grove-Gas-Sensor-MQ3.html)|

- **Step 2.** Connect Grove - Gas Sensor(MQ3) to **A0** port of Wio Terminal.

- **Step 3.** Connect the Wio Terminal to PC through USB Type-C cable.

![](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/WT-MQ3.png)

#### Software

- **Step 1.** Follow [**ArduPy Getting Started**](https://wiki.seeedstudio.com/ArduPy/) to configure the ArduPy development environment on Wio Terminal.

- **Step 2.** Make sure that the ArduPy firmware is flashed into Wio Terminal. For more information, please follow [**here**](https://wiki.seeedstudio.com/ArduPy/#ardupy-aip-cli-getting-started).

```sh
aip build
aip flash
```

- **Step 3.** Copy the following code and save it as `ArduPy-mq3.py`:

```python
from machine import Pin, ADC
from machine import LCD
from machine import Sprite
import time

mq3 = ADC(Pin(13))
lcd = LCD()
spr = Sprite(lcd) # Create a buff

def main():
    spr.createSprite(320, 240)
    while True:
        spr.setTextSize(2)
        spr.fillSprite(spr.color.BLACK)
        spr.setTextColor(lcd.color.BLUE)
        spr.drawString("MQ3 Reading", 90, 10)
        spr.drawFastHLine(40, 35, 240, lcd.color.DARKGREY)
        spr.setTextColor(lcd.color.WHITE)
        spr.drawString("- Current Level: ", 20, 50)
        spr.drawNumber(mq3.read(), 220,50)
        spr.pushSprite(0,0)
        time.sleep_ms(500)

        print("MQ3 Gas Sensor Reading is: ", mq3.read())

if __name__ == "__main__":
    main()
```

- **Step 4.** Save the `ArduPy-mq3.py` in a location that you know. Run the following command and **replace** `<YourPythonFilePath>` with your `ArduPy-mq3.py` location.

```sh
aip shell -n -c "runfile <YourPythonFilePath>"
# Example:
# aip shell -n -c "runfile /Users/ansonhe/Desktop/ArduPy-mq3.py"
```

- **Step 5.** We will see the gas value display on terminal as below, and displaying on the Wio Terminal LCD screen.

```python
ansonhe@Ansons-Macbook-Pro ~:aip shell -n -c "runfile /Users/ansonhe/Desktop/ArduPy-mq3.py"
Positional argument (/dev/cu.usbmodem1413101) takes precedence over --open.
Connected to ardupy
MQ3 Gas Sensor Reading is:  609
MQ3 Gas Sensor Reading is:  611
MQ3 Gas Sensor Reading is:  614
MQ3 Gas Sensor Reading is:  616
MQ3 Gas Sensor Reading is:  618
MQ3 Gas Sensor Reading is:  621
MQ3 Gas Sensor Reading is:  623
MQ3 Gas Sensor Reading is:  625
MQ3 Gas Sensor Reading is:  627
MQ3 Gas Sensor Reading is:  628
MQ3 Gas Sensor Reading is:  629
MQ3 Gas Sensor Reading is:  632
```

![](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/img/Ardupy-MQ3.png)

## Schematic Online Viewer

<div class="altium-ecad-viewer" data-project-src="https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/res/Gas_Sensor_Eagle_files.zip" style="border-radius: 0px 0px 4px 4px; height: 500px; border-style: solid; border-width: 1px; border-color: rgb(241, 241, 241); overflow: hidden; max-width: 1280px; max-height: 700px; box-sizing: border-box;" />
</div>


Resources
---------

**Suggest Reading / References**

-   [How to choose a Gas Sensor](/How_to_Chose_A_Gas_Sensor)
-   [What's LEL](https://en.wikipedia.org/wiki/Flammability_limit)

**Schematic**

-   [Grove Gas Sensor - EAGLE (Schematic and Board) files](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/res/Gas_Sensor_Eagle_files.zip)
-   [Grove Gas Sensor - PDF Schematic](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/res/Gas_Sensor_Schematic.pdf)

**Datasheet**

-   [MQ-3 Datasheet](https://files.seeedstudio.com/wiki/Grove-Gas_Sensor-MQ3/res/MQ-3.pdf)

<!-- This Markdown file was created from https://www.seeedstudio.com/wiki/Grove_-_Gas_Sensor(MQ3) -->

## Tech Support
Please submit any technical issue into our [forum](https://forum.seeedstudio.com/). <br /><p style="text-align:center"><a href="https://www.seeedstudio.com/act-4.html?utm_source=wiki&utm_medium=wikibanner&utm_campaign=newproducts" target="_blank"><img src="https://files.seeedstudio.com/wiki/Wiki_Banner/new_product.jpg" /></a></p>