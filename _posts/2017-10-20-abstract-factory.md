---
published: false
title: Abstract Factory
layout: post
category: DesignPartterns
subtitle: A practical approach using C++
excerpt: Think of families for this pattern. In other words, if the problem that you are trying to solve involves families of objects and they all share some common properties, but the implementations are different, you may find this pattern beneficial. Also, if you want to keep a standard for all objects, but you don't want the user application to know the details for each object, only a so called "interface", you may apply it too.
---

Hi, I'm Jorge Amengol and welcome to these series of `Design Patters: A practical approach using C++`. Before you we proceed and if you didn't do it yet, please take moment to read this brief [introduction]({% link DesignPatterns.md %}) about these series of articles. That introduction is basically to let you know that this is not a rigorous technical approach and some errors or misinterpretations may and probably do exist and also that those texts are meant for me in the first place to understand the concepts, as I'm trying to learn them yet.

### Introduction

Think of families for this pattern. In other words, if the problem that you are trying to solve involves families of objects and they all share some common properties, but the implementations are different, you may find this pattern beneficial. Also, if you want to keep a standard for all objects, but you don't want the user application to know the details for each object, only a so called "interface", you may apply it too.

### Practical Example

Imagine you are working for a game company and they want to have some sort of vehicles in their new game. For that, they hired another company to make an AI ground vehicle system that will control vehicles and simulate convincing traffic. The problem is that your company will have to pay, besides the royalties for the AI, an additional value for each functionality they want to add.

So, it become obvious that, to reduce the amount of money involved is this AI for your game, you will have to commit to a somewhat generic kind of "Vehicle", because you don't want to pay to them every time you think of another type of vehicle to add to it.

That kind of a generic vehicle will have, for instance, those generic methods:

```
getPosition()
turnVehicleOn()
turnVehicleOf()
moveForward(distance)
moveBackward(distance)
turnWheel(value)
setFuel(value)
destroy() 
etc.
```

The AI system will take your vehicles and simulate a consistent city traffic. You just have to take care of creating the vehicles and handle them to the AI so it can make its magic. The problem here is that your game can't have "Generic" vehicles. It will have a Beetle, a Ferrari or a Chev, but how you will keep things generic to the AI system? Simple, use an `interface`. 

#### The interface

In C++ an `interface` in a type of Abstract class that cannot be instantiated.

So, the first step is creating our `interface` for the vehicles:

```cpp
class iVehicle
{
public:
	
	// Make the destructor virtual too
	virtual ~iVehicle()	{	};

	// Pure vitual methods
	virtual Position* getPosition(void) = 0;
	virtual void turnVehicleOn(void) = 0;
	virtual void turnVehicleOff(void) = 0;
	virtual void moveForward(float distance) = 0;
	virtual void moveBackward(float distance) = 0;
	virtual void turnWheel(float value) = 0;
	virtual void setFuel(float value) = 0;
	virtual void destroy(void) = 0;
};
```

Take a moment to see the peculiar syntax or an interface in C++. It has a `virtual destructor` and all methods are `pure virtual`, that is it has the format:

```cpp
virtual returnType methodName(returnType) = 0;
```
 
 For our interface's getPosition() method we return a type of Position, that could be a simple struct like this:

```cpp
struct Position
{
	float x, y, z;
};
```

Next, let's create two example classes that will implement this interface. A cCar and a cTruck classes.

#### The cCar class

The `cCar.h` header file:

```cpp
class cCar : public iVehicle
{
public:
	cCar(std::string model);
	virtual ~cCar();

	virtual Position getPosition(void);
	virtual void turnVehicleOn(void);
	virtual void turnVehicleOff(void);
	virtual void moveForward(float distance);
	virtual void moveBackward(float distance);
	virtual void turnWheel(float value);
	virtual void setFuel(float value);
	virtual float getFuel(void);
	virtual void destroy(void);

private:
	std::string model;
	Position mPosition;
	bool isOn;
	float wheelDirection; // Should be between -1 and 1
	float fuel; // Shoulf be between 0 and 1
	bool isDestrouyed;
};
```

