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