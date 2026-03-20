# Record class in Java 17

A **record** is a special class used to create immutable data carrier objects with minimal boilerplate code.

**Declaration of Record class**
record Person(String name, int age) {}

**Are records immutable?**
👉 Yes
All fields are final.
No setters.
State cannot change after creation

**How do you access record fields?**
Person p = new Person("Amit", 25);
p.name();  // getter-like method

**Can a record extend a class?**
👉 ❌ No
👉 It implicitly extends java.lang.Record

**Can a record implement interfaces?**
👉 ✅ Yes
record Person(String name) implements Serializable {}

**Can we add methods inside a record?**
👉 ✅ Yes
record Person(String name) {
    public String greet() {
        return "Hello " + name;
    }
}

**What is a compact constructor?**
👉 A constructor without parameter declaration:
record Person(String name, int age) {
    public Person {
        if (age < 0) throw new IllegalArgumentException();
    }
}

**Can we override methods in a record?**
👉 ✅ Yes
You can override:
toString()
equals()
hashCode()



