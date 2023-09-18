# InterviewPreparing
----------------------------------------------------------------
## C# Interview questions 
----------------------------------------------------------------
### 1. Differentiate between Boxing and Unboxing.

When a value type is converted to an object type, the process is known as boxing; whereas, when an object type is converted to a value type, the process is known as unboxing. 

Boxing and unboxing enable value types to be treated as objects. Boxing a value type packages it inside an instance of the Object reference type. This allows the value type to be stored on the garbage collected heap. Unboxing extracts the value type from the object. In this example, the integer variable iis  boxed and assigned to object obj. 

Boxing Example:
```
public void function1()
{
    int i =111; object o = i;//implicit unboxing
    console.writeline(o); 
}
```
Unboxing Example:

```
public void function1()
{
    object o =111;
    int i = (int)o;//explicit unboxing
    console.writeline(i);   
}
```

### 2. What is the difference between Interface and Abstract Class?

|Abstract Class	|Interface|
|----           |-------- |
|Used to declare properties, events, methods, and fields as well.	|Fields cannot be declared using interfaces.
|Provides the partial implementation of functionalities that must be implemented by inheriting classes.	|Used to declare the behavior of an implementing class.
|Different kinds of access modifiers like private, public, protected, etc. are supported.	|Only public access modifier is supported.
|It can contain static members.	|It does not contain static members.
|Multiple inheritances cannot be achieved.	|Multiple inheritances are achieved.

### 3. What is the difference between string and StringBuilder in C#?

StringBuilder and string both use to store string value but both have many differences on the bases of instance creation and also for 
performance:

String: 

String is an immutable object. Immutable like when we create string object in code so we cannot modify or change that object in any 
operations like insert new value, replace or append any value with existing value in string object, when we have to do some operations 
to change string simply it will dispose the old value of string object and it will create new instance in memory for hold the new value 

StringBuilder:

Stringbuilder is mutable object which also hold the string value, mutable means once we create a System.Text.Stringbuilder 
object we can use this object for any operation like insert value in existing string with insert functions also replace or append 
without creating new instance of System.Text.Stringbuilder for every time so it’s use the previous object so it’s work fast as compare 
than System.String

### 4. What are delegates in C#?

A delegate is a .NET object which defines a method signature and it can pass a function as a parameter.<br>
Delegates always point to a method that matches its specific signature. Users can encapsulate the reference of a method in a delegate object.<br>
When we pass the delegate object in a program, it will call the referenced method. To create a custom event in a class, we can make use of delegate.

### 5. What is sealed class in c#?

Sealed classes are used to restrict the inheritance feature of object oriented programming. Once a class is defined as a sealed class, the class cannot be inherited.

In C#, the sealed modifier is used to define a class as sealed. In Visual Basic .NET the Not Inheritable keyword serves the purpose of sealed. If a class is derived from a sealed class then the compiler throws an error.

If you have ever noticed, structs are sealed. You cannot derive a class from a struct.

### 6. What happens if the inherited interfaces have conflicting method names?

If we implement multiple interface in the same class with conflict method name so we don’t need to define all or in other words we can say if we have conflict methods in same class so we can’t implement their body independently in the same class coz of same name and same signature so we have to use interface name before method name to remove this method confiscation let’s see an example: 

```
    interface testInterface1
    {
        void Show();
    }

    interface testInterface2
    {
        void Show();
    }
    class Abc : testInterface1,testInterface2
    {
        void testInterface1.Show()
        {
            Console.WriteLine("For testInterface1 !!");
        }

        void testInterface2.Show()
        {
            Console.WriteLine("For testInterface2 !!");
        }
    }

    static void Main()
    {
        testInterface1 obj1 = new Abc();
        testInterface2 obj2 = new Abc();

        obj1.Show();
        obj2.Show();
    }

```

### 7. What’s the difference between the System.Array.CopyTo() and System.Array.Clone()?

**Clone** - Method creates a shallow copy of an array. A shallow copy of an Array copies only the elements of the Array, whether they are reference types or value types, but it does not copy the objects that the references refer to. The references in the new Array point to the same objects that the references in the original Array point to.

**CopyTo** - The Copy static method of the Array class copies a section of an array to another array. The CopyTo method copies all the elements of an array to another one-dimension array. The code listed in Listing 9 copies contents of an integer array to an array of object types.

### 8. Difference between “is” and “as” operator in C#

"is" operator- In the C# language, we use the "is" operator to check the object type. If the two objects are of the same type, it returns true and false if not. Let's understand the preceding from a small program. We defined the following two classes:

```
class Speaker 
{
    public string Name { get; set; } 	
}

class Author 
{
    public string Name { get; set; } 
}

// Now, let's try to check the preceding types as:
var speaker = new Speaker { Name="Gaurav Kumar Arora"};
var isTrue = speaker is Speaker;

// In the preceding, we are just checking the matching type, so the results as true.
// and here is return false
var isTrue = speaker is Author;

```

"as" operator behaves similar to the "is" operator. The only difference is it returns the object if both are compatible to that type else it returns null.

