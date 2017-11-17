 
## INFO :bulb: ##
1. Note: The author of this blog tried his best to explain the above pattern that will fit to PHP programming... 
we may found not related to the pattern itself.
2. Facade Pattern (Structural).
    - here the ts mention the facade as a way of class to represent an entire process using with different classes.
    - they also example the product checkout for this which have a process for example:
        - Add product to cart
        - Calculate shipping charge
        - Calculate discount
        - Generate Order
    - Already did this in Formalistics in creating the custom script.
3. Adapter Pattern (Structural).
    - here the ts mention that the adapter pattern use to create another layer in the parent/api/base/concrete class because
    when the time the mention class changes its methods it will be needed to change everything in the system that uses 
    the mention classes, so here creating new layer will provide flexible solution for the method as they example for the payment:
        - instead of:
            ``paypal class -> pay method``
        - the adapter pattern represents:
            ``paypal class -> adapter paypal [implements payment interface] -> adapter paypal class -> pay method``
    - We already did this in creamsilk wordpress, thus we create an api libraries, a route class for the API instead of
    directly using the hook of wordpress.
4. Decorator Pattern (Structural).
    - here the ts mention that the decorator pattern will add a functionality or behavior to the concerete class instead of 
    modifiying it, now this is a question what is the difference of this in the sub classing, sub class you are just extending 
    the concrete class and you will be tied up on creating just a single class instead of a flexible class, 
    now the decorator is the answer for this, decorator will just be creating an abstract class and abstract method to that 
    the concrete class have and making another sub class of that abstract class to start the additional behavior, example is the:
        - email concrete
            ``-> email new year``
            ``-> email christmas``
        - you can call this both classes unlike the sub classing style.
5. Strategy Pattern (Behavioral)
    - here the ts mention that we will use this pattern if we have classes which have same functionality and may use depending on the rules
    - note that Strategy Pattern is also know as Policy Pattern because of hardcoding the condition needed to initialize specific class/objec
    example is the:
        - paypal
        - dragonpay
        - if the amount is 500+ use paypal
        - else less than 500 then use dragonpay
    - this will create another layer of class that instead of applying all the example condition in different places 
    in the application it will just wrap in the one class.
6. Simple Factory Pattern (Creational)
    - here the ts describe the simple factory pattern, just elaborating the creation of new instance class using a string concatenation
    - 3 variants of factory
        - simple factory pattern
        - factory method pattern
        - abstract factory pattern
    - example:
        - create a car class using carsfactory with input 'suv'
        - then the carsfactory will initialize the class_suv and return it
        - now the client side didn't use the 'new' keywork to init the class_suv
    - which is the purpose of the simple factory pattern.
7. Command Pattern (Behavioral)
    - here the ts emphasized the action:
        - Receiver - the actual implementation or the main manipulation logic
        - Command - interface + class that implements the interface this command are segregated via class instead of typical function.
        - Client - the main trigger what will the command to be use.
        - Invoker - this will trigger the command given by the client to be executed.
        - The main purpose of the command is to segregate the methods/functions into different classes instead of calling the direct concrete class to its method.
8. Observer Pattern (Behavioral)
    - here the ts describe the pattern as a notifier for the other object that is initiated or also an updater to the other instaces.
    - example:
        - priceSimulator <- implements the Observer interface
        - yen class <- implements the Currency interface
        - dollar class <- also implements the Currency interface
        - price simulator will use the add currency instance yen and dollar
        - price simulator will now use the update instance to update the yen and dollar object
        - To simplify the process are just updating the other objects
9. Factory Method (Creational)
    - here the ts perfectly elaborate the factory method but in the example of both website they're violating the SOLID / Open & Closed principle
        - create a factory
        - add a rules using switch or if condition
        - difining the type
        - method of the factory will get the args as string
        - This is a good way on creating different class but we need to know IoC :-)

## REFERENCES :link: ##
- For Primary Reference:
    - [ https://code.tutsplus.com/series/design-patterns-in-php--cms-747 ]
- For ``#2`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-facade-pattern--cms-22238 ]
- For ``#3`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-adapter-pattern--cms-22262 ]
- For ``#4`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-decorator-pattern--cms-22641 ]
- For ``#5`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-strategy-pattern--cms-22796 ]
- For ``#6`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-simple-factory-pattern--cms-22345 ]
- For ``#7`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-command-pattern--cms-22942 ]
- For ``#8`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-observer-pattern--cms-22975 ]
- For ``#9`` Reference:
    - [ https://code.tutsplus.com/tutorials/design-patterns-the-factory-method-pattern--cms-24530 ]
    - [ https://sourcemaking.com/design_patterns/factory_method/php/1 ]
