## Introduction
Inheritance is one of the three most important pillars of OOP (Objective Oriented Programming). Although the principle and concept of Inheritance are not hard to understand, in practice, the usage of inheritance may confuse new programmers. Therefore, this short blog aims to clarify some critical points of "Inheritence in Java". 

## Key terminology

1. **superclass and subclass**: superclass, also known as "parent class", is like a "father" to its subclass. A sub-class can "inherit"  some features, fields, and methods from the class it extends. 
1. **extends**: the keyword indicates a sub-class forming an "inherit" relationship with its superclass. It is extremely important to remember that one class can only "extends" one superclass in Java, meaning a subclass can only have one superclass.

Example: 
`public class PartTimeStaff extends Employee {
}`

3. **this and super**: this and super keywords are core concepts of inheritance. To simplify it, "super" defines a superclass's object or methods, while "this" means fields and methods inside the subclass. Both this and super keywords are mainly used in a subclass.

## Example code
Let's introduce the concept of inheritance by setting an easy-to-understand scenario. We assume that there is a chocolate company called "Sweet Joe's", which contains both full-time (receive constant monthly payment) and part-time(receive hourly fee) employees. We will create a program to store employees' information, including name, age, and pay and a calculate() method to calculate how much payment he could get. 
One way to do it is to create two independent classes of full-time and part-time classes; However, by doing this, we need to declare name and age fields separately in two classes. Both part-time and full-time employees belong to the "employee" concept in "Sweet Joe's" why not simply add an employee class as their superclass!  Here is the code:

```java
public class Employee {
    public String name;
    public int age;

    public Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
code1.0 since both full-time and part-time employees' names and ages are the same concept. So employee class should contain these two fields. Please remember that full-time and part-time staff have different payment methods, so creating a common calculate() method in full-time and part-time's common superclass is unreasonable.
```java
public class PartTimeStaff extends Employee {
    public int workHour;
    public int hourlyPay;

    public PartTimeStaff(String name, int age,int workHour,int hourlyPay) {
        super(name, age);
        this.workHour = workHour;
        this.hourlyPay = hourlyPay;
    }
    public int calculate(){
        return this.hourlyPay*this.workHour;
    }
}
```
Part-time staff can inherit fields that all staff have in common (which "super" means employee class in this case). But as part-time staff receive different payment, it should have its unique pay and calculate method ( "this").
```java
public class FullTimeStaff extends Employee{
    int salary;

    public FullTimeStaff(String name, int age,int salary) {
        super(name, age);
        this.salary = salary;
    }
    
    public int calculate(){
        return salary/12;
    }
}
```
Similar to part-time staff class, full-time class also inherit common fields like name and age from employee class. Full-time staff class also needs its unique salary fields and method. 

## Conclusion
Inheritance along side emcapsulation and polymorphism, are three core properties of OOP in Java. Inheritance allows one class(sub-class) to "inherit" some features like fiels and methods from another class(superclass AKA. parentclass). It is useful when subclass share some common features with its parentclass (some fields like with "final" keyword can not be inherited). "super" and "this" are two keywords to indicate fields and methods belong to superclass or subclass.
