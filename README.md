# Planning motors

## Story

Your boss, Melon Usk, wants to jump into the electric car business.
Whoa, bold plan, as usual. He is really into sketches and diagrams,
and keeps sending you blurred pictures of his whiteboard with some
scribbles on it and asking you to implement them. And at the end it
always turns out that he'd thought of something completely different.
Super annoying. It's time to show him how it is done in the industry:
draw proper UML diagrams from the plans, and ask for a review _before_
the implementation.

## What are you going to learn?

- Design an application using class diagram.
- Understand `draw.io`.
- Think in the OOP way.

## Tasks

1. Melon says electric cars are a subtype of cars, the only difference is that instead of an engine they have electric motors. You translate that in the following way. - `ElectricCar` is a subclass of `Car`. - `ElectricMotor` is a subclass of `Engine`. - A `Car` has an `Engine` and an `ElectricCar` has an `ElectricMotor`. Draw this, then export and upload the result to the project as `motors-v1.png`.
    - The diagram shows four class blocks – `Car`, `ElectricCar`, `Engine`, and `ElectricMotor`.
    - The `ElectricCar` class is a subclass of `Car`. The proper arrow between classes is visible.
    - The `ElectricMotor` class is a subclass of `Engine`. The proper arrow between classes is visible.
    - The `Car` class has an `Engine`, and the latter can exist in itself. The proper arrow between classes is visible.
    - The `ElectricCar` class has a constructor with an `ElectricMotor` parameter type which stores the motor, but the `ElectricMotor`. instance can exist in itself. Proper arrow between classes is visible

