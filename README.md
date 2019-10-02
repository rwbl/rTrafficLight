# rTrafficLight
rTrafficLight is an open source library to explore developing a B4R library from scratch.

The purpose is to
* control three LEDs Red-Yellow-Green using an Arduino UNO microcontroller for testing.
* learn how to create library functions and to built the B4R library.

This B4R library
* is written in C++ (using the Arduino IDE 1.8.9 and the B4Rh2xml tool).

[B4R](https://www.b4x.com/b4r.html) development tool for native Arduino and ESP programs by [Anywhere Software](https://www.b4x.com).

## Files
* rTrafficLight.zip archive contains the library and sample projects.

## Install
From the zip archive, copy the content of the library folder, to the B4R additional libraries folder keeping the folder structure.

## Wiring
```
LEDs = Arduino UNO
RED = D8
YELLOW = D9
GREEN = D10
GND = GND for all LEDs
```

## B4R Example with all Functions
```
Sub Process_Globals
  Public Serial1 As Serial
  Private tl As TrafficLight
End Sub

Private Sub AppStart
  Serial1.Initialize(115200)
  Delay(100)
  Log("AppStart")

  Log("Init the Traffic Light LEDs")
  'Pin mapping for the LEDs: D8 = Red, D9 = Yellow, D10 = Green
  tl.Initialize(8,9,10)

  Log("Library Version:")
  Log(tl.Version)

  Log("Set LED Red=off,Yellow=on,Green=on")
  tl.SetState(False,True,True)

  Log("Get the state for each of the LEDs as ArrayByte:")
  Dim b() As Byte = tl.GetState
  Log("Length:", b.Length,", State Red-Yellow-Green: ",b(0),"-",b(1),"-",b(2))
  Delay(5000)

  Log("Simulate a traffic light (rather simple)")
  tl.Simulate
  Delay(5000)

  Log("Turn LED Red on and log the state (0=off, 1=on)")
  tl.Red = True
  Log("State LED Red: ", tl.Red)

  Log("Turn all LEDs on")
  tl.TurnOn
  Delay(2000)

  Log("Turn all LEDs off")
  tl.TurnOff
End Sub
```

## Credits
* Anywhere Software for providing B4R (and of course the whole B4X suite) [Info](https://www.b4x.com/)
* Friends-of-Fritzing foundation for fritzing [Info](https://fritzing.org)

## Licence
GNU General Public License v3.0.
