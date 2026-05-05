# Frontdkk

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.1.0.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.


import java.util.*;

public class ListExample {
    public static void main(String[] args) {
        List<String> names = new ArrayList<>();

        names.add("Java");
        names.add("Python");
        names.add("Java");   // duplicates allowed

        System.out.println(names);
        System.out.println(names.get(1));  // Access by index
    }
}
================================================================
Java 8 Coding Questions with Line‑by‑Line Explanation
(Level: 4 Years Experience)

1️⃣ Filter Even Numbers From a List (Streams + Lambda)
✅ Code
Javaimport java.util.*;
import java.util.stream.*;
public class EvenNumbers {  
public static void main(String[] args) { 
List<Integer> numbers = Arrays.asList(10, 15, 20, 25, 30);       
numbers.stream()              
.filter(n -> n % 2 == 0)               
.forEach(System.out::println);   
}}
Show more lines
✅ Line‑by‑Line Explanation
JavaList<Integer> numbers = Arrays.asList(10, 15, 20, 25, 30);Show more lines

Creates a List of integers.
Arrays.asList() converts array elements into a List.

Javanumbers.stream()Show more lines

Converts the list into a Stream.
A stream is a sequence of elements supporting functional operations.
No processing happens yet (lazy execution).

Java.filter(n -> n % 2 == 0)Show more lines

filter() is an intermediate operation.
Takes a Predicate (returns boolean).
Keeps only numbers divisible by 2 (even numbers).

Java.forEach(System.out::println);Show more lines

forEach() is a terminal operation.
Iterates over filtered elements.
System.out::println is a method reference.


2️⃣ Count Frequency of Each Character in a String
✅ Code
Javaimport java.util.*;import java.util.stream.*;public class CharCount {    public static void main(String[] args) {        String input = "java";        Map<Character, Long> result =                input.chars()                     .mapToObj(c -> (char) c)                     .collect(Collectors.groupingBy(                         c -> c,                         Collectors.counting()                     ));        System.out.println(result);    }}``Show more lines
✅ Line‑by‑Line Explanation
JavaString input = "java";``Show more lines

Input string whose characters need to be counted.

Javainput.chars()``Show more lines

Returns an IntStream of ASCII values of characters.

Java.mapToObj(c -> (char) c)``Show more lines

Converts each ASCII value to a Character object.
Mandatory because groupingBy() works with objects.

Java.collect(...)``Show more lines

Terminal operation.
Collects stream elements into a collection (Map here).

JavaCollectors.groupingBy(    c -> c,    Collectors.counting())``Show more lines

Groups characters by themselves (c -> c).
counting() counts occurrences.
Result: Map<Character, Long>


3️⃣ Find First Non‑Repeated Character
✅ Code
Javaimport java.util.*;import java.util.stream.*;public class FirstUniqueChar {    public static void main(String[] args) {        String input = "swiss";        Character result =            input.chars()                 .mapToObj(c -> (char) c)                 .collect(Collectors.groupingBy(                     c -> c,                     LinkedHashMap::new,                     Collectors.counting()                 ))                 .entrySet()                 .stream()                 .filter(e -> e.getValue() == 1)                 .map(Map.Entry::getKey)                 .findFirst()                 .orElse(null);        System.out.println(result);    }}Show more lines
✅ Line‑by‑Line Explanation
Javainput.chars()Show more lines

Converts string into character ASCII stream.

JavaLinkedHashMap::newShow more lines

Maintains insertion order.
Important to preserve original string order.

Java.entrySet().stream()Show more lines

Converts Map entries into a stream.

Java.filter(e -> e.getValue() == 1)Show more lines

Keeps only characters that appear once.

Java.findFirst()Show more lines

Returns the first matching element.

Java.orElse(null)Show more lines

Avoids NoSuchElementException.


4️⃣ Find Second Highest Number
✅ Code
Javaimport java.util.*;
public class SecondHighest { 
public static void main(String[] args) {      
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 30);     
int secondHighest = numbers.stream().distinct()
  .sorted(Comparator.reverseOrder())
    .skip(1).findFirst()    
    .orElseThrow();        
  System.out.println(secondHighest);    }}Show more lines
