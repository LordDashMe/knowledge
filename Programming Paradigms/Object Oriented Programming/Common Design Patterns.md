
# Common Design Patterns
- Strategy
- Observer
- Factory Method
- Abstract Factory
- Singleton
- Builder
- Prototype
- Decorator
- Facade
- Adapter

## INFO :bulb: ##
1. Strategy Design Pattern
	- Seperate all the action into different classes instead of defining in the specific subclasses.
	- Ex: Flying ability of animal. 
2. Observer Design Pattern
	- Updating all the classes objects.
	- Notify.
	- Ex: Stocks changing values.
3. Factory Method Design Pattern
	- Create a different class for producing other instance of subclasses using conditional
	- Ex: Producing an enemyships with a corresponding string code.
4. Abstract Factory Design Pattern
	- Provide an interface for creating families of related or dependent objects without specifying their concrete classes.
5. Singleton Design Pattern
	- A class that only run by one instance in all the available thread.
	- Problem: multi-threaded, singleton must be still working only on 1 thread.
	- The main purpose of Singleton Design Pattern class is to run only once in the thread.
6. Builder Design Pattern
	- Key classes
		- ClassPlan [required interface]
		- ClassBuilder or Action (Will using the Class Plan) [required interface]
		- ClassEnginner
	- Ex: Robot Creation.
7. Prototype Design Pattern
	- Used: clone native function/class
	- Use a factory to encapsulate the super class creation for subclass
	- Ex. Animan -> Sheep cloning Sheep
8. Decorator Design Pattern
	- Combination of base class + abstract class
	- Usage:
		base class with interface same
		abstract class with interface same
		subclass extends the abstract class
		initialization is
		subclass -> ... -> baseclass
9. Facade Design Pattern
	- Facade class with many action/subclass and facade will be the centralized of execution.
10. Adapter Design Pattern
	- client -> interface -> two action but different function, the first action is fit and the second need another class or adapter class to be fit like first action
		that is the main idea of adapter design pattern.

## REFERENCES :link: ##
- For ``#1`` Reference:
    - [ https://www.youtube.com/watch?v=-NCgRD9-C6o&list=PLF206E906175C7E07&index=3 ]
- For ``#2`` Reference:
    - [ https://www.youtube.com/watch?v=wiQdrH2YpT4&index=4&list=PLF206E906175C7E07 ]
- For ``#3`` Reference:
    - [ https://www.youtube.com/watch?v=ub0DXaeV6hA&index=5&list=PLF206E906175C7E07 ]
- For ``#4`` Reference:
    - [ https://www.youtube.com/watch?v=xbjAsdAK4xQ&list=PLF206E906175C7E07&index=6 ]
- For ``#5`` Reference:
    - [ https://www.youtube.com/watch?v=NZaXM67fxbs&list=PLF206E906175C7E07&index=7 ]
- For ``#6`` Reference:
    - [ https://www.youtube.com/watch?v=9XnsOpjclUg&index=8&list=PLF206E906175C7E07 ]
- For ``#7`` Reference:
    - [ https://www.youtube.com/watch?v=AFbZhRL0Uz8&index=9&list=PLF206E906175C7E07 ]
- For ``#8`` Reference:
    - [ https://www.youtube.com/watch?v=j40kRwSm4VE&list=PLF206E906175C7E07&index=11 ]
- For ``#9`` Reference:
    - [ https://www.youtube.com/watch?v=B1Y8fcYrz5o&index=14&list=PLF206E906175C7E07 ]
- For ``#10`` Reference:
    - [ https://www.youtube.com/watch?v=qG286LQM6BU&index=13&list=PLF206E906175C7E07 ]
