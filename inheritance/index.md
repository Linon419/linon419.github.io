# Inheritance

When you inherit from an existing class, you reuse its method, and you can add new method and fields to adapt your new class to new situations.
<!--more-->
##Classes, super class, and child class
## Defining Subclass
There are two ways to get the fiels of super class from child class.
1. Access directly, firstly use the left of "="
2. Access from method, who's method, use who, otherwise find super class
//super class
'''
public class Employee {
    int salary = 20;
    public void Employee(){
        System.out.println(salary);
    }
}
```
// child class
```

public class Manager extends Employee {
    private double bonus;
    int price = 200;
    int salary = 300;
    public void Manager(){
        System.out.println(salary);
    }
}
```

```
public class Main {
    public static void main(String[] args) {
        Manager m = new Manager();
        System.out.println(m.price);//200
        System.out.println(m.salary);//300
        System.out.println("-----------------");
        //System.out.println(m.salary);

        m.Manager();//300
        m.Employee();//20
    }

}
```

## this and super
- this refers to the current object.
- super keyword in java is a reference variable that is used to refer parent class objects
super class
```
public class Employee {
    int age = 20;
}
```
child class

```
public class Manager extends Employee{
    int age = 30;
    public void method(){
        int age = 40;
        System.out.println(age);//40
        System.out.println(this.age);//30
        System.out.println(super.age);//20
    }
}
```

public class Main {
    public static void main(String[] args) {
        Manager m = new Manager();
        m.method();
    }
}
```
## override
In any object-oriented programming language, Overriding is a feature that allows a subclass or child class to provide a specific implementation of a method that is already provided by one of its super-classes or parent classes.(override method must have the same name and 参数列表)

```
public class Employee {
    int salary = 10;
    int bonus = 5;

    public int getSalary() {
        return salary;
    }

    public int getBonus() {
        return bonus;
    }
}
```

```
public class Manager extends Employee{
        int bonus = 3;
        @Override
        public int getSalary(){
            int salary = super.getSalary();
            return salary + bonus;
        }

}
```

```
public class Main {
    public static void main(String[] args) {
        Manager m = new Manager();
        int salary = m.getSalary();
        System.out.println(salary);
    }
}

```
The result is 13

