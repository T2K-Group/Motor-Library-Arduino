# Motor Library for Arduino with Encoder Support

The `Motor` class represents a motor in a project. It has a number of private member variables for storing the pin numbers of the motor driver and encoder, as well as a public variable `encoderCount` for storing the encoder count of the motor.

## Usage

```cpp

#include "motor.h"

Motor mymotor(1,2,3,4,5);

void setup(){
    //Forward is the default direction. 
    //it can be changed with setDirection(0)

    mymotor.changeSpeed(50); // ramp up to 50%

    delay(1000);

    mymotor.stop(); // stops the motor instantly

    delay(1000);

    mymotor.setSpeed(100); //sets speed to 100% instantly
}

void loop () {

}

```

---

## Constructor

The constructor for the `Motor` class takes 5 arguments:

- `pwm`: an integer representing the pin number of the PWM pin on the motor driver
- `inputA`: an integer representing the pin number of the input A pin on the motor driver
- `inputB`: an integer representing the pin number of the input B pin on the motor driver
- `encoderA`: an integer representing the pin number of the encoder A pin on the motor
- `encoderB`: an integer representing the pin number of the encoder B pin on the motor

The constructor initializes the member variables and sets the pin mode of the pins on the motor driver and encoder. It also sets the direction of the motor to forward.

Here is an example of how to create an instance of the `Motor` class:

```cpp
Motor myMotor(9, 8, 7, 6, 5);
```

---
## setSpeed

The `setSpeed` method is used to set the speed of the motor as a percentage of the max speed. It takes a single argument:

- `speedPercentage`: an integer representing the speed of the motor as a percentage of the max speed (0 = stop, 100 = full speed)

The method sets the PWM value of the motor driver to control the speed of the motor. It maps the `speedPercentage` to a value between 0 and 255 and then writes the value to the PWM pin on the motor driver.

Here is an example of how to use the `setSpeed` method:

```cpp
myMotor.setSpeed(50); // Set the speed of the motor to 50%
```

---
## setDirection

The `setDirection` method is used to set the direction of the motor. It takes a single argument:

- `direction`: an integer representing the direction of the motor (1 = forward, 0 = reverse)

The method sets the values of the input A and input B pins on the motor driver to control the direction of the motor.

Here is an example of how to use the `setDirection` method:
```cpp
myMotor.setDirection(1); // Set the direction of the motor to forward
```

---
## changeSpeed

The `changeSpeed` method is used to gradually change the speed of the motor from the previous speed to the new speed. It takes a single argument:

- `speedPercentage`: an integer representing the new speed of the motor as a percentage of the max speed (0 = stop, 100 = full speed)

The method gradually increases or decreases the speed of the motor by incrementing or decrementing the `speedPercentage` in small steps. This is done to avoid sudden changes in speed which can cause the motor to stall.

Here is an example of how to use the `changeSpeed` method:
```cpp
myMotor.changeSpeed(75); // Gradually change the speed of the motor to 75%
```

---
## stop

The `stop` method is used to stop the motor. It takes no arguments and does not return any values.

The method sets the speed of the motor to 0 using the `setSpeed` method.

Here is an example of how to use the `stop` method:
```cpp
myMotor.stop(); // Stop the motor
```
---


## resetEncoder

The `resetEncoder` method is used to reset the encoder count of the motor to 0. It takes no arguments and does not return any values.

The method sets the value of the `encoderCount` member variable to 0.

Here is an example of how to use the `resetEncoder` method:
```cpp
myMotor.resetEncoder(); // Reset the encoder count of the motor to 0
```

---

> The MIT License
>
>Copyright © 2022 Jack Fitton on behalf of T2K Group
>
> ![T2K Group Logo](https://media-exp1.licdn.com/dms/image/D4D0BAQHtBjWkaSaxFw/company-logo_200_200/0/1666895994081?e=1678924800&v=beta&t=CyIt5xVLRVW0aj_W6lZkOeNf90z1SEfKYtl9pt9t4MQ)
> 
>
>[T2K Group](https://t2k-group.co.uk)
>
>Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
>
>The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
>
>THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

