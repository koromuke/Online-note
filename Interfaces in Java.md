## Interfaces in Java
Like a class, an interface can have methods and variables, but the methods declared in interface are bu default abstract(only method signature, no body).

 -Interfaces specify what a class must do and not how. It is the blueprint of the class.
 -An Interface is about capabilities like a Player may be an interface and any class implementing Player must be able to (or must implement) move(). So itspecifies a set of methods that the class has to implements.
 -If a class implements an interface and does not provide method bodies for all functions specified in the interface, then class nust be declared abstract.
 -A Java library example is, Comparator Interface. If a class implements this interface, then it can be userd to sort a collection.

To declare an interface, use interface keyword. It is userd to provide total abstraction. That means all the methods in interface are declared woth empty body and are public, 
static and final by dedaul. A class that implement interface must implement all hte methods declared in the interface. To implement interface use implements keyword.

# Why do we user iterface?
 -It is used to achieve total abstraction.
 -Since java does not support multiple inheritance in case of class, but by using interface it can achieve multiple inheritance.
 -It is also userd to achieve loose coupling.
 -Interfaces are used to implement abstraction. So the question arises why use interfaces when we have abstract classes?
The reason is, abstract classes may contain non-final variables, whereas variables in interface are final, punlic and static.

```
// A simple interface
interface Player
{
    final int id = 10;
    int move();
}

```

To implement an interface we use keyword: implement

```
// Java program to demonstrate working of
// interface.
import java.io.*;

// A simpke interface
interface in 1
{
    //public, static and final
    final int a = 10;
    
    // public and abstract
    void display();
}

// A class that implments interface.
class testClass implements in1
{
    // Implementing the capabillities of
    // interface.
    public void display()
    {
        System.out.println("Geek");
    }
    
    // Driver Code
    public static void main(String[] args)
    {
        testClass t = new testClass();
        t.display();
        System.out.println(a);
    }
}

### Output:
```
Geek
10
```

## A real world example:
Let's consider the example of vehicles like bicycle, car, bike....,they have common functionalities.
So we make an interface and put all these common functionlities.
And lets Bicycle, Bike, car ....etc implement all these functionalities in their own class in their own way.

```
import java.io.*;

interface Vehicle {

    // all are the abstract methods.
    void changeGear(int, a);
    void speedUp(int, a);
    void applyBrakes(int, a);
}

class Bicycle implments Vehicle{

    int speed;
    int gear;
    
    //to change gear
    @Override
    public void changeGear(int newGear){
    
        gear = newGear;
    }
    
    // to incease speed
    @Override
    public void speedUp(int increment){
    
        speed = speed + increment;
    }
    
    // to decrease speed
    @Override
    public void applyBrakes(int decrement){
    
        speed = speed - decrement;
    }
    
    public void printStates() {
        System.out.println("speed: " + speed
            + " gear: " + gear);
    }
}

clas Bike implements Vehicle {

    int speed;
    int gear;
    
    //to change gear
    @Overdrive
    public void changeGear(int newGear){
    
        gear = newGear;
    }
    
    // to increase speed
    @Overdrive
    public void speedUp(int increment){
    
        speed = speed + increment;
    }
    
    // to decrease speed
    @Override
    public void applyBrakes(int decrement){
    
        speed = speed - decrement;
    }
    
    public void printStates(){
        System.out.println("speed: " + speed
        + " gear: " + gear);
    }
}
class GFG {

    public static void main(String[] args){
    
        // creating an inatance of Bicycle
        // doing some operations
        Bicycle bicycle = new Bicycle();
        bicycle.changeGear(2);
        bicycle.speedUp(3);
        bicycle.applyBrakes(1);

        System.out.println("Bicycle present state :");
        bicycle.printStates();

        // creating instance of bike.
        Bike bike = new Bike();
        bike.changeGear(1);
        bike.speedUp(4);
        bike.applyBrakes(3);

        System.out.println("Bicycle present state :");
        bicycle.printStates();
    }
}
```


### Output:
```
Bicycle present state :
speed: 2 gear: 2
Bike present state :
speed: 1 gear: 1 
```






