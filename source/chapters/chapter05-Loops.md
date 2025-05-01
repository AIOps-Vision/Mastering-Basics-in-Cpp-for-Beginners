# Chapter 5: Loops
A loop is a control structure that causes a statement or group of statements to repeat. C++ provides three looping control structures: `while`, `do-while`, and `for`. The difference between them lies in how they control repetition.

## `while` Loop
A `while` loop is a *pretest* loop, meaning it tests its expression before each iteration.

**Syntax:**
```cpp
while (expression)
    statement;
```

- If the expression (loop header) is true, the statement (loop body) is executed.
- Then the expression is tested again.
- If true, the statement executes again. This cycle repeats until the expression is false.
- Each repetition of the loop is known as an *iteration*.

**With a block of statements:**
```cpp
while (expression) {
    statement;
    statement;
    // Place as many statements here as necessary.
}
```

## Infinite Loops
Loops must contain a way to terminate. Something inside the loop must eventually make the test expression false.

```cpp
int number = 0;
while (number < 5) {
    cout << "Hello\n";
}
```

Placing a semicolon after the loop header causes the loop to become infinite:
```cpp
while (number < 5); // Infinite loop
```
The semicolon is interpreted as a null statement, and the block after it is disconnected.

**Tips:**
- Don't forget to use braces `{}` with block statements.
- The loop only executes the statement that immediately follows it.
- Don't use `=` when you mean to use `==`. Using `=` causes an assignment, not a comparison, which may create an infinite loop.
- Remember: any nonzero value in C++ is treated as `true`.

## Using `while` Loop for Input Validation
You can use a loop to re-prompt the user until a valid value is entered.

```cpp
cout << "Enter a number in the range 1-100: ";
cin >> number;
while (number < 1 || number > 100) {
    cout << "ERROR: Enter a value in the range 1-100: ";
    cin >> number;
}
```

The read operation before the loop is called a *priming read*.

**Counter:**
A counter is a variable that is regularly incremented or decremented each time the loop iterates.

```cpp
int MIN = 6, MAX = 15, num = MIN; // Counter
while (num <= MAX) {
    cout << num << endl;
    num++; // Increment counter
}
return 0;
```

## `do-while` Loop
A `do-while` loop is a *posttest* loop, meaning its expression is tested **after** each iteration. It must be terminated with a semicolon.

**Syntax:**
```cpp
do {
    statement;
} while (expression);
```

This loop always performs at least one iteration.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int score1, score2, score3;
    double average;
    char again;

    do {
        cout << "Enter 3 scores and I will average them: ";
        cin >> score1 >> score2 >> score3;
        average = (score1 + score2 + score3) / 3.0;
        cout << "Average is " << average << ".\n";
        cout << "Do you want to average another set? (Y/N) ";
        cin >> again;
    } while (again == 'Y' || again == 'y');

    return 0;
}
```

This is known as a **user-controlled loop** because the user decides the number of iterations.

## Using `do-while` with Menus
A `do-while` loop can be used to repeat a menu until the user chooses to exit.

## `for` Loop
There are two types of loops: **conditional loops** and **count-controlled loops**.
- A conditional loop runs based on a condition.
- A count-controlled loop runs a known number of times. The `for` loop is designed for this purpose.

**Syntax:**
```cpp
for (initialization; test; update) {
    statement;
    // Place as many statements here as necessary.
}
```

### Example:
```cpp
for (int count = 0; count < 5; count++)
    cout << "Hello" << endl;
```

- Initialization: `count = 0`
- Test: `count < 5`
- Update: `count++`

Use the counter variable within the loop body.

### Using `for` Instead of `while` or `do-while`
Use a `for` loop when the number of iterations is known and requires clear initialization.

### Avoid Modifying the Counter in the Loop Body
Counter modifications should be in the update expression only. Modifying it in the loop body may cause unexpected behavior:
```cpp
for (int x = 1; x <= 10; x++) {
    cout << x << endl;
    x++; // Wrong: increments x twice per iteration
}
```

### Other Forms of Update Expression
Display all even numbers from 2 to 100:
```cpp
for (int num = 2; num <= 100; num += 2)
    cout << num << endl;