✅ Explanation
Java.distinct()Show more lines

Removes duplicate values (important when max repeats).

Java.sorted(Comparator.reverseOrder())Show more lines

Sorts numbers in descending order.

Java.skip(1)Show more lines

Skips the first element (highest).

Java.findFirst()Show more lines

Fetches second highest number.


5️⃣ Employee Sorting by Salary
✅ Employee Class
Javaclass Employee {    int id;    String name;    double salary;    // getters    public double getSalary() {        return salary;    }}``Show more lines
✅ Code
Javaemployees.stream()         .sorted(Comparator.comparingDouble(Employee::getSalary))         .forEach(e -> System.out.println(e.name));Show more lines
✅ Explanation
JavaComparator.comparingDouble(Employee::getSalary)Show more lines

Extracts salary from Employee.
Sorts employees based on salary.

JavaEmployee::getSalaryShow more lines

Method reference.
Replaces lambda (e) -> e.getSalary().


6️⃣ Reduce – Sum of Numbers
✅ Code
Javaint sum =    numbers.stream()           .reduce(0, (a, b) -> a + b);System.out.println(sum);Show more lines
✅ Explanation
Java.reduce(0, (a, b) -> a + b)Show more lines

0 → identity value.
a → accumulated result.
b → current value from stream.
Adds elements one by one.


7️⃣ Optional – Null Safety
✅ Code
JavaOptional<String> name = Optional.ofNullable(getName());String value = name.orElse("Default");System.out.println(value);Show more lines
✅ Explanation
JavaOptional.ofNullable(getName())Show more lines

Wraps possibly null value safely.

Java.orElse("Default")Show more lines

Returns default if value is null.

✅ Prevents NullPointerException.

8️⃣ Java 8 Date & Time API
✅ Code
Javaimport java.time.*;public class DateExample {    public static void main(String[] args) {        LocalDate today = LocalDate.now();        LocalDate tomorrow = today.plusDays(1);        System.out.println(today);        System.out.println(tomorrow);    }}Show more lines
✅ Explanation
JavaLocalDate.now()Show more lines

Gets current date.
Immutable and thread‑safe.

Javatoday.plusDays(1)Show more lines

Returns new object.
Original date not modified.


🔥 Interview Must‑Say Points (4 YOE)
✅ Streams are lazy
✅ Terminal operation triggers execution
✅ Lambdas work only with functional interfaces
✅ map() vs flatMap() difference
✅ Parallel streams are not always faster
✅ Avoid Optional in entity fields

✅ What I Can Help You With Next

✅ 20 real Java 8 interview questions with answers
✅ flatMap() explained with real‑world examples
✅ Java 8 mock interview
✅ Tricky stream programs asked by MNCs

Just tell me what you want next 👌
Provide your feedback on BizChatDrop your files hereMessage CopilotFilesFilesAI
==================================================================================

Serialization is the process of converting a Java object into a byte stream so that it can be stored in a file, sent over a network, or persisted, and later reconstructed back into an object using deserialization.

✅ Why Serialization is Needed (Very Important)
You should clearly state USE CASES:

To persist object state (save to file or DB)
To send objects over network (RMI, distributed systems)
To cache objects
To support Cloning / Deep copy
Used internally in HTTP Sessions, JMS, RMI


✅ 3. How to Implement Serialization in Java
✅ Step‑by‑step Explanation
✅ Step 1: Implement Serializable Interface
import java.io.Serializable;

public class Employee implements Serializable {
    int id;
    String name;

    Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

✅ Explanation (Line by Line Logic)

Serializable is a marker interface
It has NO methods
JVM checks this marker at runtime
If not implemented → NotSerializableException

✅ Say this explicitly — very important interviewer expectation.

Step 2: Serialize the Object
FileOutputStream fos = new FileOutputStream("emp.ser");
ObjectOutputStream oos = new ObjectOutputStream(fos);

oos.writeObject(emp);
oos.close();

✅ Explanation

FileOutputStream → writes raw bytes to file
ObjectOutputStream → converts object into byte stream
writeObject() → triggers serialization
JVM converts:

primitive values
object references
into binary format

What is Marker Interface?
✅ Answer:

An interface with no methods
Used to give metadata information to JVM
Examples:

Serializable
Cloneable
RandomAccess

=================================================================================
2️⃣ ✅ Ideal Answer (How YOU Should Start)
✅ Definition (Clear & Crisp)

Multithreading is a Java feature that allows multiple threads to execute concurrently within a single process, enabling better CPU utilization, improved application performance, and responsiveness.
 Keywords interviewers expect:

Concurrent execution
Same process
Shared memory
Better performance
Why Multithreading Is Needed (Very Important)
You should clearly explain WHY, not just WHAT.
✅ Real Reasons:

To maximize CPU utilization
To perform multiple tasks simultaneously
To build responsive applications (UI remains active)
To improve throughput in server applications
To handle multiple client requests (web servers)

5️⃣ How Multithreading Is Achieved in Java
✅ Two Main Ways
✅ 1. By Extending Thread Class

class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running");
    }
}