The `cCar.cpp` implementation file:

```cpp
cCar::cCar(std::string model)
{
	// Set initial states
	this->model = model;
	this->mPosition.x = 0.0f;
	this->mPosition.y = 0.0f;
	this->mPosition.z = 0.0f;
	this->isOn = false;
	this->wheelDirection = 0.0f; 
	this->fuel = 1.0f; 
	this->isDestrouyed = false;

	std::cout << "cCar was created!" << std::endl;
}

cCar::~cCar()
{
	std::cout << "cCar was deleted!" << std::endl;
}

Position cCar::getPosition(void)
{
	return this->mPosition;
}

void cCar::turnVehicleOn(void)
{
	this->isOn = true;
	std::cout << this->model << " was turned ON!" << std::endl;
}

void cCar::turnVehicleOff(void)
{
	this->isOn = false;
	std::cout << this->model << " was turned OFF!" << std::endl;
}

void cCar::moveForward(float distance)
{
	this->mPosition.z += distance;

	// This is a car, so it gets to its final distance faster
	float velocity = 100.0f; // km/h
	
	// Time in hours
	float time = distance / velocity;

	
	std::cout << this->model << " moved forwards to z "
		      << this->mPosition.z
		      << " in "
		      << time * 60 
		      << " minutes!" << std::endl;

}

void cCar::moveBackward(float distance)
{
	this->mPosition.z -= distance;

	// Moving backwards should be slower, right?
	float velocity = 10.0f; // km/h

	// Time in hours
	float time = distance / velocity;


	std::cout << this->model << " moved backwards to z "
		      << this->mPosition.z
		      << " in "
		      << time * 60
		      << " minutes!" << std::endl;
}

void cCar::turnWheel(float value)
{
	if (value >= 1.0f) this->wheelDirection = 1.0f;
	else if (value <= -1.0f) this->wheelDirection = -1.0f;
	else this->wheelDirection = value;

	std::cout << this->model << " wheel's is in the "
		      << this->wheelDirection 
		      << " position." << std::endl;
}

void cCar::setFuel(float value)
{
	if (value >= 1.0f) this->fuel = 1.0f;
	else if (value <= 0.0f) this->fuel = 0.0f;
	else this->fuel = value;
}

float cCar::getFuel(void)
{
	return this->fuel;
}

void cCar::destroy(void)
{
	this->isDestrouyed = true;
	std::cout << this->model << " exploded!!" << std::endl;
}
```

The `cTruck.h` and `cTruck.cpp` are similar, with just some small differences in those methods. I will omit the code for it, but you can see the complete code in my GitHub Design Patterns example codes at the end of this article.

Now let's make a really complicated AI class to drive the vehicles (just kidding :grin:)

The `cAI.h` header:

```cpp
class cAI
{
public:

	void driveVehicle(iVehicle* vehicle);

};
```

And the `cAI.cpp` implementation:

```cpp
void cAI::driveVehicle(iVehicle* vehicle)
{
	vehicle->turnVehicleOn();
	
	// While we have fuel...
	while (vehicle->getFuel() > 0.0f)
	{
		vehicle->turnWheel(0.5f);
		vehicle->moveForward(10.0f);				
		vehicle->setFuel(vehicle->getFuel() - 0.2f);
	}

	// Lets put some gas and destroy it
	vehicle->setFuel(1.0f);
	vehicle->destroy();

}
```

Now, for the `Main.cpp` we just make some car and truck objects to be used by the AI. The important thing to notice is that the AI will not handle the objects themselves, but through the `Abstract Factory` aka `interface` iVehicle that we created:

```cpp
int main()
{
	// Create the AI
	cAI myPowerfulAI;

	// Let's create some vehicles
	cCar* myBeetle = new cCar("Beetle");
	cCar* myFerrari = new cCar("Ferrari");
	cTruck* myTruck = new cTruck("Monster Truck");

	// Let's put those vehicles in a vector of iVehicles
	std::vector<iVehicle*> myVehicles;
	myVehicles.push_back(myBeetle);
	myVehicles.push_back(myFerrari);
	myVehicles.push_back(myTruck);

	// Drive'em
	for (int i = 0; i < myVehicles.size(); i++) {
		
		myPowerfulAI.driveVehicle(myVehicles.at(i));

	}

	return 0;
}
```

