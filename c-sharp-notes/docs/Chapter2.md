# Variables

## Local Variables

Local vars exist inside of methods and only exist during execution of that method. Once that method returns, memory allocated to the variables is released. You can use the **var** keyword to declare local variables, though not necessary.

### Inferring

When you use var, the data assigned causes the compiler to infer what type to assign.

## Format

| Name convention | Example                               | Used for                                                 |
|-----------------|---------------------------------------|----------------------------------------------------------|
| Camel Case      | cost, orderDetail, dateOfBirth        | Local Variables, Private Fields                          |
| Pascal Case     | String, Int32, Cost, DateOfBirth, Run | Types, non-private fields, and other member like methods.|

## Strings
| Type | Definition | Assignment|
|------|------------|-----------|
| Char | A single letter (A, B, etc), unicode character | Char letter ='A';|
| String | Multiple chars are stored as a string.| string myName="Mike";|

### Numbered Positional Arguments Example

```c#
int numberOfApples = 12; 
decimal pricePerApple = 0.35M;
Console.WriteLine(
  format: "{0} apples cost {1:C}", 
  arg0: numberOfApples,
  arg1: pricePerApple * numberOfApples);
string formatted = string.Format(
  format: "{0} apples cost {1:C}",
  arg0: numberOfApples,
  arg1: pricePerApple * numberOfApples);
//WriteToFile(formatted); // writes the string into a file
```

### Interpolated Strings Example

```c#
/*
    Has a slew of cons, generally avoid but can be easy quick way to make a quick concatenated string
*/
private const string firstname = "Omar";
private const string lastname = "Rudberg";
private const string fullname = firstname + " " + lastname;

// post c# 10
private const string fullname = $"{firstname} {lastname}";

```

### Format Strings

```c#
/*
Syntax: { index [, alignment ] [ : formatString ] }
*/
string applesText = "Apples"; 
int applesCount = 1234;
string bananasText = "Bananas"; 
int bananasCount = 56789;
Console.WriteLine(
  format: "{0,-10} {1,6}",
  arg0: "Name",
  arg1: "Count");
Console.WriteLine(
  format: "{0,-10} {1,6:N0}",
  arg0: applesText,
  arg1: applesCount);
Console.WriteLine(
  format: "{0,-10} {1,6:N0}",
  arg0: bananasText,
  arg1: bananasCount);

```

### String Tips - Escape Characters

Literal strings allow you to not have to use escape characters all over the place.

| Char | Example |
|------|---------|
|@ | string literalString = @"c:\temp\"|
|\\' | single quote, needed for character literal.|
|\\" | double quote, needed for string literal.|
|\\\\ | backslash |
| \\0 | unicode char 0 |
| \\b | backspace |
| \\n | New line |
| \\r | carriage return |
| \\t | horizontal rule |
| \\v | vertical tab |

## Integers

| Type | Definition | Assignment|
|------|------------|-----------|
| uint | unsigned integer, positive whole number or 0 | uint naturalNumber = 23; |
| int | integer means negative or positive whole number, or 0. 4 bytes, -2,147,483,648 to 2,147,483,647.  | int integerNumber = -23; |
| float | Float means single-precision floating point | float realNumber = 2.3F; | 
| double | Double means double-precision floating point, default type for a number value with a decimal point. 8 bytes, huge numbers (- and +). Only use when precision isn't necessary, for example 0.1 cannot be represented as a floating-point value. For example, don't use it for == conditions but perfect for > < | double realNumber = 2.3;|
| decimal | Decimal supports decimals, 16 bytes -79,228,162,514,264,337,593,543,950,335 to 79,228,162,514,264,337,593,543,950,335 | decimal decimalNumber = |

### Int Tips

| Char | Definition |
|------|------------|
| _ | Used to seperate numbers easier, for example 2_000_000 is 2000000 |
| 0b | Binary notation (base 2), 2000000 is 0b_0001_1110_1000_0100_1000_0000 |
| 0x | Hex notation (base 16), 0-9, A-F, 2000000 is 0x_001E_8480 |

## Boolean

Boolean can only be one of two values, true or false. Generally used to branch and loop.

## Object

This can be a poor performing choice and should be avoided when possible, instead relying on generics.

## Using Statements

### Static Using

You can simplify **using** by calling a static class for instance so you no longer need to call the class out everytime.

```C#
using static System.Console;
Write("Press any key combination: "); 
ConsoleKeyInfo key = ReadKey(); 
WriteLine();
WriteLine("Key: {0}, Char: {1}, Modifiers: {2}",
  arg0: key.Key, 
  arg1: key.KeyChar,
  arg2: key.Modifiers);
```

You can also modify the .csproj file, after the \<PropertyGroup\> section, add a new \<ItemGroup\> section to statically import a class. For example

```xml
<ItemGroup>
  <Using Include="System.Console" Static="true" />
</ItemGroup>
```

### Global Using

You can modify the \obj\debug\net7.0\\<project\>.GlobalUsings.g.cs file to include namespaces to import into all .cs files by default, for example:

```c#
// <auto-generated/>
global using global::System;
global using global::System.Collections.Generic;
global using global::System.IO;
global using global::System.Linq;
global using global::System.Net.Http;
global using global::System.Threading;
global using global::System.Threading.Tasks;
```

## Passing arguments to console app

Default variable of **args** gets assigned all arguments

1. Navigate to Project > Properties.
2. Select the Debug Tab > Click Open Debug Launch Profiles UI
3. Add in your command line arguments.

## async and await

Beginning in C# 5, two key words were created when working with the **Task** type, async and await. These are useful for

1. Implementing multitasking for a graphical user interface (GUI).
2. Scaling web apps and web services
3. Preventing blocking calls when working with filesystems, databases, remote sessions, etc.

### random code snips I need for final of ch2

```C#
Console.WriteLine($"int uses {sizeof(int)} bytes and can store numbers in the range {int.MinValue:N0} to {int.MaxValue:N0}."); 
Console.WriteLine($"double uses {sizeof(double)} bytes and can store numbers in the range {double.MinValue:N0} to {double.MaxValue:N0}."); 
Console.WriteLine($"decimal uses {sizeof(decimal)} bytes and can store 
```