public class Test {
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();
    }
}

Explanation:

run() contains thread logic
start() creates new call stack
JVM internally calls run()
Calling run() directly → NOT multithreading

✅ 2. By Implementing Runnable Interface (Preferred)
class MyTask implements Runnable {
    public void run() {
        System.out.println("Thread running");
    }
}

public class Test {
    public static void main(String[] args) {
        Thread t = new Thread(new MyTask());
        t.start();
    }
}
``
Why Runnable Is Better:

Supports multiple inheritance
Separates task from thread
Better design

6️⃣ Thread Life Cycle (Very Important)
✅ States:

New
Runnable
Running
Blocked / Waiting
Terminated

NEW → RUNNABLE → RUNNING → BLOCKED → TERMINATED

8️⃣ What Is Synchronization? (Critical Topic)
✅ Definition:

Synchronization ensures that only one thread accesses a shared resource at a time to maintain data consistency.

1️⃣3️⃣ Thread Pool & Executor Framework (Senior Topic)
✅ Why Thread Pool?

Creating threads is expensive
Reuse threads
Better resource management
===========================================================================================================
Coding Problems- Employee
==========================================================================================================


Employee-Based Java 8 Coding Questions

Employee class::
--------------------
class Employee {
    private int id;
    private String name;
    private String department;
    private double salary;
    private int age;