```

Count backward from 10 to 0:
```cpp
for (int num = 10; num >= 0; num--)
    cout << num << endl;
```

### Defining Variable in `for` Initialization
You can define a variable in the initialization expression. Its scope is limited to the loop.
```cpp
for (int num = MIN_NUMBER; num <= MAX_NUMBER; num++)
    cout << num << "\t\t" << (num * num) << endl;
```

Trying to access the variable outside the loop will cause an error:
```cpp
for (int count = 1; count <= 10; count++)
    cout << count << endl;
cout << "Count is now " << count << endl; // ERROR
```

### Creating a User-Controlled `for` Loop
```cpp
for (int value = 914, i = 0; value <= 922; value++, i++)
    array[i] = value;
```

In the `for` loop, use `&&` or `||` in the test expression. Do not use commas in the test expression:
```cpp
for (int x = 1, y = 10; x <= y; x++, y--)
    cout << x << " + " << y << " = " << (x + y) << endl;
```

### Omitting `for` Loop Expressions
You can omit the initialization or update expressions if done externally:
```cpp
int num = 1;
for (; num <= maxValue;) {
    cout << num << "\t\t" << (num * num) << endl;
    num++;
}
```

Simulate a digital clock (seconds):
```cpp
for (int seconds = 0; seconds < 60; seconds++) {
    cout.fill('0');
    cout << right << setw(2) << seconds << endl;
}
```

### Nested Loop
A loop inside another loop. The inner loop completes faster than the outer one.

## Case Study:

### Case study 1: program to sum odd numbers from 0 to 100
```cpp
int i, x=0;
for (i = 1; i < 100; i++) {
    if ((i % 2) != 0)
        x += i;
}
cout << "sum odd =" << x;
```

### Case study 2: program print factorial of number that you enter.
```cpp
int x, y=1;
cout << "enter number to get it's factorial";
cin >> x;
for (int i = 1; i <= x; i++)
    y *= i;
cout << "factorial=" << y;
```

### Case study 3: program to print this shape
```
(0,0) (0,1) (0,2) (0,3) (0,4)
(1,0) (1,1) (1,2) (1,3) (1,4)
(2,0) (2,1) (2,2) (2,3) (2,4)
(3,0) (3,1) (3,2) (3,3) (3,4)
(4,0) (4,1) (4,2) (4,3) (4,4)
```
```cpp
for (int i=0; i<=4; i++) {
    for (int j=0; j<=4; j++)
        cout << "(" << i << "," << j << ")" << "\t";
    cout << "\n";
}
```

### Case study 4: program print 1234567654321
```cpp
int i, j;
for (i = 1; i < 7; i++) // last saved value for I without printing is 7.
    cout << i;
for (j = i; j > 0; j--)
    cout << j;
```

### Case study 5: program check if number is prime, two factors: 1 and themselves as: 2, 3, 5, 7, 11.
```cpp
int i, x, y = 0;
cin >> x;
for (i = 2; i < x; i++) {
    if (x % i == 0)
        y = 1;
}
if (y == 1)
    cout << "number is no prime";
else
    cout << "number is prime";
```

### Case study 6: program of multiplication table of numbers to 10.
```cpp
int i, j;
for (i = 1; i <= 10; i++) {
    cout << "multiply table for (" << i << ").\n-----------------------\n";
    for (j = 1; j <= 10; j++)
        cout << j << " *" << i << " =" << i * j << "\n";
}
```

## `goto` loop:
### Force program to transfer to specific position in program (loop function):
```cpp
int main () {
    // statement 1;
    if (condition)
        goto npoint;
    // statement 3;
npoint:
    // statement 5;
}
```

### Program count from 0 to 4
```cpp
int main () {
    int y = 0;
x:
    cout << y << "\t";
    y += 1;
    if (y <= 4)
        goto x;
    else
        cout << "number is great than 4\n";
    return 0;
}
```

## Keeping Running Total:
Running total is sum of numbers that accumulates with each iteration of loop. accumulator is variable that is used to accumulate total of numbers:
```cpp
for (int count = 1; count <= days; count++) {
    double sales, sum = 0;
    cout << "Enter sales for day " << count << ": ";
    cin >> sales;
    sum += sales; // Accumulate running total.
}
```

## Case Study:
### Case study 1: program to calculate factorial of positive number only
```cpp
int number, factorial = 1;
cout << "enter positive number \n";
cin >> number;
if (number < 0)
    cout << "enter positive number only\n";