### 9. what is Nullable Types in .Net?

A nullable Type is a data type is that contain the defined data type or the value of null. You should note here that here variable datatype has been given and then only it can be used.

This nullable type concept is not compatible with "var".

### 10. Can you describe the accessibility modifiers in c#.Net?

Access modifiers are keywords used to specify the declared accessibility of a member or a type

Access modifiers are an integral part of object-oriented programming. They support the concept of encapsulation, which promotes the idea of hiding functionality. Access modifiers allow you to define who does or doesn't have access to certain features. In C# there are 5 different types of Access Modifiers:

1. **Public**: There are no restrictions on accessing public members
1. **Private**: Access is limited to within the class definition. This is the default access modifier type if none is formally specified
1. **Protected**: Access is limited to within the class definition and any class that inherits from the class
1. **Internal**: Access is limited exclusively to classes defined within the current project assembly
1. **Protected internal**: Access is limited to current assembly

### 11. What do you understand by Value types and Reference types in C#.Net?

In C# data types can be of two types: Value Types and Reference Types. Value type variables contain their object (or data) directly. If we copy one value type variable to another then we are actually making a copy of the object for the second variable. Both of them will independently operate on their values, Value Type member will locate into Stack and reference member will locate in Heap always. Let consider each case briefly:

- **Pure Value Type**: Here I used a structure as a value type. It has an integer member. I created two instances of this structure. Afterwards I assigned second instance to the first one. Then I changed the state of second instance, but it hasn't effect the first one, as whole items are value type and assignments on those types will copy only values not references i.e. in a Value Type assignment, all instances have its own local copy of members.

- **Pure Reference Type**: I created a class and added a "DataTable" as a Reference Type member for this class. Then I performed the assignments just like below. But the difference is that on changing the state of second instance, the state of first instance will automatically alter. So in a Reference Type assignment both Value and Reference will be assigned i.e. all instances will point to the single object.

- **Value Type with Reference Type**: This case and the last case to come are more interesting. I used a structure in this particular scenario also. But this time it includes a Reference Type (A Custom Class Object) Member besides a Value Type (An Integer) Member. When you performing the assignments, it seems like a swallow copy, as Value Type member of first instance won't effected, but the Reference Type member will alter according to the second instance. So in this particular scenario, assignment of Reference Type member produced a reference to a single object and assignment of Value Type member produced a local copy of that member.

- **Reference Type With Value Type** : Contrary to the above case, in this scenario, both Reference & Value Types will be affected. I.e. a Value Type member in a Reference Type will be shared among its instances.

### 12. What is the use of using statement in C#?

The .Net Framework provides resource management for managed objects through the garbage collector - You do not have to explicitly allocate and release memory for managed objects. Clean-up operations for any unmanaged resources should perform in the destructor in C#. To allow the programmer to explicitly perform these clean-up activities, objects can provide a Dispose method that can be invoked when the object is no longer needed. The using statement in C# defines a boundary for the object outside of which, the object is automatically destroyed. The using statement is excited when the end of the "using" statement block or the execution exits the "using" statement block indirectly, for example - an exception is thrown. The "using" statement allows you to specify multiple resources in a single statement. The object could also be created outside the "using" statement. The objects specified within the using block must implement the IDisposable interface. The framework invokes the Dispose method of objects specified within the "using" statement when the block is exited.

### 13. Can you Explain Hashtable in C#?

A Hashtable is a collection that stores (Keys, Values) pairs. Here, the Keys are used to find the storage location and are immutable and cannot have duplicate entries in the Hashtable. The .Net Framework has provided a Hash Table class that contains all the functionality required to implement a hash table without any additional development. The hash table is a general-purpose dictionary collection. Each item within the collection is a DictionaryEntry object with two properties: a key object and a value object. These are known as Key/Value. When items are added to a hash table, a hashcode is generated automatically. This code is hidden from the developer. All access to the table's values is achieved using the key object for identification. As the items in the collection are sorted according to the hidden hash code, the items should be considered to be randomly ordered.

The Hashtable Collection: The Base Class libraries offers a Hashtable Class that is defined in the System.Collections namespace, so you don't have to code your own hash tables. It processes each key of the hash that you add every time and then uses the hash code to look up the element very quickly. The capacity of a hash table is the number of elements the hash table can hold. As elements are added to a hash table, the capacity is automatically increased as required through reallocation. It is an older .Net Framework type.

### 14. What are differences between Object, Var and Dynamic type?

**Object** from C# 1.0 
- It can store any kind of value, because object is the base class of all type in .NET framework. 
- Compiler has little information about the type. 
- Object type can be passed as method argument and method also can return object type. 
- Need to cast object variable to original type to use it and performing desired operations. 
- Cause the problem at run time if the stored value is not getting converted to underlying data type. 
- Useful when we don’t have more information about the data type.