    public Employee(int id, String name, String department, double salary, int age) {
        this.id = id;
        this.name = name;
        this.department = department;
        this.salary = salary;
        this.age = age;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getDepartment() {
        return department;
    }

    public double getSalary() {
        return salary;
    }

    public int getAge() {
        return age;
    }

    public String toString() {
        return id + " " + name + " " + department + " " + salary + " " + age;
    }
}
---------------------
Sample Employee List:
List<Employee> employees = Arrays.asList(
        new Employee(1, "Ravi", "IT", 60000, 28),
        new Employee(2, "Anu", "HR", 45000, 26),
        new Employee(3, "Kiran", "IT", 80000, 32),
        new Employee(4, "Meena", "Finance", 70000, 30),
        new Employee(5, "Arun", "HR", 50000, 29)
);

-----------------------------------
 Find employees from IT department
 
List<Employee> itEmployees = employees.stream()
        .filter(e -> e.getDepartment().equals("IT"))
        .collect(Collectors.toList());

System.out.println(itEmployees);

-----------------------------------
Get only employee names
List<String> names = employees.stream()
        .map(Employee::getName)
        .collect(Collectors.toList());

System.out.println(names);

O/P: [Ravi, Anu, Kiran, Meena, Arun]
-----------------------------------
 Sort employees by salary ascending
 List<Employee> sortedEmployees = employees.stream()
        .sorted(Comparator.comparingDouble(Employee::getSalary))
        .collect(Collectors.toList());

System.out.println(sortedEmployees);

-----------------------------------
 Sort employees by salary descending
 List<Employee> sortedEmployeesDesc = employees.stream()
        .sorted(Comparator.comparingDouble(Employee::getSalary).reversed())
        .collect(Collectors.toList());

System.out.println(sortedEmployeesDesc);

-----------------------------------
Find highest paid employee
Employee highestPaid = employees.stream()
        .max(Comparator.comparingDouble(Employee::getSalary))
        .orElseThrow();

System.out.println(highestPaid);

-----------------------------------
Find lowest paid employee

Employee lowestPaid = employees.stream()
        .min(Comparator.comparingDouble(Employee::getSalary))
        .orElseThrow();

System.out.println(lowestPaid);

-----------------------------------
Group employees by department
Map<String, List<Employee>> employeesByDepartment = employees.stream()
        .collect(Collectors.groupingBy(Employee::getDepartment));

System.out.println(employeesByDepartment);

Interview explanation:
groupingBy() groups data based on a classifier function and returns a Map.
-----------------------------------
 Count employees in each department
 Map<String, Long> countByDepartment = employees.stream()
        .collect(Collectors.groupingBy(
                Employee::getDepartment,
                Collectors.counting()
        ));

System.out.println(countByDepartment);

O/P:{Finance=1, HR=2, IT=2}
-----------------------------------
 Find average salary of each department
 Map<String, Double> avgSalaryByDepartment = employees.stream()
        .collect(Collectors.groupingBy(
                Employee::getDepartment,
                Collectors.averagingDouble(Employee::getSalary)
        ));

System.out.println(avgSalaryByDepartment);

-----------------------------------
Find total salary of all employees
double totalSalary = employees.stream()
        .mapToDouble(Employee::getSalary)
        .sum();

System.out.println(totalSalary);

-----------------------------------
 Find employees whose salary is greater than 60000
 List<Employee> highSalaryEmployees = employees.stream()
        .filter(e -> e.getSalary() > 60000)
        .collect(Collectors.toList());

System.out.println(highSalaryEmployees);

-----------------------------------
Convert employee list to map using id as key and name as value
Map<Integer, String> employeeMap = employees.stream()
        .collect(Collectors.toMap(
                Employee::getId,
                Employee::getName
        ));

System.out.println(employeeMap);

-----------------------------------
Find department with highest average salary
Map<String, Double> avgSalaryByDepartment = employees.stream()
        .collect(Collectors.groupingBy(
                Employee::getDepartment,
                Collectors.averagingDouble(Employee::getSalary)
        ));

Map.Entry<String, Double> highestAvgDept = avgSalaryByDepartment.entrySet()
        .stream()
        .max(Map.Entry.comparingByValue())
        .orElseThrow();

System.out.println(highestAvgDept);

-----------------------------------
For 4 years Java developer, practice these strongly:

Duplicate elements
Frequency count
First non-repeated character
Second highest number
Employee grouping by department
Average salary by department
Convert list to map
Duplicate key handling in toMap()
map() vs flatMap()
Optional usage

These are the most commonly asked Java 8 coding patterns.
-------------------
Difference between map() and flatMap()
map():
List<String> names = Arrays.asList("java", "spring");
List<String> result = names.stream()
        .map(String::toUpperCase)
        .collect(Collectors.toList());
                .collect(Collectors.toList());
Used for one input → one output.
        
flatMap():
List<List<String>> data = Arrays.asList(
        Arrays.asList("Java", "Spring"),
        Arrays.asList("Hibernate", "JPA")
);
List<String> result = data.stream()
        .flatMap(List::stream)
        .collect(Collectors.toList());
Used for one input → multiple outputs, then flattening.
----------------------------------------------------------------
optional usage:
String name = null;

String result = Optional.ofNullable(name)
        .orElse("Default Name");

System.out.println(result);
--------------------------------------------------------







