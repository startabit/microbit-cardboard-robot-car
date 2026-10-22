# Program your servo car

### @explicitHints false

## Introduction @showdialog

Your car has two wheels, each on a 360° servo.
**Servo 1 is the LEFT wheel, Servo 2 is the RIGHT wheel.**

The two servos face opposite ways, so to drive forward they must turn in opposite directions:
Servo 1 **counter-clockwise**, Servo 2 **clockwise**.

![The two servos face opposite ways](https://www.startabit.com/projects/microbit-servo-car/images/5-opposite-ways.png)

## Step 1: Drive forward

Make a function **forward** (``||functions:Make a Function...||``).
Inside: servo **1** **counter-clockwise** and servo **2** **clockwise**, both at **50** %.

```blocks
function forward () {
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo1, kitronik_simple_servo.ServoDirection.CCW, 50)
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo2, kitronik_simple_servo.ServoDirection.CW, 50)
}
```

## Step 2: Stop

Make a function **stop_car** with ``||kitronik_simple_servo:stop servo||`` **1** and **2**.

```blocks
function stop_car () {
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo1)
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo2)
}
```

## Step 3: Button A

In ``||input:on button A pressed||``: show an arrow, call **forward**, pause **2000** ms,
call **stop_car**, clear the screen.

```blocks
function forward () {
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo1, kitronik_simple_servo.ServoDirection.CCW, 50)
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo2, kitronik_simple_servo.ServoDirection.CW, 50)
}
function stop_car () {
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo1)
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo2)
}
input.onButtonPressed(Button.A, function () {
    basic.showArrow(ArrowNames.North)
    forward()
    basic.pause(2000)
    stop_car()
    basic.clearScreen()
})
```

## Step 4: Test in the air

**Download**, switch the servo board **ON**, hold the car up and press **A**.
Both wheels should roll **forward** for 2 seconds.

## Step 5: Wrong way?

Car goes backwards? Swap the direction in **both** servo blocks.
One wheel goes the wrong way? Swap **that** servo only.

## Step 6: Spin with button B

Make a function **spin_right**: both servos **counter-clockwise** at **50** %.
Call it from ``||input:on button B pressed||`` for **1000** ms, then **stop_car**.

```blocks
function spin_right () {
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo1, kitronik_simple_servo.ServoDirection.CCW, 50)
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo2, kitronik_simple_servo.ServoDirection.CCW, 50)
}
function stop_car () {
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo1)
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo2)
}
input.onButtonPressed(Button.B, function () {
    basic.showArrow(ArrowNames.East)
    spin_right()
    basic.pause(1000)
    stop_car()
    basic.clearScreen()
})
```

## Challenge: drive a square @showdialog

Put the car on the floor. Can you make it drive a square?
Use a ``||loops:repeat 4 times||`` loop with **forward**, a pause, **spin_right**, and a shorter pause.
Change the spin pause until each corner is a quarter turn.

```package
pxt-kitronik-simple-servo=github:kitronikltd/pxt-kitronik-simple-servo#v0.0.7
```