else {
    for (int i = 1; i <= number; i++)
        factorial = factorial * i;
    cout << "factorial=\n" << factorial << "\n";
}
```

### Case study 2: print these stars
```cpp
*
**
***
****
*****
```
```cpp
for (int i = 0; i < 5; i++) {
    for (int x = 0; x < i+1; x++) // for every new for loop x starts from 1.
        cout << "*";
    cout << endl;
}
```

### Case study 3: print these stars
```
    *
   ***
  *****
 *******
*********
```
```cpp
for (int i = 0; i < 5; i++) {
    for (int x = 4; x > i; x--)
        cout << " ";
    for (int z = 1; z <= 2 * i + 1; z++) // (2i+1) is wrong.
        cout << "*";
    cout << endl;
}
```

## Sentinel:
Special value that marks end of list of values. when user enters sentinel, loop terminates. program calculates total number of points. user enters a series of values, then −1 when finished:
```cpp
#include <iostream>
using namespace std;

int main() {
    int game = 1, points, total = 0;
    cout << "points your team earned\nthen enter −1 when finished.\nEnter game points " << game << ": ";
    cin >> points;
    while (points != -1) { // program performs priming read to check if there's a sentinel value (-1); it isn’t included in total.
        total += points;
        game++;
        cout << "Enter points for game " << game << ": ";
        cin >> points;
    }
    cout << "\ntotal points are " << total << endl;
    return 0;
}
```

## Breaking and Continuing Loop:
`break;` statement causes its loop to terminate early. `continue;` statement causes loop to stop its current iteration and begin next one. (break and continue must be used with loop).

### Program to enter password and continue asking until user enters valid one:
```cpp
int password;
for (;;) {
    cout << "enter password\n";
    cin >> password;
    if (password == 1234) {
        cout << "password is correct";
        break; // means don’t complete loop.
    } else {
        cout << "password is error try again\n";
    }
}
```

Note: `exit(0);` means don't complete entire program.

### Using break in Nested Loop:
In nested loop, `break` statement only interrupts the loop it's placed in.
```cpp
for (int row = 0; row < 5; row++) {
    for (int star = 0; star < 20; star++) {
        cout << '*';
        if (star == 10)
            break;
    }
    cout << endl;
}
```

### Program counts from 1 to 200, skips 75:
```cpp
int i;
for (i = 1; i <= 200; i++) {
    if (i == 75)
        continue;
    cout << i << "\t";
}
cout << "\nfinished printing to 200 except 75 is not printed";
```

## Final Case Study:
Write program to calculate cost for DVD rentals, where current DVD costs $2 and all others cost $1. If customer rents several DVDs, every third one is free:
```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    int DVDnumber, CurrentRelease = 2, OtherRelease = 1;
    double total = 0.0;
    char release;

    cout << "My Dear Customer:\nHow many DVD you want to hire?\n";
    cin >> DVDnumber;

    while (DVDnumber <= 0 || isdigit(DVDnumber)) {
        cout << "Please! enter number of DVD to be hired\n";
        cin >> DVDnumber;
    }

    for (int i = 1; i <= DVDnumber; i++) {
        if (i % 3 == 0) {
            cout << "DVD number: " << i << " is free for you my dear customer.\n\n";
            continue;
        }

        cout << "Now tell me about release for each DVD you rent.\n";
        cout << "Is DVD number: " << i << " current release?\nEnter y or n\n";
        cin >> release;

        if (release == 'y' || release == 'Y')
            total += CurrentRelease;
        else if (release == 'n' || release == 'N')
            total += OtherRelease;
        else
            cout << "Please! enter o or c to check total price.\n";
    }

    cout << "Total price of hired DVD is:\n" << fixed << showpoint << setprecision(2) << total << "$" << endl;
    return 0;
}
