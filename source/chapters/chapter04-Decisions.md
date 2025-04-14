# Chapter 4: Decisions

## Relational Operators

Relational operators allow you to compare numeric and character values.

| Relational Operator | Meaning                  |
|---------------------|--------------------------|
| `>`                 | Greater than             |
| `<`                 | Less than                |
| `>=`                | Greater than or equal to |
| `<=`                | Less than or equal to    |
| `==`                | Equal to                 |
| `!=`                | Not equal to             |


Example:

```cpp
x >= y;  // Is x greater than or equal to y?
y != x;  // True if y is not equal to x

```

> Note: All relational operators have left-to-right associativity and return `1` for true and `0` for false. They have higher precedence than assignment.

### Example Program

```cpp
#include <iostream>
using namespace std;

int main() {
    bool V;
    int x = 5, y = 10;
    V = x < y;
    cout << "true is " << V << " false is " << (y == x) << endl;
    return 0;
}

```

## The `if` Statement

The `if` statement conditionally executes code:

```cpp
if (expression) {
    // statements
}

```

> ⚠️ Avoid placing a semicolon right after `if (condition);` — it creates a null statement and skips the intended block.

## Comparing Floating-Point Numbers

Due to rounding errors, avoid using `==` with floating-point values.

```cpp
#include <iostream>
using namespace std;

int main() {
    double a = 1.5, b = 1.5;
    a += 0.0000000000000001;
    if (a == b)
        cout << "Both a and b are same.\n";
    else
        cout << "a and b are not same.\n";
    return 0;
}

```

Use `>` or `<` instead of `==` for reliable comparisons.

## Numbers’ Truth

-   Any **non-zero** value is considered `true`
    
-   `0` is considered `false`
    

Examples:

```cpp
if (value) // Executes if value != 0
if (x + y) // Executes if x + y != 0
if (pow(a, b)) // Executes if pow returns non-zero

```

> ⚠️ Don't confuse `=` with `==`. `=` assigns value, `==` compares.

```cpp
if (x = 2) // Always true because x is assigned 2

```

## Expanding the `if` Statement

To execute multiple lines:

```cpp
if (expression) {
    statement1;
    statement2;
}

```

## `if/else` Statement

Will execute one group of statements if expression is true, or another group of statements if expression is false. 

```cpp
if (expression) {
    // true block
} else {
    // false block
}

```

## Nested `if` Statements

To test more than one condition, if statement can be nested inside another if.

Both if statements have `else`: ↓

```cpp
if (condition1) {
    if (condition2) {
        // Nested block
    } else {
        // Else for inner if
    }
} else {
    // Else for outer if
}

```

> **Programming Style and Nested Decision Structures:** Proper indentation makes complex conditions easier to read.

## `if/else if` Statement

Tests series of conditions. it is often simpler to test series of conditions with if/else if statement than with set of nested if/else statements.

```cpp
if (expression1) {
    // block 1
} else if (expression2) {
    // block 2
} else {
    // fallback block
}

```

last else, which doesn’t have if statement following it, is referred to as over else. it is optional, but in most cases, you will use it.

### Case Study – Grading Program

Dr. teaches literature class and uses following 10-point grading scale for all of his students:
(90 and above A)            (80–89 B)        (70–79 C)           (Below 69 D)


```cpp
#include <iostream>
using namespace std;

int main() {
    const int A_SCORE = 90, B_SCORE = 80, C_SCORE = 70;
    int testScore;
    cout << "Enter your numeric test score: ";
    cin >> testScore;

    if (testScore >= A_SCORE)
        cout << "Your grade is A.\n";
    else if (testScore >= B_SCORE)
        cout << "Your grade is B.\n";
    else if (testScore >= C_SCORE)
        cout << "Your grade is C.\n";
    else if (testScore >= 0)
        cout << "Your grade is D.\n";
    else
        cout << "Invalid test score.\n";

    return 0;
}

```

## Using Trailing else To Catch Errors: 

```cpp
cout << "Your grade is C.\n";
else if (testScore >= 0)
cout << "Your grade is D.\n";
else // if negative score is entered
cout << "Invalid test score.\n";
```

## Logical Operators

Logical operators connect multiple expressions:

| Operator | Meaning | Effect                                           |
|----------|---------|--------------------------------------------------|
| `&&`     | AND     | True only if both expressions are true           |
| `||`     | OR      | True if at least one expression is true          |
| `!`      | NOT     | Reverses the truth of the expression              |


### Examples

```cpp
if (temp < 20 && minutes > 12)
    cout << "Danger zone.";

if (temp < 0 || temp > 100)
    cout << "Out of range.";

if (!(temp > 100))
    cout << "Below max temp.";

```

> ❗ Always write full expressions: `temp > 0 && temp < 100` instead of `temp > 0 && < 100`

### Short-Circuit Evaluation

-   In `&&`, if left is `false`, right is not evaluated.
    
-   In `||`, if left is `true`, right is not evaluated.
    

## Operator Precedence and Associativity

From highest to lowest:

1.  `!`
    
2.  `&&`
    
3.  `||`
    

Use parentheses for clarity:

```cpp
if ((a < b) || ((y == z) && (m > j)))

```

## Checking Numeric Ranges

```cpp
if (x >= 20 && x <= 40)
    cout << x << " is in range.\n";

if (x < 20 || x > 40)
    cout << x << " is out of range.\n";

```

