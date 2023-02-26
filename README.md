# CP2-Tutoring

## Session-01
-----
## Passing down by reference vs by value

- In Java, passing by reference and passing by value have different meanings.

- Passing by value means that a copy of the variable's value is passed to the method. This means that changes made to the variable within the method will not affect the original variable outside the method. For example, if you pass an integer to a method and the method changes the value of that integer, the original integer will not be changed.

- Passing by reference means that the method receives a reference to the original variable, not a copy of its value. This means that changes made to the variable within the method will also affect the original variable outside the method. In Java, however, all object variables are actually references to objects, so when you pass an object variable to a method, you are passing the reference to the object. If the method changes the object's state, the changes will be reflected in the original object.

- In Java, primitive data types such as int, float, and boolean are passed by value, while objects are passed by reference. However, since all object variables in Java are actually references, it can sometimes be confusing to understand whether you are passing an object by reference or by value.


## Encapsulation

- Hiding the characteristic of an object but making its methods public

- We have 3 visibility modifiers:

  1. Public : accessible outside the class
  
  2. Private : accessible inside the class only
  
  3. Protected accessible inside the class and in subclasses that are extending our current class


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

## Casting

- Any variable declared to be of type class *A*, can point to any object of actual type *A*, or actual type *B* **iff(iff = if and only if)** *B* is a subclass of *A*, **the inverse is not true**

- :warning: at ***compile-time**, **declared type is checked*** and at ***run-time actual type is checked*** (late binding)


### Student Class
```java
public class Student {
    
  private String name;
  private int id;

  public Student(String n, int i) {
    name = n;
    id = i;
  }

  // Getters and setters

  public String getName() {
    return name;
  }

  public void setName(String n) {
    name = n;
  }

  public int getId() {
    return id;
  }

  public void setId(int i) {
    id = i;
  }
}
```
### Class GradStudent subclass of class Student
```java
public class GradStudent extends Student {

  private String researchArea;

  public GradStudent(String n, int i, String r) {
    super(n, i);
    researchArea = r;
  }

  // Getters and setters

  public String getResearchArea() {
    return researchArea;
  }

  public void setResearchArea(String r) {
    researchArea = r;
  }
}
```
###  Class Main (where we are going to run our code)
```java

public class Main {

  public static void main(String[] args) {
    // Declaring a variable of type Student
    Student student;

    // Assigning an object of type Student to the variable
    student = new Student("John Doe", 123);
    System.out.println(student.getName());  // John Doe

    // Assigning an object of type GradStudent to the same variable
    student = new GradStudent("Jane Smith", 456, "Computer Science");
    System.out.println(student.getName());  // Jane Smith

    // System.out.println(student.getResearchArea());  // This line will not compile, as getResearchArea() is not defined in class Student
  }
}
```



## ArrayLists
- :warning: ArrayLists and Vectors are **NOT** inherently dynamic. 
- When new elements are added to an ArrayList or Vector and the underlying array becomes full, the array is dynamically resized to accommodate more elements. The resizing process involves creating a new, larger array, and copying the existing elements from the old array to the new array.

- While ArrayLists and Vectors are designed to be dynamically resizable, the process of resizing can be inefficient, especially for large lists, since it involves allocating and copying memory. In contrast, linked lists are designed to be dynamically resizable without requiring additional memory allocation or copying of elements.
- Therefore, while ArrayLists and Vectors can behave as dynamic data structures in practice, they are not inherently dynamic in the same way that linked lists are, due to their underlying implementation.

- ArrayLists methods
  1. add(element) - This method adds an element to the end of the ArrayList.
  2. add(index, element) - This method inserts an element at a specific index in the ArrayList, shifting the existing elements to the right.
  3. get(index) - This method returns the element at the specified index in the ArrayList.
  4. remove(index) - This method removes the element at the specified index in the ArrayList, shifting the remaining elements to the left.
  5. size() - This method returns the number of elements in the ArrayList.
  6. clear() - This method removes all elements from the ArrayList.
  7. indexOf(element) - This method returns the index of the first occurrence of the specified element in the ArrayList, or -1 if the element is not found.
  8. contains(element) - This method returns true if the ArrayList contains the specified element, otherwise it returns false.
  9. set(index, element) - This method replaces the element at the specified index in the ArrayList with the specified element.

## Abstract Classes  

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


## Exceptions 

- Errors and exceptions are objects that indicates an erroneous situation, you cannot do anything about errors
- When an exception is thrown you can:
  1. Ignore it, **NEVER DO THIS**
  2. Handle it right where it occurs in the code
  3. Postpone it, handle it later on in the code

2. Handle it an exception immediately:

  ```java
   try{
    // Statement that might throw an exception
   }
   catch(Exception e){
    // Statement to handle the exception 
   }
  ```

3. Handling the exception later in the code

```java
public static void openfile(String s) throws IOException{
  // Statement to do
}

```

:trollface: yall better be studying and actually asking the instructors question :trollface:

this repo shall be updated and will add exercises and make it nicer