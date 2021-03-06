# cfmdarts

cfmdarts is a Python library that simulates the projectile motion of darts.

# Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Tutorials](#tutorial)
4. [How To Guides](#how-to-guides)
5. [Testing](#testing)
6. [Explanation](#explanation)
7. [License](#license)

# Introduction
This project has an extremely trivial goal. Simply input 3 values relating to the throw of a dart
- tilt angle
- swivel angle (both in degrees)
- initial velocity (in metres per second).

Then output the score of which is obtained. This project involves many areas of mathematics to solve.
Primarily Mechanics and Geometry.

# Installation

Use the package manager [pip](https://pypi.org/) to install [cfmdarts](https://pypi.org/project/cfmdarts).

```bash
pip install cfmdarts
```
NOTE: It is recommended to have a Python version which is greater that 3.6 to be installed.

# Tutorial

In order to use cfmdarts is really simple. To use in your project, you type

```python
from cfmdarts import*
```

# How To Guides

These next guides are simple pieces of code to get you started using cfmdarts.

## Creating a new Projectile object.

```python
from cfmdarts import*

#Creating a new Projectile object called Object1
#with tilt_angle=2, swivel_angle=1.5 and initial_velocity=21

Object1 = cfmdarts.Projectile(2, 1.5, 21)
```

## Outputting a new Projectile objects range, height and shift values.
```python
from cfmdarts import*

#Creating a new Projectile object called Object1
#with tilt_angle=2, swivel_angle=1.5 and initial_velocity=21

Object1 = cfmdarts.Projectile(2,1.5,21)

##This outputs the follow
print(Object1.range())
print(Object1.height())
print(Object1.shift())
```
Output:
```bash
2.370812418203357
0.02019783552359672
0.06206063411897303
```

## Creating a coordinates object to calculate and output the cartesian and polar coordinates
```python
from cfmdarts import*

#Creating a coordinates object called coord1
#with tilt_angle=2, swivel_angle=1.5 and initial_velocity=21

Coord1 = cfmdarts.Coordinates(2,1.5,21)

## These two statements below print out the
## cartesian and polar coordinates.
print(Coord1.cartesian_coordinates())
print(Coord1.polar_coordinates())
```
Output:
```bash
[0.06206063411897303, 0.02019783552359672]
[0.06526465250874554, 18.027647207949578]
```

## Creating a data simulation using the dart_simulation that returns a final score.
```python
from cfmdarts import*

#Creating a variable called 'simulation1'.
simulation1 = cfmdarts.dart_simulation(2, 1.5, 21)

##Outputs the final score from simulation1
print(simulation1)
```
Output:
```bash
13
```

## Creating a Dartboard Plot of the score using Display
```python
from cfmdarts import*

#Creating a new Coordinates object.
Coord1 = cfmdarts.Coordinates(2,1.5,22)

##These two lines below print out the respective r and theta values
##of the coordinates object.
print(Coord1.r())
print(Coord1.theta())

###This function displays a graphical image of a dartboard with the score
###Being displayed as a red cross.
cfmdarts.display_dartboard(Coord1.r(),Coord1.theta())
```
Output in the terminal and the following display:
```bash
0.06719401869315685
22.54128468531238
```
![Screenshot](Figure_1.png)


## Example of a dart simulation that has an incorrect input case with tilt_angle being an invalid input 
```python
from cfmdarts import*

#Creating a variable called 'simulation1'.
simulation1 = cfmdarts.dart_simulation(-91, 2, 29)

##Outputs the final score from simulation1
print(simulation1)
```
Output:
```bash
null shot, please ensure the tilt and swivel angles are both between -90 and 90, and that the velocity is positive
```

# Testing

To test the code:

```bash
$ python test_cfmdarts.py
```

# Explanation

## Phase I - Projectile In 3D

We must first consider the 2-dimensional plane (x,y) in which our dart
travels through. Doing, we can model the trajectory of the dart using projectile motion
in order to obtain the range, height, and shift of the dart relative to the bullseye. We can say that air resistance of the dart is negligible.

## Phase II - Geometry Of Dartboard

Determining the score is precisely the same as determining the position at which the dart landed
on the dartboard. We will obtain (via the specified throw) 2 distances relative to the distance from the
bullseye.
Using these 2 values as Cartesian coordinates, we can translate the position into polar form r, ?? via similar methods to determining the modulus and argument of a complex number. See the Coordinates class in how this was achieved.

# License
[MIT](https://choosealicense.com/licenses/mit/)