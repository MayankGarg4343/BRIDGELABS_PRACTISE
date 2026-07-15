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

IS-A relationship is the simplest relationship in which the one class is a type of another class.

🌟like inheritance:

class Animal{
    void eat(){
        System.out.println("eating");
    }
}
class Dog extends Animal{
    void bark(){
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
// this is the example of the inheritance.

HAS-A relationship -> It tells how strongly two objects depend on eachother.

🌟Association — two objects known about eachother and nothing more and both are independent.

for example:

class Student{
    String name;
    Student(String name){
        this.name = name;
    }
}
class Teacher{
    String name;
    Teacher(String name){
        this.name = name;
    }
    void teach(Student student){
        System.out.println(name+" teaches "+student.name);
    }
}
class Main {
    public static void main(String[] args) {
        Student s = new Student("mayank");
        Teacher t = new Teacher("amit");
        t.teach(s);
    }
}

🌟Aggregation - It is more stronger and one object contains another object and the contained object can live independently.

for exmample - department ◊---------  professor

class Professor{
    String name;
    Professor(String name){
        this.name = name;
    }
}
class Department{
    String name;
    List<Professor> professors;
    Department(String name, List<Professor>professors){
        this.name = name;
        this.professors = professors;
    }
}

Professor p1 = new Professor("A");
Professor p1 = new Professor("B");
Department cs = new Department("CS",List.of(p1,p2));

🌟Composition - it is the strongest relationship and the whole object creates and owns the part and if 
                whole dies then the part also dies.

class Engine{
    Engine(){
        System.out.println("Engine created");
    }
}
class Car{
    private Engine engine;
    Car(){
        engine = new Engine();
    }
}
Car car = new Car();

/// here the engine is created inside the car.