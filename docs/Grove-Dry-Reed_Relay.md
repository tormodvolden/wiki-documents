---
name: Grove - Dry-Reed Relay
category: Actuator
bzurl: https://seeedstudio.com/Grove-Dry-Reed-Relay-p-1412.html
oldwikiname: Grove_-_Dry-Reed_Relay
prodimagename: DryReed_Relay_01.jpg
bzprodimageurl: https://statics3.seeedstudio.com/images/product/DryReed Relay.jpg
surveyurl: https://www.research.net/r/Grove-Dry-Reed_Relay
sku: 103020014
tags: grove_digital, io_3v3, io_5v, plat_duino, plat_linkit, plat_pi, plat_bbg, plat_wio
---

![](https://files.seeedstudio.com/wiki/Grove-Dry-Reed_Relay/img/DryReed_Relay_01.jpg)

The **Grove-Dry Reed Relay** is a relay module which works through magnetizing the vibration reed via the current in the coils. Compared to electromagnetic relays, the contacts completely sealed is the biggest feature of the Dry-Reed Relay. Besides, it features simplicity in construct, compactness, fast speed and long life, which make it widely applied in many fields such as microelectronic detection, Automatic Control etc.


[![](https://files.seeedstudio.com/wiki/common/Get_One_Now_Banner.png)](https://www.seeedstudio.com/Grove-Dry-Reed-Relay-p-1412.html)

Features
-------

-   Grove Interface
-   High Speed
-   Good stability
-   Long contact life
-   Contact fully sealed

!!!Tip
    More details about Grove modules please refer to [Grove System](https://wiki.seeedstudio.com/Grove_System/)
    
Specifications
-------------

<table border="1" cellspacing="0" width="80%">
<tr>
<th scope="col">
Item
</th>
<th scope="col">
Min
</th>
<th scope="col">
Typical
</th>
<th scope="col">
Max
</th>
<th scope="col">
Unit
</th>
</tr>
<tr align="center">
<th scope="row">
Voltage
</th>
<td>
4.8
</td>
<td>
5.0
</td>
<td>
5.2
</td>
<td>
VDC
</td>
</tr>
<tr align="center">
<th scope="row">
Coil Resistance
</th>
<td>
225
</td>
<td>
250
</td>
<td>
275
</td>
<td>
Ω
</td>
</tr>
<tr align="center">
<th scope="row">
Pick-Up Voltage
</th>
<td colspan="3">
3.75
</td>
<td>
VDC
</td>
</tr>
<tr align="center">
<th scope="row">
Switching Current(Max)
</th>
<td colspan="3">
0.5
</td>
<td>
A
</td>
</tr>
<tr align="center">
<th scope="row">
Switching Voltage(Max)
</th>
<td colspan="3">
120 VAC/60VDC
</td>
<td>
-
</td>
</tr>
<tr align="center">
<th scope="row">
Carrying Current(Max)
</th>
<td colspan="3">
1.0
</td>
<td>
A
</td>
</tr>
<tr align="center">
<th scope="row">
Operate Time(Max)
</th>
<td colspan="3">
1.0
</td>
<td>
mS
</td>
</tr>
<tr align="center">
<th scope="row">
Release Time(Max)
</th>
<td colspan="3">
0.5
</td>
<td>
mS
</td>
</tr>
<tr align="center">
<th scope="row">
Mechanical Life(at no load)
</th>
<td colspan="3">
1×108 operations
</td>
<td>
-
</td>
</tr>
<tr align="center">
<th scope="row">
Ambient Temperature
</th>
<td>
-30
</td>
<td>
/
</td>
<td>
70
</td>
<td>
˚C
</td>
</tr>
</table>

Platforms Supported
-------------------

| Arduino                                                                                             | Raspberry Pi                                                                                             |                                                                                                 |                                                                                                          |                                                                                                    |
|-----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/arduino_logo.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/raspberry_pi_logo.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/bbg_logo.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/wio_logo.jpg) | ![](https://files.seeedstudio.com/wiki/wiki_english/docs/images/linkit_logo.jpg) |

!!!Caution
    The platforms mentioned above as supported is/are an indication of the module's software or theoritical compatibility. We only provide software library or code examples for Arduino platform in most cases. It is not possible to provide software library / demo code for all possible MCU platforms. Hence, users have to write their own software library.


Usage
-----

### With Arduino

The Dry-Reed Relay can support up to 60VDC 1A load. You can use it to control resistance load,<font color="red"> **but it is not applicable to inductive load(such as Motor)**</font>.

The usage of this Dry-reed relay is quite alike that of common relays.

-   Connect electric light to Grove - Dry-Reed Relay and power for electric light.
-   Connect Grove - Dry-Reed Relay to port D2 of [Grove - Base Shield](/Base_Shield_V2 "Grove - Base Shield") and plug it into Arduino/Seeeduino.

-   Upload the below code.

```
    int Relay = 2;

    // the setup routine runs once when you press reset:
    void setup() {                
      // initialize the digital pin as an output.
      pinMode(Relay, OUTPUT);     
    }

    // the loop routine runs over and over again forever:
    void loop() {
      digitalWrite(Relay, HIGH);   //the Relay close(HIGH is the voltage level)
      delay(5000);               // wait for five seconds
      digitalWrite(Relay, LOW);    //the Relay normally open by making the voltage LOW
      delay(5000);               // wait for five seconds
    }
```

-   The electric light will light up for seconds ,then off for seconds, repeatedly.For the special applications, you may need to write the code by yourself.

### With Raspberry Pi

1.You should have got a raspberry pi and a grovepi or grovepi+.

2.You should have completed configuring the development enviroment, otherwise follow [here](/GrovePi_Plus).

3.Connection

-   Plug the sensor to grovepi socket D4 by using a grove cable.

4.Navigate to the demos' directory:
```
    cd yourpath/GrovePi/Software/Python/
```

-   To see the code
```
    nano grove_relay.py   # "Ctrl+x" to exit #
```
```
    import time
    import grovepi

    # Connect the Grove Relay to digital port D4
    # SIG,NC,VCC,GND
    relay = 4

    grovepi.pinMode(relay,"OUTPUT")

    while True:
        try:
            # switch on for 5 seconds
            grovepi.digitalWrite(relay,1)
            print "on"
            time.sleep(5)

            # switch off for 5 seconds
            grovepi.digitalWrite(relay,0)
            print "off"
            time.sleep(5)

        except KeyboardInterrupt:
            grovepi.digitalWrite(relay,0)
            break
        except IOError:
            print "Error"
```

5.Run the demo.
```
    sudo python grove_relay.py
```


## Schematic Online Viewer

<div class="altium-ecad-viewer" data-project-src="https://files.seeedstudio.com/wiki/Grove-Dry-Reed_Relay/res/Grove-Dry-Reed_Relay_Eagle_File.zip" style="border-radius: 0px 0px 4px 4px; height: 500px; border-style: solid; border-width: 1px; border-color: rgb(241, 241, 241); overflow: hidden; max-width: 1280px; max-height: 700px; box-sizing: border-box;" />
</div>


Resources
--------

- [Grove - Dry-Reed Relay Eagle File](https://files.seeedstudio.com/wiki/Grove-Dry-Reed_Relay/res/Grove-Dry-Reed_Relay_Eagle_File.zip)
- [Dry-Reed Relay Datasheet](https://files.seeedstudio.com/wiki/Grove-Dry-Reed_Relay/res/Dry-Reed_Relay_Datasheet.pdf)

<!-- This Markdown file was created from https://www.seeedstudio.com/wiki/Grove_-_Dry-Reed_Relay -->

## Tech Support
Please submit any technical issue into our [forum](https://forum.seeedstudio.com/). <br /><p style="text-align:center"><a href="https://www.seeedstudio.com/act-4.html?utm_source=wiki&utm_medium=wikibanner&utm_campaign=newproducts" target="_blank"><img src="https://files.seeedstudio.com/wiki/Wiki_Banner/new_product.jpg" /></a></p>