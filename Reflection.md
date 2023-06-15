
Table of Content
- [1. Reflection in C#](#1-reflection-in-c)
  - [1.1. Definition](#11-definition)
  - [1.2. Reflection with 'Type' object](#12-reflection-with-type-object)
    - [1.2.1. The type's Type object representation:](#121-the-types-type-object-representation)
    - [How can I get Type object of Value Types (Primitive Type) ?](#how-can-i-get-type-object-of-value-types-primitive-type-)
- [2. Explain Keywords](#2-explain-keywords)
      - [2.0.0.1. Simple Explain about 'Metadata'](#2001-simple-explain-about-metadata)


# 1. Reflection in C#
---

## 1.1. Definition

Reflection in C# is used to retrieve `metadata` on types on runtime. In other words, you can use reflection to inspect `metadata` of the types in your program dynamically.

You can retrieve information on the loaded assemblies and the types defined in them.

To work with the reflection in .Net, you should include the **System.Reflection** namespace in your program. In using reflection, you get objects of the type **Type** that can be used to represent aseemblies, types, or modules.

``` cs
// Include System.Reflection namespace
using System.Reflection;
```
## 1.2. Reflection with 'Type' object

### 1.2.1. The type's Type object representation:
* Classes
* Value Types
* Arrays
* Interfaces
* Enumerations
* Delegates
* Constructed generic types and generic type definition
* Type arguments and type parameters of constructed generic types, generic type definitions, and generic method definitions

Reference: [Type Object in .Net](https://learn.microsoft.com/en-us/dotnet/api/system.type?view=net-7.0)


### How can I get Type object of Value Types (Primitive Type) ?

**1. The ==first way== I can get the Type object based on the value through the **GetType** method.**

```cs
object[] values = { "word", true, 120, 6.6 };

foreach (var value in values)
{
    Console.WriteLine($"{value} - type: {value.GetType().Name}");
}
```

The Result:
![Result](../Note_CS/img/Reflection/print_value_types_using_GetType_method.PNG)


**2. The ==second way== I can get the Type object by using 'typeof' operator.**

``` cs

Type[] typeValues = { typeof(int), typeof(double), typeof(float), typeof(string) };

foreach (var typeValue in typeValues)
{
    Console.WriteLine($"{typeValue.Name}");
}
```

The result:
![Result](../Note_CS/img/Reflection/get_Type_object_by_using_typeof_operator.PNG) 

**3. How can I get Type object of user-defined type?**
**3.1 We can ==use the same way as Value Types== by using the **GetType** method.**
Assumed that I have a Customer class:

``` cs
public class Customer
{
    public int Id { get; set; }
    public string? Name { get; set; }
    public string? Address { get; set; }
}
```

I want to get Type object after creating the Customer object and named 'c':

``` cs
Customer c = new Customer();

Type customerTypeByGetType = c.GetType();

Console.WriteLine($"Customer type of c object is : {customerTypeByGetType.Name}");
```
The result:
![Result](./img/Reflection/get_Type_object_after_creating_user_defined_object.PNG)

**3.2 We can use the typeof operator for getting Type object from user-defined type**

```cs
Type customerTypeByTypeof = typeof(Customer);

Console.WriteLine($"Customer type of Customer class is : {customerTypeByTypeof.Name}");
```
The result: 
![Result](./img/Reflection/get_Type-object-through-user-defined-type_ver2.PNG)

I have separated by using the typeof operator and GetType method in user-defined to not be mistaken.

---
# 2. Explain Keywords

#### 2.0.0.1. Simple Explain about 'Metadata'
- The ==main purpose== of the **metadata** is to know the information of the class, data members, inheritance, and data types, etc,... of the class.
- Metadata is the file consists of the table and heap data structures.

**References**:
[Metadata in C#](https://www.educba.com/metadata-in-c-sharp/)



