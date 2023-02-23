# CP2-Tutoring-Session-1


## Passing down by refrence vs by value

- In Java, passing by reference and passing by value have different meanings.

- Passing by value means that a copy of the variable's value is passed to the method. This means that changes made to the variable within the method will not affect the original variable outside the method. For example, if you pass an integer to a method and the method changes the value of that integer, the original integer will not be changed.

- Passing by reference means that the method receives a reference to the original variable, not a copy of its value. This means that changes made to the variable within the method will also affect the original variable outside the method. In Java, however, all object variables are actually references to objects, so when you pass an object variable to a method, you are passing the reference to the object. If the method changes the object's state, the changes will be reflected in the original object.

- In Java, primitive data types such as int, float, and boolean are passed by value, while objects are passed by reference. However, since all object variables in Java are actually references, it can sometimes be confusing to understand whether you are passing an object by reference or by value.

- However, if you want to pass a primitive type by reference in Java, one way to achieve this is to wrap the primitive type in an object, such as a java.lang.Integer, java.lang.Float, java.lang.Double, etc. and pass the object reference to the method.


## Inheritence



## Encapsulation

- Hiding the charactersitc of an object but making its methods public

- We have 3 visibility modifiers:

  1. Public : accsesible outside the class
  
  2. Private : accsesible inside the class only
  
  3. Protected accsesible inside the class and in subclasses that are extending our current class


## Overloading vs Overriding

### Overloading

- Overloading refers to the ability to define multiple methods with the same name but different parameters. When you overload a method, you create a set of methods with the same name that perform different tasks based on the number or types of parameters they receive.


```java

public class MyMath {
    public int add(int a, int b) {
        return a + b;
    }

    public int add(int a, int b, int c) {
        return a + b + c;
    }

    public double add(double a, double b) {
        return a + b;
    }
}

```

- In this example, the "add" method is overloaded three times with different parameters. When you call the "add" method with different arguments, Java will automatically choose the correct version of the method based on the number and types of arguments you pass.


### Overriding

- Overriding refers to the ability to define a method in a subclass that has the same signature (name, return type, and parameters) as a method in the superclass. When you override a method, you provide a new implementation for that method in the subclass that replaces the original implementation in the superclass.

```java
public class Animal {
    public void makeSound() {
        System.out.println("The animal makes a sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("The dog barks");
    }
}

```

- In this example, the "Dog" class overrides the "makeSound" method of the "Animal" class with a new implementation that prints "The dog barks" to the console. When you create an instance of the "Dog" class and call the "makeSound" method, the new implementation in the "Dog" class will be called instead of the original implementation in the "Animal" class.

## Need of Casting



## ArrayLists

1. add(element) - This method adds an element to the end of the ArrayList.

2. add(index, element) - This method inserts an element at a specific index in the ArrayList, shifting the existing elements to the right.

3. get(index) - This method returns the element at the specified index in the ArrayList.

4. remove(index) - This method removes the element at the specified index in the ArrayList, shifting the remaining elements to the left.

5. size() - This method returns the number of elements in the ArrayList.

6. clear() - This method removes all elements from the ArrayList.

7. indexOf(element) - This method returns the index of the first occurrence of the specified element in the ArrayList, or -1 if the element is not found.

8. contains(element) - This method returns true if the ArrayList contains the specified element, otherwise it returns false.

9. set(index, element) - This method replaces the element at the specified index in the ArrayList with the specified element.


## Abstact Classes 

```java
public abstract class Animal {
    protected String name;

    public Animal(String n) {
        name = n;
    }

    public abstract void makeSound();
}

```
In this example, Animal is an abstract class that has a single abstract method makeSound(). This method doesn't have a body, so any concrete class that extends Animal must implement this method.

Animal also has a constructor that takes a name parameter, which is used to set the name instance variable.


```java
public class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }

    public void makeSound() {
        System.out.println("Woof!");
    }
}
```

This class has a constructor that calls the superclass constructor using the super keyword, and also implements the makeSound() method by printing "Woof!" to the console.

By making Animal an abstract class with an abstract method, we can define a common interface for all animals without having to implement the makeSound() method for every single animal subclass. Instead, we can simply extend Animal and implement the makeSound() method for each specific animal.