2. Looking at the first version, Melon starts shouting. He says that an electric motor is not an engine because it is not driven (by heat)[https://english.stackexchange.com/questions/42027/semantic-difference-between-engine-and-motor]. Cars with engines are just regular cars, while cars with electric motors are called _electric_ cars because of the motor. "And don't forget to include the batteries, we will be focusing on batteries!" you hear the last instruction. You translate it in the following way. - `Motor` is abstract, and `Engine` and `ElectricMotor` are subclasses of it. - Every `Car` has a `Motor`. - A `Battery` class has to be added to `Car`s as every car has a battery inside. - No need to introduce a new class for `ElectricCar` since the motor type decides the type. Draw this, then export and upload the result to the project as `motors-v2.png`.
    - The diagram shows five class blocks – `Car`, `Motor`, `Engine`, `ElectricMotor`, and `Battery`.
    - The `Motor` class is abstract.
    - The `Engine` and `ElectricMotor` classes are subclasses of `Motor`. The proper arrow between classes is visible.
    - The `Car` class has a `Motor` and a `Battery`, and the latter two can exist without the `Car`. The proper arrow between classes is visible.

3. "Do not forget that electric cars in fact can be charged!" - yells Melon as you design the architecture. "Kevin, who works on SpaceY project, has already created the `Rechargeable` interface with a `charge` method, please reuse it for our electric cars". All electric cars must implement the `Rechargeable` interface. It seems we've deleted the `ElectricCar` class too soon. Happens to the best of us. Draw this, then export and upload the result to the project as `motors-v3.png`.
    - The diagram shows seven class blocks – `Car`, `ElectricCar`, `Motor`, `Engine`, `ElectricMotor`, `Battery`, and `Rechargeable`.
    - The `Motor` class is abstract
    - The `Engine` and `ElectricMotor` classes are subclasses of `Motor`. The proper arrow between classes is visible.
    - The `Car` class has a `Motor` and a `Battery`, and the latter two can exist without the `Car`. The proper arrow between classes is visible.
    - The  `ElectricCar` class has a constructor with an `ElectricMotor` parameter type which stores the motor, but the `ElectricMotor` instance can exist in itself. The proper arrow between classes is visible.
    - The `Rechargeable` interface is visible.
    - The `ElectricCar` class extends `Car` and implements `Rechargeable`.

4. Melon says that it looks cool, but `Car` is too generic. He asks you to create distinction between `ElectricCars` and `CombustionCars`. "Our customers cannot think that electric cars are in any way extension of combustion ones!". Makes sense. Create a `CombustionCar` class, derived from a `Car` class. At this point, `Car` can be marked as abstract. `CombustionCars` can only have regular `Engines`. Draw this, then export and upload the result to the project as `motors-v4.png`.
    - The diagram shows eight class blocks – `Car`, `ElectricCar`, `CombustionCar`, `Motor`, `Engine`, `ElectricMotor`, `Battery`, and `Rechargeable`.
    - The `Motor` and `Car` classes are abstract.
    - The `Engine` and `ElectricMotor` clases are subclasses of `Motor`. The proper arrows between classes are visible.
    - The `ElectricCar` and `CombustionCar` classes are subclasses of `Car`. The proper arrows between classes are visible.
    - The `Car` class has a `Motor` and a `Battery`, and the latter two can exist without the `Car`. The proper arrows between classes are visible.
    - The `CombustionCar` class has an `Engine`, and the latter can exist in itself. The proper arrow between classes is visible.
    - The `ElectricCar` class has a constructor with an `ElectricMotor` parameter type which stores the motor, but the `ElectricMotor` instance can exist in itself. The proper arrow between classes is visible.
    - The `Rechargeable` interface is visible, and class `ElectricCar` implements it.

5. "Hey, you cannot put _my_ battery in a combustion car!" – rages Melon. It seems that you have to differentiate two types of batteries: _automotive batteries_ that are included in all types of cars (even in electric ones) for providing power to standard automotive accessories. And there is the so-called "electric vehicle battery" which is the main source of energy for the traction of electric cars. Finally, it's clear what the boss wants. - `Battery` is abstract, and `AutomotiveBattery` and `ElectricVehicleBattery` are subclasses of it - Cars have an `AutomotiveBattery` in general - Electric cars have an additional `ElectricVehicleBattery` Draw this, then export and upload the result to the project as `motors-v5.png`.
    - The diagram shows ten class blocks - `Car`, `ElectricCar`, `CombustionCar`, `Motor`, `Engine`, `ElectricMotor`, `Battery`, `AutomotiveBattery`, `ElectricVehicleBattery`, and `Rechargeable`.
    - The `Motor`, `Car`, and `Battery` classes are abstract.
    - The `Engine` and `ElectricMotor` classes are subclasses of `Motor`. The proper arrows between classes are visible.
    - The `ElectricCar` and `CombustionCar` classes are subclasses of `Car`. The proper arrows between classes are visible.
    - The `Car` class has a `Motor` and a `AutomotiveBattery`, and the latter two can exist without the `Car`. The proper arrow between classes is visible.
    - The `CombustionCar` class has an `Engine`, and the latter can exist in itself. The proper arrow between classes is visible.
    - The `ElectricCar` class has a constructor with an `ElectricMotor` parameter types which stores the motor, but the `ElectricMotor` instance can exist in itself. The proper arrow between classes is visible.
    - The `ElectricCar` class has an `ElectricVehicleBattery`, and the latter can exist without the `ElectricCar`. The proper arrow between classes is visible.
    - The `Rechargeable` interface is visible, and class `ElectricCar` implements it.

## General requirements

None

## Hints

- Visit `draw.io` and create a new class diagram. Find the `UML` section on the left menu and browse the positions available there. Locate all
  building blocks needed in this project.

## Background materials

- <i class="far fa-exclamation"></i> [Class diagram basics](https://medium.com/@smagid_allThings/uml-class-diagrams-tutorial-step-by-step-520fd83b300b)
- <i class="far fa-exclamation"></i> [Class diagram explained](https://medium.com/@smagid_allThings/uml-class-diagram-example-fab6197200e6)
- <i class="far fa-exclamation"></i> [Class diagram in depth](https://www.visual-paradigm.com/guide/uml-unified-modeling-language/uml-class-diagram-tutorial/)