When you run the whole code, you should get this output:

```
cCar was created!
cCar was created!
cTruck was created!
Beetle was turned ON!
Beetle wheel's is in the 0.5 position.
Beetle moved forwards to z 10 in 6 minutes!
Beetle wheel's is in the 0.5 position.
Beetle moved forwards to z 20 in 6 minutes!
Beetle wheel's is in the 0.5 position.
Beetle moved forwards to z 30 in 6 minutes!
Beetle wheel's is in the 0.5 position.
Beetle moved forwards to z 40 in 6 minutes!
Beetle wheel's is in the 0.5 position.
Beetle moved forwards to z 50 in 6 minutes!
Beetle wheel's is in the 0.5 position.
Beetle moved forwards to z 60 in 6 minutes!
Beetle exploded!!
Ferrari was turned ON!
Ferrari wheel's is in the 0.5 position.
Ferrari moved forwards to z 10 in 6 minutes!
Ferrari wheel's is in the 0.5 position.
Ferrari moved forwards to z 20 in 6 minutes!
Ferrari wheel's is in the 0.5 position.
Ferrari moved forwards to z 30 in 6 minutes!
Ferrari wheel's is in the 0.5 position.
Ferrari moved forwards to z 40 in 6 minutes!
Ferrari wheel's is in the 0.5 position.
Ferrari moved forwards to z 50 in 6 minutes!
Ferrari wheel's is in the 0.5 position.
Ferrari moved forwards to z 60 in 6 minutes!
Ferrari exploded!!
Monster Truck was turned ON!
Monster Truck wheel's is in the 0.5 position.
Monster Truck  moved forwards to z 10 in 10 minutes!
Monster Truck wheel's is in the 0.5 position.
Monster Truck  moved forwards to z 20 in 10 minutes!
Monster Truck wheel's is in the 0.5 position.
Monster Truck  moved forwards to z 30 in 10 minutes!
Monster Truck wheel's is in the 0.5 position.
Monster Truck  moved forwards to z 40 in 10 minutes!
Monster Truck wheel's is in the 0.5 position.
Monster Truck  moved forwards to z 50 in 10 minutes!
Monster Truck wheel's is in the 0.5 position.
Monster Truck  moved forwards to z 60 in 10 minutes!
Monster Truck was wrecked!!
```

You can see that, although the cAI class received only `iVehicle` "objects", it is able to control the concrete objects Beetle, Ferrari and Monster Truck. This means that you can add another vehicle object without having to alter the cAI class, especially because you are not touching the iVehicle interface.

### Trade-offs

The main problem with this Pattern is that changing the `interface` will result in a massive change in your project. For instance, imagine adding a new method `openDoor(int door)`. All dependent entities would have to change as well to make use of it. Those entities are not limited to just subclasses, but also other piece of code that uses it, like in our case, the cAI class itself. Keep in mind that `interfaces` should last as much as possible without any changing or there is no point in making one.

### Conclusion

As you can see, the `Abstract Factor Pattern` can be very handy when you want to control how you create families of objects, mainly if you want to limit how those objects are "interfaced" with other classes. It is very easy to implement in C++, as long as you pay special attention to how an `interface` should be created. The downside of using this pattern is the great dependence your code can create to interfaces and if they change, the chain reaction it could cause in your code is huge.

### C++ Source Files

I developed this code using Visual Studio 2017 Community. If you want to see the entire code or even run it in your machine, please go to my GitHub page about Design Patters and look for `Abstract Pattern`.

I hope this has help you in any way, and if you have questions or any suggestion to make this text or the code better, please feel free to contact me by any means at the bottom of this page.

Have fun coding,

Jorge Amengol.



