
## 4. Generic Classes and Interfaces
### Creating Generic Classes
To create generic classes in Java, you use the generic type parameter syntax. This allows you to write a class that can work with different types while providing type safety. Here's a basic example:

```java
// Generic class with a single type parameter T
public class Box<T> {

    // Private instance variable of type T
    private T value;

    // Constructor that takes an initial value of type T
    public Box(T value) {
        this.value = value;
    }

    // Getter method to retrieve the value
    public T getValue() {
        return value;
    }

    // Setter method to set the value
    public void setValue(T value) {
        this.value = value;
    }

    public static void main(String[] args) {
        // Create a Box of Integer
        Box<Integer> integerBox = new Box<>(10);
        System.out.println("Integer Value: " + integerBox.getValue());

        // Create a Box of String
        Box<String> stringBox = new Box<>("Hello, Generics!");
        System.out.println("String Value: " + stringBox.getValue());
    }
}
```
In this example:

The class Box is declared with a single type parameter T within angle brackets (<>).
The private instance variable value is of type T.
The constructor, getter (getValue), and setter (setValue) methods all operate on values of type T.
The main method demonstrates creating instances of Box with different types (Integer and String).
When you create an instance of the Box class, you specify the actual type you want to use for T. This is done by providing the type argument within angle brackets (<>). For example, Box<Integer> means you are working with a Box that holds values of type Integer.

Generic classes provide flexibility and type safety, allowing you to create reusable and type-specific components in your code.

### Using Generic Interfaces

Using generic interfaces in Java allows you to create interfaces that can work with different types in a type-safe manner. Here's an example demonstrating how to define and use a generic interface:
 ```java
// Generic interface with a single type parameter T
public interface Pair<T> {

    // Method to set the first and second values
    void setPair(T first, T second);

    // Method to get the first value
    T getFirst();

    // Method to get the second value
    T getSecond();

    // Example of a generic method within a generic interface
    <U> U combineValues(U value1, U value2);
}
// Class implementing the generic interface
class StringPair implements Pair<String> {

    private String first;
    private String second;

    @Override
    public void setPair(String first, String second) {
        this.first = first;
        this.second = second;
    }
    @Override
    public String getFirst() {
        return first;
    }
    @Override
    public String getSecond() {
        return second;
    }
    @Override
    public <U> U combineValues(U value1, U value2) {
        // Combine two values in a way specific to the data type
        // Here, for simplicity, just concatenating strings
        return (U) (value1.toString() + value2.toString());
    }
}

public class GenericInterfaceExample {
    public static void main(String[] args) {
        // Creating an instance of the class implementing the generic interface
        StringPair pair = new StringPair();
        pair.setPair("Hello", "World");

        // Accessing values using methods from the generic interface
        System.out.println("First: " + pair.getFirst());
        System.out.println("Second: " + pair.getSecond());

        // Using the generic method from the interface
        String combined = pair.combineValues("Java", "Programming");
        System.out.println("Combined: " + combined);
    }
}
```   
In this example:
- The *Pair* interface is declared with a single type parameter *T*.
- The interface has methods for setting and getting pairs of values, as well as a generic method (*combineValues*) that takes two values of the same type and returns a combined result.
- The *StringPair* class implements the *Pair* interface with *String* as the specific type.
- In the *main* method, an instance of *StringPair* is created, and methods from the generic interface are used to set, get, and combine values.  
  Using generic interfaces provides a way to create flexible and reusable components in your code that can work with different types while ensuring type safety.

## [5.Generics in Collections](generic_collections.md)
