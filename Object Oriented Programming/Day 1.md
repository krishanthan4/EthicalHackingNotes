# 💨 Inheritance:

To inherit a class, you simply incorporate the definition of one class into another by using the extends keyword.

**Syntax:-** 

```java
class subclass-name extends superclass-name { 

// body of class

}
```

- You can only specify one superclass for any subclass that you create. 
    
- Java does not support the inheritance of multiple superclasses into a single subclass
    
- You can, as stated, create a hierarchy of inheritance in which a subclass becomes a superclass of another subclass. 
    
- However, no class can be a superclass of itself.
    
- Although a subclass includes all of the members of its superclass, it cannot access those members of the superclass that have been declared as private.

**A Superclass Variable Can Reference a Subclass Object:**

It is important to understand that it is the type of the reference variable—not the type of the object that it refers to—that determines what members can be accessed.

When a reference to a subclass object is assigned to a superclass reference variable, you will have access only to those parts of the object defined by the superclass.

plainbox      =  weightbox;

(superclass)     (subclass)

SUPERCLASS ref = new SUBCLASS();    // HERE ref can only access methods which are available in SUPERCLASS

# Using super:

Whenever a subclass needs to refer to its immediate superclass, it can do so by use of the keyword super.

# Super has two general forms. 

- The first calls the superclass constructor.
    
- The second is used to access a member of the superclass that has been hidden by a member of a subclass.

```java
BoxWeight(double w, double h, double d, double m) {
    super(w, h, d); // call superclass constructor
    weight = m;
}
```

Here, BoxWeight( ) calls super( ) with the arguments w, h, and d. This causes the Box constructor to be called, which initializes width, height, and depth using these values. BoxWeight no longer initializes these values itself.

It only needs to initialize the value unique to it: weight. This leaves Box free to make these values private if desired.

Thus, super( ) always refers to the superclass immediately above the calling class.

This is true even in a multileveled hierarchy.

```java
class Box {
     private double width;
     private double height;
     private double depth;

// construct clone of an object
     Box(Box ob) { // pass object to constructor
       width = ob.width;
       height = ob.height;
       depth = ob.depth;
     }
}
class BoxWeight extends Box {
     double weight; // weight of box
     // construct clone of an object
     BoxWeight(BoxWeight ob) { // pass object to constructor
        super(ob);
        weight = ob.weight;
     }
}
```

Notice that super() is passed an object of type BoxWeight—not of type Box.This still invokes the constructor Box(Box ob).

**NOTE:** A superclass variable can be used to reference any object derived from that class.

Thus, we are able to pass a BoxWeight object to the Box constructor.Of course,Box only has knowledge of its own members.

## A Second Use for super

The second form of super acts somewhat like this, except that it always refers to the superclass of the subclass in which it is used.
```java
super.member
```

Here, member can be either a method or an instance variable. This second form of super is most applicable to situations in which member names of a subclass hide members by the same name in the superclass.

- super( ) always refers to the constructor in the closest superclass. 
    
- The super( ) in BoxPrice calls the constructor in BoxWeight. The super( ) in BoxWeight calls the constructor in Box. 
    
- In a class hierarchy, if a superclass constructor requires parameters, then all subclasses must pass those parameters “up the line.”
    
-  This is true whether or not a subclass needs parameters of its own.

💨If you think about it, it makes sense that constructors complete their execution in order of derivation.

💨Because a superclass has no knowledge of any subclass, any initialization it needs to perform is separate from and possibly prerequisite to any initialization performed by the subclass. Therefore, it must complete its execution first.

**NOTE:** If super( ) is not used in subclass' constructor, then the default or parameterless constructor of each superclass

will be executed.
# Using final with Inheritance:

The keyword final has three uses:

- First, it can be used to create the equivalent of a named constant.

- Using final to Prevent Overriding:

- To disallow a method from being overridden, specify final as a modifier at the start of its declaration.
    
- Methods declared as final cannot be overridden.
    
- Methods declared as final can sometimes provide a performance enhancement: The compiler is free to inline calls to them because it “knows” they will not be overridden by a subclass. 
    
