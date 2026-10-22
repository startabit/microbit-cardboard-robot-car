# Program your servo car

### @explicitHints false

## Introduction @showdialog

Your car has two wheels, each on a 360° servo.
**Servo 1 is the LEFT wheel, Servo 2 is the RIGHT wheel.**

The two servos face opposite ways, so to drive forward they must turn in opposite directions:
Servo 1 **counter-clockwise**, Servo 2 **clockwise**.

![The two servos face opposite ways](https://startabit.startabit.workers.dev/projects/microbit-servo-car/images/5-opposite-ways.png)

## Step 1: A function to drive forward

Make a function called **forward**: open ``||functions:Functions||`` and click **Make a Function...**.

Put two ``||kitronik_simple_servo:set servo to turn at % speed||`` blocks inside it:
servo **1** turns **counter-clockwise** at **50** %, servo **2** turns **clockwise** at **50** %.

```blocks
function forward () {
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo1, kitronik_simple_servo.ServoDirection.CCW, 50)
    kitronik_simple_servo.servoRunPercentage(kitronik_simple_servo.ServoChoice.servo2, kitronik_simple_servo.ServoDirection.CW, 50)
}
```

## Step 2: A function to stop

Make a second function called **stop_car** with two ``||kitronik_simple_servo:stop servo||`` blocks: servo **1** and servo **2**.

```blocks
function stop_car () {
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo1)
    kitronik_simple_servo.servoStop(kitronik_simple_servo.ServoChoice.servo2)
}
```

## Step 3: Button A drives forward for 2 seconds

Take an ``||input:on button A pressed||`` block. Inside it: show an arrow with ``||basic:show arrow||``,
``||functions:call forward||``, ``||basic:pause||`` **2000** ms, ``||functions:call stop_car||``, then ``||basic:clear screen||``.

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

## Step 4: Test with the wheels in the air

Click **Download** to download the program to your Micro:bit. Switch the servo board **ON**.
Hold the car up and press **A**: both wheels should roll **forward** for 2 seconds.

- Car goes backwards? Swap the direction in **both** servo blocks.
- One wheel goes the wrong way? Swap the direction of **that** servo only.

## Step 5: Spin right with button B

Make a function **spin_right**: both servos turn **counter-clockwise** at **50** %.
The left wheel rolls forward and the right wheel rolls backward, so the car spins on the spot.
Call it from ``||input:on button B pressed||`` for **1000** ms, then ``||functions:call stop_car||``.

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
