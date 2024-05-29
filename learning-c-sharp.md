# Learning C#

C# is a useful language to know - it is great for when we are working with windows and we can use it to craft a myriad of malicious programs.

These notes will hopefully help in the learning journey :smiley:

>[!TIP]
>If some concepts here are hazy it is worth having a look at [learning python](https://github.com/puzz00/learning-python/blob/main/python-notes.md) notes as more depth is given there for programing concepts such as what variables are and what the OOP paradigm is - python is another great language for hackers to know - it is close to our :purple_heart:

## Fundamentals

### Sorting the IDE and Workflow

Microsoft Visual Code is an excellent choice of IDE for working with C#

>[!NOTE]
>We will be using a *linux* OS - it is easy to find how to install vscode for any major OS by searching online - [useful downloads](https://code.visualstudio.com/download)

Once it is installed we need to go into the extensions and search for the *C# Dev Kit* which we then install.

![1](/images/1.png)

If *dontnet-sdk* is not installed on our system we need to install it - in these notes we will work with version 6

```bash
sudo apt install dotnet-sdk-6.0
```

![2](/images/2.png)

In order to code with C# in VSCode we first of all need to create a new project - we can open all the commands using `CTRL + SHIFT + P` and then use `.NET: New Project` We will then be shown a drop down menu of templates to use. To start with we are going to be using `Console App`

![3](/images/3.png)

We can now code using C#

When we want to compile and execute our code to test it we can just click into the `Run` menu and choose `Run without debugging` - the output will be shown in a terminal within VSCode itself.

![4](/images/4.png)

Once the code has compiled we will be able to find .dll files along with an .exe binary.

![6](/images/6.png)

#### Using Mono

We can use the opensource implementation of microsofts .NET framework which is [mono](https://www.mono-project.com/)

We can install it using `sudo apt install mono-complete`

![7](/images/7.png)

We can then code in VSCode or a text editor - VSCode is obviously better when available.

![8](/images/8.png)

Once mono is installed we can compile our source code using `mcs -out:test.exe test.cs`

![9](/images/9.png)

We can decompile our code using `monodis --output=decompiled_test.txt test.exe`

![10](/images/10.png)

### Variables

We need to *declare* and *initialize* variables before we can use them. We can declare a variable before it is initialized or we can declare and initialize it on one line.

We need to specify the *type* of the variable - if we are not initializing it at declaration - and once we have specified this type *it cannot change* later. This means that if we declare a variable called `age` as a `string` we cannot later reassign a different datatype - such an an `int` to it.

>[!NOTE]
>We can use `var` to replace all datatypes when we declare *and* initialize a variable at the same time since the compiler can infer the datatype from the value which is assigned to the variable - this is known as an *implicitly typed* variable as opposed to when we specify the datatype which is an *explicitly typed* variable

We can declare and initialize more than one variable at a time if they are of the same datatype.

>[!IMPORTANT]
>We *must* use `""` not `''` for *string* datatypes in C# as *single quotes* are used for *char* datatypes

```csharp
string greeting; // declare a string type variable
greeting = "hello world!"; // initialize the greeting variable
Console.WriteLine(greeting);

string farewell = "goodbye!"; // declare a string type variable and initialize it
Console.WriteLine(farewell);

int x = 8; // declare and initialize an int type variable
Console.WriteLine(x);

int y = 3, z = 5; // declare and initialize two variable of the same type
Console.WriteLine(y);
Console.WriteLine(z);

// implicityly typed variables
var name = "dduck";
var a = 10;
Console.WriteLine(name + a);
```

>[!TIP]
>In C# the most common way to name variables is to use lowerCamelCase

### Operators

We can use standard arithmetic operators as we would expect.

```csharp
int x = 15;
int y = 3;

int @sum = x + y;
int difference = x - y;
int product = x * y;
int quotient = x / y;

Console.WriteLine(@sum);
Console.WriteLine(difference);
Console.WriteLine(product);
Console.WriteLine(quotient);
```

>[!TIP]
>If we want to use a *keyword* such as `sum` as a variable name we can put `@` before it

We can concatenate *string* and *integer* datatypes using `+`

The returned datatype will be a *string*

```csharp
int x = 15;
int y = 3;

string @sum = "Sum: " + (x + y);
string difference = "Difference: " + (x - y);
string product = "Product: " + (x * y);
string quotient = "Quotient: " + (x / y);

Console.WriteLine(@sum);
Console.WriteLine(difference);
Console.WriteLine(product);
Console.WriteLine(quotient);
```

>[!NOTE]
>We wrap the equations in `()` because of precedence - we dont need to do it for `*` and `/` because they are higher in precednce than `+` but it looks cleaner if we do wrap them as shown above

#### Unary Operators

We can use *unary operators* such as `++` and `--` in C#

### String Interpolation

We can *interpolate* strings just as we can in other languages such as python and javascript.

The syntax for this in C# is we put `$` before the string and just like with an *f string* in python we use `{}` to place variables or expressions into.

Using *string interpolation* is a better way most of the time to embed variables or expressions into strings.

```csharp=
string animal = "cat";
int lives = 9;
System.Console.WriteLine($"The {animal} has got {lives} lives.");
System.Console.WriteLine($"{lives} + {lives} = {lives * 2}");
```

### User Input

We can get user input by using the `ReadLine()` method from the `Console` class - it always returns a `string` datatype.

```csharp
// reading user input
string userInput = Console.ReadLine();
System.Console.WriteLine("You wrote: " + userInput);
```

>[!TIP]
>In vscode we can use *code snippets* - to quickly access the `WriteLine()` method we can type `cw` followed by `TAB`

### Boolean Type and Equality

We can use *bool* datatypes as expected and the *equality operator* is as expected ie `==`

>[!TIP]
>When naming *boolean* datatype variables it is useful to begin with *is* to make it a question which can be answered *true* or *false* as it makes our code easier to understand

```csharp
// boolean datatypes
bool canSwim = true; // explicityly typed
var canFly = false; // implicityly typed

// equality operator ==
bool isFish = canSwim == true; // returns true
bool isBird = canFly == true; // returns true
bool isStarFish = canSwim == false; //returns false
bool isKiwi = canFly == false; //returns false
```

>[!NOTE]
>Apologies if star fish can swim - it seems they shouldnt be able to but we could be wrong

The *inequality operator* `!=` works as expected.

```csharp
// inequality operator
string userGender = "male";
bool isWoman = userGender != "male"; // returns false
```

We can use *logical negation* as expected.

```csharp
// logical negation
string userGender = "male";
bool isWoman = !(userGender == "male"); // returns false
```

### More Arithmetic Operators

We can use more arithmetic operators such as we would expect.

```csharp
// more arithmetic operators > < >= <= mod
int userAge = 17;
var canDrive = userAge > 16; // returns true
var isChild = userAge < 13; // returns false
var canVote = userAge >= 18; // returns false
var freeEntry = userAge <= 3; // returns false
bool isEven = userAge % 2 == 0; // returns false
```

### Logical Operators

We can use `&&` for *and*

We can use `||` for *or*

```csharp
// logical operators
// and &&
string userGender = "female";
int userAge = 25;
bool canMarry = userGender == "female" && userAge >= 21; // true as both sides are true

// or ||
vehicleType = "motorcycle";
int hp = 178;

bool isFun = vehicleType == "motorcycle" || hp >= 400; // true as left side is true
```

### Flow Control Using If Statements

We can use `if` statements on their own or in combination with `else if` and `else` blocks.

```csharp
// flow control
string userName = Console.ReadLine();
if(userName == "Daffy Duck")
{
    System.Console.WriteLine("Hello " + userName);
} else if(userName == "Bugs Bunny") {
    System.Console.WriteLine("Whats up doc?");
}
else {
    System.Console.WriteLine("Goodbye!");
}
```

### Code Blocks and Local Scope

The `{}` used in C# shows us a *code block*

When we are working with flow control we can see that the `if` statement has a *code block* which belongs to it - this is the code which will execute if the statement given is `true`

We can see that `if else` and `else` have their own code blocks.

This introduces us to the *scope* of variables - this essentialy determines where variables can be accessed in our code.

If we declare a variable inside a code block it will be *locally scoped* to that block - we will not be able to access it from other areas outside of that block.

![11](/images/11.png)

If we have declared a variable in a code block which itself has a code block or code blocks inside it, we can access that variable from the inner blocks since the blocks are in the scope of the outer block - a way we can picture this is if the variable does not exist in the namespace of an inner block then the program will bubble up and up and keep checking until it finds the variable.

![12](/images/12.png)

```csharp=
string userName = Console.ReadLine();
if(userName == "dduck")
{
    System.Console.WriteLine("Hello, " + userName);
    int userAge = 82;
    System.Console.WriteLine("You are: " + userAge); // we can use userAge here
    if(userAge > 70)
    {
        // we enter an inner code block
        System.Console.WriteLine(userName); // can bubble up to get userName
        System.Console.WriteLine("is " + userAge); //can bubble up to outer code block to get userAge
    }
}
else if(userName == "bbunny")
{
    System.Console.WriteLine("Whats up " + userName); // we can access userName but not userAge
}
else{
    System.Console.WriteLine("Goodbye!" + userName);
}
```

>[!IMPORTANT]
>We cannot bubble down so variables defined with local scope to *inner* code blocks cannot be accessed by *outer* code blocks

### Methods

Methods are blocks of code which we can call again and again once we have defined them - they help us make sure our code is concise and less prone to bugs.

#### Void Methods

Void methods do not *return* any values - we need to specify them using the `void` keyword before the name of the method.

In this example the `greeting` method saves us from writing the same lines of code over and over again.

Since it just prints output to the console we specify it is `void`

We *call* methods to get them to execute - we use the name of the method along with `()` to call them.

```csharp=
void Greeting() // void because nothing is returned
{
    System.Console.WriteLine("Hello - what a great day it is!");
}

System.Console.WriteLine("What is your name? ");
string userName = Console.ReadLine();
if(userName == "dave")
{
    Greeting(); // calling the Greeting method
}
else if(userName == "sarah")
{
    Greeting(); // calling the Greeting method
}
else if(userName == "billybob")
{
    Greeting(); // calling the Greeting method
}
else{
    System.Console.WriteLine("Goodbye!");
}
```

>[!TIP]
>Use *PascalCase* in which all first letters of all words are *upper case* when naming *methods* in C#

##### Arguments and Parameters

We can pass data into methods to make the method act differently or give different output - we call the data we pass *arguments* - we specify these *arguments* in the `()` when we call the method.

When we define a method which needs to accept data we make a space for the data to be recieved - this is essentialy a varaible which will be used by the method - we call these spaces *parameters*

Essentialy we pass data to method *paramaters* as *arguments*.

![13](/images/13.png)

>[!IMPORTANT]
>We need to make sure the *datatype* of an argument matches that specified as the parameter it is being passed to

#### Non Void Methods

If a method *returns* a value we need to specify which datatype will be returned - we do this infront of the name of the method where before we used `void`

```csharp=
int addNums(int x, int y) // returns an int so we specify this
{
    return x + y; // return key word returns an int
}

int smallSum = addNums(2, 8);
int midSum = addNums(23, 82);
int largeSum = addNums(288, 343);

System.Console.WriteLine(smallSum);
System.Console.WriteLine(midSum);
System.Console.WriteLine(largeSum);
```

If we have specified that a method will return a value we must make sure all paths return a value - this is important if we start to use flow control.

```csharp=
int addNums(int x, int y) // returns an int so we specify this
{
    if(x + y >= 100)
    {
        System.Console.WriteLine("Ton Up");
        return x + y; // return key word returns an int
    }
    return x + y; // needed so all paths return an int
}

int smallSum = addNums(2, 8);
int midSum = addNums(23, 82);
int largeSum = addNums(288, 343);

System.Console.WriteLine(smallSum);
System.Console.WriteLine(midSum);
System.Console.WriteLine(largeSum);
```

>[!IMPORTANT]
>We must ensure we return the same datatype as we specify as the return datatype in the method declaration

#### Static Typing vs Dynamic Typing

C# is a *static* typed language - this is why we need to ensure that datatypes match.

In a *static* typed language we cannot assign a datatype to a variable which does not match its original datatype. For example a variable declared `string userAge = "10";` cannot later have any other kind of datatype assigned to it - `userAge = 11;` will not work but `userAge = "11";` will work.

>[!NOTE]
>Dynamically typed languages such as python do allow different datatypes to be assigned to variables - `user_age = "10"` in python can be followed later with `user_age = 11` if wanted

An advantage of using a *static* typed language such as C# is that *type errors* are picked up during compilation so we dont have them during runtime.

A disadvantage of using a *static* typed language such as C# is that it makes it less flexible when programing with it.

#### int.Parse() Method

We can use the `int.Parse()` method to *parse* a *string* datatype into an *integer* datatype - this is useful when working with user supplied input as the `ReadLine()` method always returns a *string* even though we might want an *integer* to work with.

```csharp=
System.Console.WriteLine("Enter your age: ");
string userAge = Console.ReadLine(); // returns a string
int age = int.Parse(userAge); // we parse the string to be an int
int catAge = age * 7; // we can now work with the data mathematically
System.Console.WriteLine("As a cat you are: " + catAge);
```
