# Object-Oriented Programming (OOP) Relationships

## Relationship Hierarchy

```text
                    Object
                       │
     ┌─────────────────┴──────────────────┐
     │                                    │
 Structural                       Behavioral
     │                                    │
     │                             Dependency
     │
     ├───────────────┐
     │               │
   IS-A            HAS-A
     │               │
Inheritance      Association
Realization          │
                ┌────┴────┐
                │         │
          Aggregation  Composition
```

## IS-A Relationship

The **IS-A** relationship is the simplest relationship in which one class is a type of another class.

### 🌟 Inheritance

```java
class Animal {
    void eat() {
        System.out.println("eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("barking");
    }
}

class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.bark();
        d.eat();
    }
}
```

> This is the example of **Inheritance**.

---

## HAS-A Relationship

It tells how strongly two objects depend on each other.

### 🌟 Association

Two objects know about each other and nothing more, and both are independent.

**Example:**

```java
class Student {
    String name;

    Student(String name) {
        this.name = name;
    }
}

class Teacher {
    String name;

    Teacher(String name) {
        this.name = name;
    }

    void teach(Student student) {
        System.out.println(name + " teaches " + student.name);
    }
}

class Main {
    public static void main(String[] args) {
        Student s = new Student("mayank");
        Teacher t = new Teacher("amit");

        t.teach(s);
    }
}
```

---

### 🌟 Aggregation

It is stronger than Association. One object contains another object, and the contained object can live independently.

**Example:**

```text
Department ◇--------- Professor
```

```java
class Professor {
    String name;

    Professor(String name) {
        this.name = name;
    }
}

class Department {
    String name;
    List<Professor> professors;

    Department(String name, List<Professor> professors) {
        this.name = name;
        this.professors = professors;
    }
}

Professor p1 = new Professor("A");
Professor p2 = new Professor("B");

Department cs = new Department("CS", List.of(p1, p2));
```

---

### 🌟 Composition

It is the strongest relationship. The whole object creates and owns the part, and if the whole object dies, then the part also dies.

```java
class Engine {
    Engine() {
        System.out.println("Engine created");
    }
}

class Car {
    private Engine engine;

    Car() {
        engine = new Engine();
    }
}

Car car = new Car();
```

> Here, the `Engine` is created inside the `Car`.