- When a small final method is called, often the Java compiler can copy the bytecode for the subroutine directly inline with the compiled code of the calling method, thus eliminating the costly overhead associated with a method call. 

- Inlining is an option only with final methods.
    
- Normally, Java resolves calls to methods dynamically, at run time. This is called late binding. However, since final methods cannot be overridden, a call to one can be resolved at compile time. This is called early binding.

# Using final to Prevent Inheritance:

- Sometimes you will want to prevent a class from being inherited. To do this, precede the class declaration with final.

**NOTE:** Declaring a class as final implicitly declares all of its methods as final, too.

As you might expect, it is illegal to declare a class as both abstract and final since an abstract class is incomplete

by itself & relies upon its subclasses to provide complete implementations.

**# NOTE:** Although static methods can be inherited ,there is no point in overriding them in child classes because the

method in parent class will run always no matter from which object you call it. That is why static interface methods

cannot be inherited because these method will run from the parent interface and no matter if we were allowed to

override them, they will always run the method in parent interface.

That is why static interface method must have a body.

**NOTE :** Polymorphism does not apply to instance variables.

# 💨 Polymorphism:

**Compile-time Polymorphism / Overloading Methods:**

In Java, it is possible to define two or more methods within the same class that share the same name, as long as their parameter declarations are different.

While overloaded methods may have different return types, the return type alone is insufficient to distinguish two versions of a method. When Java encounters a call to an overloaded method, it simply executes the version of the method whose parameters match the arguments used in the call.

In some cases, Java’s automatic type conversions can play a role in overload resolution.

```java
class OverloadDemo {
    void test(double a){
        System.out.println("Inside test(double) a: " + a);
    }
}
class Overload {

     public static void main(String args[]) {

         OverloadDemo ob = new OverloadDemo();
         int i = 88;
         ob.test(i);        // this will invoke test(double)
         ob.test(123.2);    // this will invoke test(double)
     }
}
```

As you can see, this version of OverloadDemo does not define test(int). Therefore, when test( ) is called with an integer argument inside Overload, no matching method is found. However, Java can automatically convert an integer into a double, and this conversion can be used to resolve the call. Therefore, after test(int) is not found, Java elevates i to double and then calls test(double).

Of course, if test(int) had been defined, it would have been called instead.

Java will employ its automatic type conversions only if no exact match is found.

Returning Objects:

 // Returning an object.
```java
       class Test {
           int a;
             Test(int i) {
                 a = i;
            }
            Test incrByTen() {
                Test temp = new Test(a+10);
                return temp;
            }
       }
       class RetOb {
         public static void main(String args[]) {
           Test ob1 = new Test(2);
           Test ob2;
           ob2 = ob1.incrByTen();
           System.out.println("ob1.a: " + ob1.a);
           System.out.println("ob2.a: " + ob2.a);
       }
}
```
Output:
ob1.a: 2
ob2.a: 12

As you can see, each time incrByTen( ) is invoked, a new object is created, and a reference to it is returned to the

calling routine. Since all objects are dynamically allocated using new, you don’t need to worry about an object going

out-of-scope because the method in which it was created terminates. The object will continue to exist as long as there

is a reference to it somewhere in your program. When there are no references to it, the object will be reclaimed the

next time garbage collection takes place.
# Dynamic | Run time Polymorphism:

- In a class hierarchy, when a method in a subclass has the same name and type signature as a method in its superclass, then the method in the subclass is said to override the method in the superclass. 
    
- When an overridden method is called from within its subclass, it will always refer to the version of that method defined by the subclass. The version of the method defined by the superclass will be hidden.

- Method overriding occurs only when the names and the type signatures of the two methods are identical.
    
- If they are not, then the two methods are simply overloaded.
    
- The object type defines which one to run and the reference type defines which one to acess

(Check display functions in box classes)
# Dynamic Method Dispatch:

- Dynamic method dispatch is the mechanism by which a call to an overridden method is resolved at run time, rather than compile time. 
    
- Dynamic method dispatch is important because this is how Java implements run-time polymorphism.
    
- Let’s begin by restating an important principle: a superclass reference variable can refer to a subclass object.
    
- When an overridden method is called through a superclass reference, Java determines which version of that method to execute based upon the type of the object being referred to at the time the call occurs. Thus, this determination is made at run time.
    