**Var** from C# 3.0 
- It can store any type of value but It is mandatory to initialize var types at the time of declaration. 
- It is type safe i.e. Compiler has all information about the stored value, so that it doesn't cause any issue at run-time. 
- Var type cannot be passed as method argument and method cannot return object type. Var type work in the scope where it defined. 
- No need to cast because compiler has all information to perform operations. 
- Doesn't cause problem because compiler has all information about stored value. 
- Useful when we don’t know actual type i.e. type is anonymous.

**Dynamic** from C# 4.0 
- It can store any type of the variable, similar to old VB language variable. 
- It is not type safe i.e. Compiler doesn't have any information about the type of variable. 
- Dynamic type can be passed as method argument and method also can return dynamic type. 
- Casting is not required but you need to know the properties and methods related to stored type. 
- Cause problem if the wrong properties or methods are accessed because all the information about stored value is get resolve only at run time. 
- Useful when we need to code using reflection or dynamic languages or with the COM objects, because you need to write less code.

### 15. How can you implement multiple inheritance in C#?

we can use interfaces for multiple inheritance and no way to multiple inheritance from class

### 16. What is the difference between Array and Collections?

We need to specify the size of the Array at the time of declaration but while Working with collections it is not required to mention the size of the Collection because the size of the collection will be fixed at runtime -->The members of the Array must be of same datatype but collections can have elements of Different datatypes

### 17. what is the Difference between Event and Method?

Event will not have returntype but method will have returntype

### 18. Can you explain the difference between Task and Thread in .NET?

Thread represents an actual OS-level thread, with its own stack and kernel resources. Thread allows the highest degree of control; you can Abort() or Suspend() or Resume() a thread, you can observe its state, and you can set thread-level properties like the stack size, apartment state, or culture. ThreadPool is a wrapper around a pool of threads maintained by the CLR.

The Task class from the Task Parallel Library offers the best of both worlds. Like the ThreadPool, a task does not create its own OS thread. Instead, tasks are executed by a TaskScheduler; the default scheduler simply runs on the ThreadPool. Unlike the ThreadPool, Task also allows you to find out when it finishes, and (via the generic Task) to return a result.

### 19. What is a garbage collector?

Garbage collector frees the unused code objects in the memory. The memory heap is partitioned into 3 generations:

Generation 0: It holds short-lived objects.<br>
Generation 1: It stores medium-lived objects.<br>
Generation 2: This is for long-lived objects.<br>

Collection of garbage refers to checking for objects in the generations of the managed heap that are no longer being used by the application. It also performs the necessary operations to reclaim their memory. The garbage collector must perform a collection in order to free some memory space.<br>

During the garbage collection process:
- The list of live objects is recognized.
- References are updated for the compacted objects.
- The memory space occupied by dead objects is recollected. The remaining objects are moved to an older segment.
- System.GC.Collect() method is used to perform garbage collection in .NET.

### 20. Difference between Delegates and Events in C#

|Delegates | Events |
|----      | ----   |
|Delegate is a function pointer. It holds the reference of one or more methods at runtime.| The event is a notification mechanism that depends on delegates|
|Delegate is independent and not dependent on events.	|An event is dependent on a delegate and cannot be created without delegates. Event is a wrapper around delegate instance to prevent users of the delegate from resetting the delegate and its invocation list and only allows adding or removing targets from the invocation list.|
|Delegate includes Combine() and Remove() methods to add methods to the invocation list.	|EventInfo class inspect events and to hook up event handlers that include methods AddEventHandler() and RemoveEventHandler() methods to add and remove methods to invocation list, respectively.|
|A delegate can be passed as a method parameter.	|An event is raised but cannot be passed as a method parameter.|
|= operator is used to assigning a single method, and += operator is used to assign multiple methods to a delegate.	|= operator cannot be used with events, and only += and -= operator can be used with an event that adds or remove event handler. These methods internally call AddEventHandler and RemoveEventHandler methods.|


In a way, an event is a delegate only. The program code will work even if you remove the event keyword and only use a delegate. However, using the event keyword, we prevent subscribers to register with an event by using = operator and thereby removing all handlers.

Consider the following example.

```
public delegate void Notify();
public Notify MyDelegate;

MyDelegate = MyMethod;// valid
MyDelegate += MyMethod;// valid

public delegate void Notify();
public event Notify MyEvent;

MyEvent = MyEventHandler;// Error
MyEvent += MyEventHandler;// valid
```

### 21. Difference between Hashtable and Dictionary

|Hashtable | Dictionary |
|----      | ----   |
|Hashtable is included in the System.Collections namespace.	|Dictionary is included in the System.Collections.Generic namespace.|
|Hashtable is a loosely typed (non-generic) collection, this means it stores key-value pairs of any data types.	|Dictionary is a generic collection. So it can store key-value pairs of specific data types.|
|Hashtable is thread safe.	|Only public static members are thread safe in Dictionary.|
|Hashtable returns null if we try to find a key which does not exist.	|Dictionary throws an exception if we try to find a key which does not exist.|
|Data retrieval is slower than the dictionary collection because of boxing-unboxing.	|Data retrieval is faster than Hashtable because it is a type safe so no need of boxing-unboxing.|


