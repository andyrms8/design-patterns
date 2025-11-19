## Chapter 1: Intro To Design Patterns


Premise: In a company video game, we have a duck superclass class that implements behaviors like `quack()` and `fly()` that are either inherited or overridden by child classes. With the game getting increasingly complex (introduction of more and more ducks, rubber ducks, etc.) the inheritance is not scaling - rubber ducks should not fly or quack!

Overriding the fly() and quack() methods to do nothing in rubber duck classes and and subsequent non real duck classes would also suck. In this case, inheritance leads to:
- code duplication
- make runtime behavior changes difficult, since behavior is implemented in the class and compiled at runtime
- make it hard to gain knowledge of all duck behaviors, since some classes inherit, others override -> there's no clear orgnization of unique behaviors, so we'd have to read every Duck sublass
- changes unintnetionally affecting subclasses


### Design Principals

1) **Identify the aspects of your application that vary, and separate them from what stays the same**

   The duck behaviors constantly change/differ, so we pull them out of the Duck classes)
2) **Program to an interface, not an implementation**

   We replace the duck behaviors originally implimented in the Duck superclass with behavior interfaces instead. So that each implimention of a quack or fly interface is implimented only once, instead of possible duplicated across child classes share similar overriden behaviors.
   * Note that programming to an interface really means programming to a supertype (some sort of abstract class or interface), not necessarily a Java interface, as these design patterns are language agnostic.
     <img width="721" height="348" alt="image" src="https://github.com/user-attachments/assets/e322bd4f-b630-40b7-b9dd-574411512fa6" />
3) **Favor Composition over inheritance**
   
   We can ultimately pass in different instances of behavior interface implementations.  (e.g. We can have a `Goose` subclass that extends a Duck abstract class that contains two members, a `QuackBehavior` interface and `FlyBehavior` interface. Then, we can pass instances of any classes  that impliments those interfaces into `Goose` via a constructor, and even change the behavior at runtime (through setters)!
