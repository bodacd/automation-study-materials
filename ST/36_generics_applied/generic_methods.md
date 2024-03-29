
## 3. Generic Methods

### Declaration and Usage
In programming, generic methods allow you to write functions or methods that can work with different types while providing type safety. They are particularly useful when you want to create flexible and reusable code.  
Below is an example in Java to demonstrate the declaration and usage of generic methods:
```java
public class GenericMethodsExample {

    // Declaration of a generic method
    public <T> void printArray(T[] array) {
        for (T element : array) {
            System.out.print(element + " ");
        }
        System.out.println();
    }
    // Another example of a generic method
    public <T, U> void printPair(T first, U second) {
        System.out.println("Pair: " + first + " and " + second);
    }

    public static void main(String[] args) {
        GenericMethodsExample example = new GenericMethodsExample();

        // Usage of a generic method with an Integer array
        Integer[] intArray = {1, 2, 3, 4, 5};
        example.printArray(intArray);

        // Usage of a generic method with a String array
        String[] stringArray = {"apple", "orange", "banana"};
        example.printArray(stringArray);

        // Usage of a generic method with different types
        example.printPair(10, "Hello");
        example.printPair(3.14, true);
    }
}
```
In this example:
1. The printArray method is declared with a type parameter <T>, making it a generic method. It can be used to print arrays of any type.
2. The printPair method is declared with two type parameters <T, U>, allowing it to accept two different types as arguments.
3. In the main method, instances of the GenericMethodsExample class are created, and the generic methods are called with different types of arguments.  
   By using generic methods, you can create more versatile and type-safe code that works with a variety of data types.

## Constraints on Generic Methods
In Java, you can apply constraints or bounds on generic methods to restrict the types that can be used as arguments. This is useful when you want to ensure that the generic type meets certain requirements. There are two types of bounds for generic methods: upper bounds and lower bounds.

1. Upper Bounds:
   You can specify an upper bound to restrict the generic type to be a subclass of a particular class or implement a specific interface. Here's an example:

```java
public class GenericMethodWithUpperBound {
    // Upper bound: T must be a subclass of Number
    public <T extends Number> double sumOfNumbers(T num1, T num2) {
        return num1.doubleValue() + num2.doubleValue();
    }

    public static void main(String[] args) {
        GenericMethodWithUpperBound example = new GenericMethodWithUpperBound();

        // Valid usage with Integer
        double result1 = example.sumOfNumbers(10, 20);
        System.out.println("Sum of numbers: " + result1);

        // Valid usage with Double
        double result2 = example.sumOfNumbers(3.14, 2.5);
        System.out.println("Sum of numbers: " + result2);

        // Invalid usage with String (compile-time error)
        // double result3 = example.sumOfNumbers("Hello", "World");
    }
}
```

In this example, the <T extends Number> syntax sets an upper bound on the generic type T to be a subclass of Number. Therefore, the method can only be called with arguments that are instances of classes extending the Number class.

2. Lower Bounds:
   You can also use lower bounds to specify that the generic type must be a superclass of a particular type. Here's a simple example:

```java
public class GenericMethodWithLowerBound {

    // Lower bound: T must be a superclass of Integer
    public <T super Integer> void printValue(T value) {
        System.out.println("Value: " + value);
    }

    public static void main(String[] args) {
        GenericMethodWithLowerBound example = new GenericMethodWithLowerBound();

        // Valid usage with Number (Integer is a subclass of Number)
        example.printValue(42);

        // Invalid usage with String (compile-time error)
        // example.printValue("Hello");
    }
}
```
In this example, the <T super Integer> syntax sets a lower bound on the generic type T to be a superclass of Integer. As a result, the method can only be called with arguments that are instances of classes higher up in the hierarchy than Integer.

Applying bounds in generic methods helps enforce type safety and provides more clarity about the acceptable types for a given method.


### Type Inference with Generic Methods
Type inference is the ability of a programming language to automatically deduce or infer the types of variables or expressions without explicit type annotations. In Java, type inference is particularly relevant when working with generic methods. Let's explore how type inference works with generic methods in Java:

Consider the following generic method:

```java
public class TypeInferenceExample {

    // Generic method that takes an array and prints its elements
    public <T> void printArray(T[] array) {
        for (T element : array) {
            System.out.print(element + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        TypeInferenceExample example = new TypeInferenceExample();

        // Type inference with Integer array
        Integer[] intArray = {1, 2, 3, 4, 5};
        example.printArray(intArray);

        // Type inference with String array
        String[] stringArray = {"apple", "orange", "banana"};
        example.printArray(stringArray);

        // Type inference with Double array
        Double[] doubleArray = {2.5, 3.14, 1.0};
        example.printArray(doubleArray);
    }
}
```
In this example, the printArray method is a generic method that can take an array of any type. When calling this method, you don't explicitly specify the type argument; instead, Java infers the type based on the actual arguments passed to the method.
Here's how type inference works in the main method:  
*example.printArray(intArray);*: The type *Integer* is inferred for the generic method based on the type of the intArray.  
*example.printArray(stringArray);*: The type *String* is inferred for the generic method based on the type of the stringArray.  
*example.printArray(doubleArray);*: The type *Double* is inferred for the generic method based on the type of the doubleArray.  
Java's compiler uses a process called "type inference" to determine the generic type based on the context in which the method is called. This allows for cleaner and more concise code without the need for explicit type annotations in many cases. Type inference enhances the readability and maintainability of code while preserving the benefits of generics.  

## [4.Generic Classes and Interfaces](generic_classes_and_interfaces.md)  