> C++ does **not** allow `5 < x < 20`; use logical operators to connect expressions. instead, you must use logical operator to connect two relational expressions, as previously discussed.


## ASCII Character Comparisons

Characters are compared by their ASCII values:


| Character       | ASCII Value |
|-----------------|-------------|
| `'0' – '9'`     | 48 – 57     |
| `'A' – 'Z'`     | 65 – 90     |
| `'a' – 'z'`     | 97 – 122    |
| `' '` (space)   | 32          |
| `'.'` (dot)     | 46          |


> `'A' < 'B'`, `'1' < '2'`, and `'a' > 'Z'` — because lowercase letters have higher ASCII values.

----------


## Comparing String Objects

When two `string` objects are compared, it is their ASCII character values that are actually being evaluated. For example:

```cpp
string str1 = "ABC";
string str2 = "XYZ";

```

Here, `str1 < str2` would evaluate to `true` because the ASCII values of "ABC" are less than those of "XYZ". Comparison is done character by character.

You can also compare `string` objects with string literals:

```cpp
if (str1 < "XYZ") // true

```

## Conditional Operator

The **conditional operator** (`?:`) is a ternary operator that offers a shorthand for `if/else` logic:

```cpp
expression ? expression : expression;

```

Example:

```cpp
x < 0 ? y = 10 : z = 20;

```

Equivalent to:

```cpp
if (x < 0)
    y = 10;
else
    z = 20;

```

> Use parentheses for readability: `(x < 0) ? (y = 10) : (z = 20);`

### Using the Value of a Conditional Expression

All expressions in C++ return a value. Example:

```cpp
a = x > 100 ? 0 : 1;

```

Equivalent to:

```cpp
if (x > 100)
    a = 0;
else
    a = 1;

```

This makes it useful in compact expressions:

```cpp
cout << "Your grade is: " << (score < 60 ? "Fail." : "Pass.");

```

Without parentheses, only the Boolean result (`true`/`false`) would be sent to `cout`, not the full string.

## `switch` Statement

The `switch` statement evaluates an **integer expression** and executes statements based on its value:

```cpp
switch (Integer Expression) {
    case ConstantExpression:
        // Statements
        break;
    default:
        // Default block
}

```

> Each `case` expression must be unique and must be a constant.

### Example Program

```cpp
#include <iostream>
using namespace std;

int main() {
    char choice;
    cout << "Our pet food is available in three grades:\nA, B. Which do you want pricing for? ";
    cin >> choice;

    switch (choice) {
        case 'a':
        case 'A':
            cout << "You entered A. \n";
            break;
        case 'b':
        case 'B':
            cout << "You entered B. \n";
            break;
        default:
            cout << "Invalid choice. Please enter A or B.\n";
    }
    return 0;
}

```

> Notice that `'a'` and `'A'` share the same block using fall-through behavior.

## Using `switch` in Menu Systems

`switch` is useful for handling user input in menu-based systems.

### Menu Program Example

Menu is screen displaying set of choices user selects from. nested if/else or if/else if create menu-driven programs, that allows user to determine course of action by selecting it from list of actions. switch statement is natural mechanism for building menu systems. 

```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    int choice, months;
    double charges;
    const double ADULT = 40.0, CHILD = 20.0, SENIOR = 30.0;
    const int ADULT_CHOICE = 1, CHILD_CHOICE = 2, SENIOR_CHOICE = 3, QUIT_CHOICE = 4;

    cout << "\tHealth Club Membership Menu\n";
    cout << "1. Standard Adult Membership\n";
    cout << "2. Child Membership\n";
    cout << "3. Senior Citizen Membership\n";
    cout << "4. Quit Program\n";
    cout << "Enter your choice: ";
    cin >> choice;

    cout << fixed << showpoint << setprecision(2);

    switch (choice) {
        case ADULT_CHOICE:
            cout << "For how many months? ";
            cin >> months;
            charges = months * ADULT;
            cout << "Total charges are $" << charges << endl;
            break;
        case CHILD_CHOICE:
            cout << "For how many months? ";
            cin >> months;
            charges = months * CHILD;
            cout << "Total charges are $" << charges << endl;
            break;
        case SENIOR_CHOICE:
            cout << "For how many months? ";
            cin >> months;
            charges = months * SENIOR;
            cout << "Total charges are $" << charges << endl;
            break;
        case QUIT_CHOICE:
            cout << "Program ending.\n";
            break;
        default:
            cout << "Valid choices are 1 through 4. Please run again.\n";
    }
    return 0;
}

```

## Blocks and Variable Scope

Variable Scope is part of program where variable may be used. first rule of scope you should learn is that variable cannot be used in any part of program before definition.

### Example – Invalid Access Before Declaration

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << value; // ❌ ERROR! value not defined yet
    int value = 100;
    return 0;
}

```

### Local Scope

Variables defined inside `{}` are local to that block. Define variables close to where they are used for clarity.

### Same Variable Name in Nested Blocks

Variables in nested blocks can have the same name as outer variables. Inner variables hide the outer ones until the block ends.

```cpp
int number;
cout << "Enter a number greater than 0: ";
cin >> number;

if (number > 0) {
    int number; // Hides outer number
    cout << "Now enter another number: ";
    cin >> number;
    cout << "Second number you entered: " << number << endl;
}

cout << "Your first number was: " << number << endl;

```

As soon as program leaves that block, inner number goes out of scope, revealing outer number variable.

> ⚠️ Avoid reusing variable names in nested scopes to prevent confusion.

----------