- In other words, it is the type of the object being referred to (not the type of the reference variable) that determines which version of an overridden method will be executed.

If B extends A then you can override a method in A through B with changing the return type of method to B.

Can we override static methods?

Ans:- Overriding depend on object

Static does not depend on object

Hence we cannot override static methods

# 💨 Encapsulation:

Definition:- wrapping up the implementation of the data members and methods in class

![](file:///tmp/lu3070acn1.tmp/lu3070acna_tmp_78c11198fd619705.png)

# 💨 Abstract:

Sometimes you will want to create a superclass that only defines a generalized form that will be shared by all of its subclasses, leaving it to each subclass to fill in the details. Such a class determines the nature of the methods that the subclasses must implement.

You may have methods that must be overridden by the subclass in order for the subclass to have any meaning.

In this case, you want some way to ensure that a subclass does, indeed, override all necessary methods.

Java’s solution to this problem is the abstract method.

You can require that certain methods be overridden by subclasses by specifying the abstract type modifier.

```java
        abstract type name(parameter-list);
```

These methods are sometimes referred to as subclass's responsibility because they have no implementation specified in the superclass.

Thus, a subclass must override them—it cannot simply use the version defined in the superclass.

Any class that contains one or more abstract methods must also be declared abstract.

# There can be no objects of an abstract class.

# You cannot declare abstract constructors, or abstract static methods.

# You can declare static methods in abstract class.

Because there can be no objects for abstract class. If they had allowed to call abstract static methods,

it would that mean we are calling an empty method (abstract) through classname because it is static.

Any subclass of an abstract class must either implement all of the abstract methods in the superclass,

or be declared abstract itself.

Abstract classes can include as much implementation as they see fit i.e.there can be concrete methods(methods with body)

in abstract class.

Although abstract classes cannot be used to instantiate objects, they can be used to create object references,

because Java’s approach to run-time polymorphism is implemented through the use of superclass references.

A public constructor on an abstract class doesn't make any sense because you can't instantiate an abstract class directly 

(can only instantiate through a derived type that itself is not marked as abstract)

Check: https://stackoverflow.com/questions/260666/can-an-abstract-class-have-a-constructor

# 💨 Interfaces:

Multiple inheritance is not available in java.

(Same functions in 2 classes it will skip that hence no multiple inheritance)

Instead we have java interfaces. they have abstract functions (no body of functions)

Interface is like class but not completely. it is like an abstract class.

By default functions are public and abstract in interface.

variables are final and static by default in interface.

Interfaces specify only what the class is doing, not how it is doing it.

The problem with MULTIPLE INHERITANCE is that two classes may define different ways of doing the same thing,

and the subclass can't choose which one to pick.

Key difference between a class and an interface: a class can maintain state information

(especially through the use of instance variables), but an interface cannot.

Using interface, you can specify a set of methods that can be implemented by one or more classes.

Although they are similar to abstract classes, interfaces have an additional capability:

A class can implement more than one interface. By contrast, a class can only inherit a single superclass

(abstract or otherwise).

Using the keyword interface, you can fully abstract a class’ interface from its implementation.

That is, using interface, you can specify what a class must do, but not how it does it.

Interfaces are syntactically similar to classes, but they lack instance variables, and, as a general rule,

their methods are declared without any body.

By providing the interface keyword, Java allows you to fully utilize the “one interface, multiple methods”

aspect of polymorphism.

NOTE: Interfaces are designed to support dynamic method resolution at run time.

Normally, in order for a method to be called from one class to another, both classes need to be present at compile time

so the Java compiler can check to ensure that the method signatures are compatible. This requirement by itself makes for

a static and nonextensible classing environment. Inevitably in a system like this, functionality gets pushed up higher

and higher in the class hierarchy so that the mechanisms will be available to more and more subclasses. Interfaces are

designed to avoid this problem. They disconnect the definition of a method or set of methods from the inheritance

hierarchy. Since interfaces are in a different hierarchy from classes, it is possible for classes that are unrelated

in terms of the class hierarchy to implement the same interface. This is where the real power of interfaces is realized.

Beginning with JDK 8, it is possible to add a default implementation to an interface method.

Thus, it is now possible for interface to specify some behavior.However, default methods constitute what is, in essence,

a special-use feature, and the original intent behind interface still remains.

Variables can be declared inside of interface declarations.

NOTE: They are implicitly final and static, meaning they cannot be changed by the implementing class.

They must also be initialized. All methods and variables are implicitly public.

NOTE: The methods that implement an interface must be declared public. Also, the type signature of the implementing method must match exactly the type signature specified in the interface definition.

It is both permissible and common for classes that implement interfaces to define additional members of their own.

NOTE:

You can declare variables as object references that use an interface rather than a class type.

This process is similar to using a superclass reference to access a subclass object.

Any instance of any class that implements the declared interface can be referred to by such a variable.

When you call a method through one of these references, the correct version will be called based on the actual instance of the interface being referred to. Called at run time by the type of object it refers to.

The method to be executed is looked up dynamically at run time, allowing classes to be created later than the code which

calls methods on them.

The calling code can dispatch through an interface without having to know anything about the “callee.”

CAUTION: Because dynamic lookup of a method at run time incurs a significant overhead when compared with the normal

method invocation in Java, you should be careful not to use interfaces casually in performance-critical code.
# Nested Interfaces:

An interface can be declared a member of a class or another interface. Such an interface

is called a member interface or a nested interface. A nested interface can be declared as public, private, or protected.

This differs from a top-level interface, which must either be declared as public or use the default access level.
```java
// This class contains a member interface.
class A {
  // this is a nested interface
  public interface NestedIF {
    boolean isNotNegative(int x);
  }
}
// B implements the nested interface.
class B implements A.NestedIF {

  public boolean isNotNegative(int x) {
    return x < 0 ? false: true;
  }
}
class NestedIFDemo {

  public static void main(String args[]) {
    // use a nested interface reference
    A.NestedIF nif = new B();

    if(nif.isNotNegative(10))
      System.out.println("10 is not negative");

    if(nif.isNotNegative(-12))
      System.out.println("this won't be displayed");
  }
}
```

Interfaces Can Be Extended:

One interface can inherit another by use of the keyword extends. The syntax is the same as for inheriting classes.

Any class that implements an interface must implement all methods required by that interface, including any that are

# inherited from other interfaces.

## Default Interface Methods (aka extension method) :

A primary motivation for the default method was to provide a means by which interfaces could be expanded without breaking existing code.

i.e. suppose you add another method without body in an interface. Then you will have to provide the body of that method

in all the classes that implement that interface.

Ex:

```java
 default String getString() {
    return "Default String";
 }
```

For example, you might have a class that implements two interfaces.

If each of these interfaces provides default methods, then some behavior is inherited from both.
# In all cases, a class implementation takes priority over an interface default implementation.

# In cases in which a class implements two interfaces that both have the same default method, but the class does not

override that method, then an error will result.
# In cases in which one interface inherits another, with both defining a common default method, the inheriting

interface’s version of the method takes precedence.

NOTE: static interface methods are not inherited by either an implementing class or a subinterface.

i.e. static interface methods should have a body! They cannot be abstract. 

NOTE : when overriding methods, the access modifier should be same or better i.e. if in Parent Class it was protected, then then overridden should be either protected or public.
# Abstract class vs Interface:

## Type of methods:

Interface can have only abstract methods.

Abstract class can have abstract and non-abstract methods. From Java 8, it can have default and static methods also.
# Final Variables:

Variables declared in a Java interface are by default final.

An abstract class may contain non-final variables.
# Type of variables:

Abstract class can have final, non-final, static and non-static variables.

Interface has only static and final variables.
# Implementation:

Abstract class can provide the implementation of interface.

Interface can’t provide the implementation of abstract class.
# Inheritance vs Abstraction:

A Java interface can be implemented using keyword “implements”

and abstract class can be extended using keyword “extends”.
# Multiple implementation:

An interface can extend another Java interface only,

an abstract class can extend another Java class and implement multiple Java interfaces.
# Accessibility of Data Members:

Members of a Java interface are public by default.

A Java abstract class can have class members like private, protected, etc.