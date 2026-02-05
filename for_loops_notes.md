# C++ Loops Mastery & Interview Prep

## Table of Contents
- [Overview](#overview)
- [Key Concepts](#key-concepts)
  - [Loop Types](#loop-types)
  - [For Loop Header](#for-loop-header)
- [Code Snippets & Explanations](#code-snippets--explanations)
  - [Basic For Loop](#basic-for-loop)
  - [Loop Variable Scope](#loop-variable-scope)
  - [Loop Variable Shadowing](#loop-variable-shadowing)
  - [Iterating Even/Odd Numbers](#iterating-evenodd-numbers)
  - [Multiplication Table](#multiplication-table)
  - [Arithmetic Progression (AP)](#arithmetic-progression-ap)
  - [Geometric Progression (GP)](#geometric-progression-gp)
  - [Factorial Calculation](#factorial-calculation)
  - [Prime Number Check (Naive)](#prime-number-check-naive)
  - [Power Calculation](#power-calculation)
  - [Counting Digits](#counting-digits)
  - [Sum of Digits](#sum-of-digits)
  - [Reverse a Number](#reverse-a-number)
  - [Alternating Series Sum](#alternating-series-sum)
  - [Fibonacci Series](#fibonacci-series)
  - [Character Loop](#character-loop)
  - [Using `continue` in loops](#using-continue-in-loops)
  - [Break vs Continue](#break-vs-continue)
  - [Compound Assignment in While](#compound-assignment-in-while)
- [Best Practices](#best-practices)
- [Common Mistakes](#common-mistakes)
- [Interview Prep Questions & Answers](#interview-prep-questions--answers)
- [Quick Reference](#quick-reference)

---

## Overview
This comprehensive guide delves into C++ loops (`for`, `while`, `do-while`), offering detailed explanations, code examples, best practices, and a full set of interview-style questions and answers sourced from `loops.cpp`. Master control flow and iterative algorithms for robust C++ programming.

## Key Concepts

### Loop Types
**Q1: What are the three main loop types in C++ and when to use each?**
**A1**:
*   **`for` loop**: Best for situations where the number of iterations is known or can be determined before the loop begins. It combines initialization, condition checking, and iteration update into a single line.
*   **`while` loop**: Suitable when the number of iterations is unknown, and the loop continues as long as a specified condition remains true. The condition is checked *before* each iteration.
*   **`do-while` loop**: Similar to `while`, but guarantees that the loop body executes at least once, as the condition is checked *after* the first iteration.

### For Loop Header
**Q2: What are the parts of a `for` header?**
**A2**: The `for` loop header consists of three optional expressions, separated by semicolons:
1.  **Initialization**: Executed once at the very beginning of the loop. Typically used to declare and initialize a loop control variable (e.g., `int i = 0;`).
2.  **Condition**: Evaluated before each iteration. If true, the loop body executes; if false, the loop terminates.
3.  **Update**: Executed after each iteration of the loop body. Typically used to modify the loop control variable (e.g., `i++`, `i -= 2`).
    Example: `for(int i = 0; i < n; i++) { /*body*/ }`

---

## Code Snippets & Explanations

### Basic For Loop
Demonstrates printing "Good morning" 10 times, contrasting repetitive code with an efficient loop.
```cpp
// Inefficient repetition:
// cout<<"Good morning"<<endl; // ... repeated 10 times ...

// Efficient with for loop:
#include<iostream>
using namespace std;
int main(){
    for (int i = 0; i<10;i++){
        cout<<"Good morning"<<endl;
    }
    return 0;
}
```
**Explanation**: Loops drastically reduce code repetition, making it more concise and maintainable, especially for many iterations.

### Loop Variable Scope
Illustrates that a variable declared within the `for` loop header is local to that loop and not accessible outside.
```cpp
// [Q-Scope] Example: loop variable declared inside header — not visible outside.
#include<iostream>
using namespace std;
int main(){
    int n;
    cout<<"enter no. n: ";
    cin>>n;
    for (int i = 1; i<=n;i++){
        cout<<"Hello World"<<endl;
    }
    // cout<<i; // This line would cause a compile-time error: 'i' was not declared in this scope
    return 0; // Added return 0 for proper main function
}
```
**Explanation**: `i` is scoped only within the `for` loop. To use it outside, declare it before the loop.

### Loop Variable Shadowing
Shows how declaring a variable with the same name outside and inside a loop can lead to confusion or unintended behavior (shadowing).
```cpp
// [Q-Scope] Example: inner `i` shadows outer `i` — initialize outer `i` to avoid garbage.
#include<iostream>
using namespace std;
int main(){
    int n;
    cout<<"enter no. n: ";
    cin>>n;
    int i_outer; // Declared outside, but not initialized
    for (int  i = 1; i<=n;i++){ // This 'i' shadows i_outer
        cout<<"Hello World"<<endl;
    }
    // cout<<i_outer; // Prints garbage or 0 if globally initialized.
    // If you want to use the same variable:
    // int i;
    // for (i = 1; i<=n;i++){ ... }
    // cout<<i; // This would print the last value of i (n+1)
    return 0;
}
```
**Explanation**: When a variable is declared inside a loop with the same name as one outside, the inner one takes precedence within the loop's scope. To use the *same* variable throughout, declare it once outside and just use its name in the `for` loop's initialization (e.g., `for (i = 1; ...)`).

### Iterating Even/Odd Numbers
Examples of printing numbers, specifically even numbers, and checking parity within a loop.
```cpp
// Print 1 to 100
// int main(){
//     for (int i = 1; i<=100; i++){
//         cout<<i<<endl;
//     }
// }

// Print even numbers from 2 to 100
#include<iostream>
using namespace std;
int main(){
    int i;
    for (i=2;i<=100;i+=2){
        cout<<i<<endl;
    }
    return 0;
}

// Check and print even/odd for 1 to 100
// int main(){
//     int n; // n is unused here, original code had it but it's not needed for this example
//     int i;
//     for(i=1;i<=100;i++){
//         if(i%2==0){
//             cout<<i<<" even no."<<endl;
//         }
//         else{
//             cout<<i<<" odd no."<<endl;
//         }
//     }
//     return 0;
// }
```
**Explanation**: Loops can iterate with different step values (`i+=2`) and incorporate conditional logic (`if-else`) to process numbers based on criteria.

### Multiplication Table
Generating a multiplication table for a given number `n`.
```cpp
#include<iostream>
using namespace std;
int main(){
    int n;
    cout<<"Enter no. n: ";
    cin>>n;
    int i;
    for (i=1;i<=10;i++){ // Changed loop to go up to 10 for standard multiplication table
        cout<<n<<" * "<<i <<" = "<<n*i<<endl;
    }
    return 0;
}
```
**Explanation**: A `for` loop is ideal for generating sequences like multiplication tables where the number of iterations is fixed.

### Arithmetic Progression (AP)
Generating terms of an Arithmetic Progression.
```cpp
// Print AP 4, 7, 10, 13, 16 ...... upto n terms
#include<iostream>
using namespace std;
int main(){
    int n;
    cin>>n;
    int a = 4; // Starting term
    int common_diff = 3; // Common difference
    for (int i = 0; i<n; i++){
        cout<<a<<endl;
        a = a + common_diff;
    }
    return 0;
}

// Display this AP - 100, 97, 94.... upto all terms which are positive
// int main(){
//     for(int i = 100;i>0;i-=3){ // Loop continues as long as i is positive
//         cout<<i<<endl;
//     }
//     return 0;
// }
```
**Explanation**: APs can be generated by repeatedly adding a common difference within a loop. The loop condition must handle positive/negative steps correctly.

### Geometric Progression (GP)
Generating terms of a Geometric Progression.
```cpp
// Print GP upto nth term: 1, 2, 4, 8, 16, 32...........
#include<iostream>
using namespace std;
int main ();
{
    int n;
    cin>>n;
    int a = 1; // Starting term
    int ratio = 2; // Common ratio
    for(int i = 0;i<n;i++){
        cout<<a<<endl;
        a=a*ratio;
    }
    return 0;
}

// Print GP: 2, 6, 18, 54......
// int main(){
//     int n;
//     int a = 2;
//     cin>>n;
//     for(int i = 0;i<n;i++){
//         cout<<a<<endl;
//         a = a*3;
//     }
//     return 0;
// }
```
**Explanation**: GPs are generated by repeatedly multiplying by a common ratio.

### Factorial Calculation
Calculating the factorial of a number iteratively.
```cpp
// [Q-Factorial] Use `long long` for larger `n` or check overflow before multiplying.
#include<iostream>
using namespace std;
int main(){
    int n,i;
    long long fact=1; // Use long long to prevent overflow for larger factorials
    cout<<"Enter the no.: ";
    cin>>n;
    for( i=1 ; i<=n;i++){
        fact=fact*i;
    }
    cout<<fact;
    return 0;
}
```
**Explanation**: Iterative multiplication inside a loop is used. Important to consider data types (`long long`) to handle potential overflow for larger `n`.

### Prime Number Check (Naive)
A basic method to check if a number is prime by trial division.
```cpp
// [Q-Prime] Naive check up to n-1 shown. Optimize by checking up to sqrt(n) and skipping even divisors.
#include<iostream>
using namespace std;
int main(){
    int n;
    cin>>n;
    bool isprime = true;
    if (n <= 1) { // 0 and 1 are not prime numbers
        isprime = false;
    } else {
        for (int i =2;i<n;i++){
            if(n%i==0){
                isprime=false;
                break; // Exit loop early if a divisor is found
            }
        }
    }
    
    if(isprime){
        cout<<n<<" is a prime no.";
    }
    else{
        cout<<n<<" is a composite no.";
    }
    return 0;
}
```
**Explanation**: A `for` loop iterates from 2 up to `n-1`. If any number divides `n` evenly, it's not prime. Optimization (checking up to `sqrt(n)`) is noted.

### Power Calculation
Calculating `base` raised to the power of `power` (handling positive and negative exponents).
```cpp
// [Q-Power] Handle `0^0`, negative exponents, and prefer `double` when inverting. Consider fast exponentiation.
#include<iostream>
using namespace std;
int main(){
    double after_calc=1; // Use double for potential fractional results
    int power;
    cout<<"Enter the power: ";
    cin>>power;
    int base;
    cout<<"enter the base: ";
    cin>>base;
    bool is_negative_power = false;
    
    if(base == 0 && power == 0){
        cout<<"not defined";
        return 0;
    }
    
    if (power < 0){
        is_negative_power = true;
        power = -power; // Work with positive power for calculation
    }

    for (int i = 1; i <= power; i++){
        after_calc = base * after_calc;
    }

    if(is_negative_power){
        after_calc = (1.0 / after_calc); // Invert for negative exponent
    }
    cout<<after_calc;
    return 0;
}
```
**Explanation**: Uses a loop for repeated multiplication. Special handling for `0^0` and negative exponents (by inverting the result).

### Counting Digits
Counts the number of digits in an integer.
```cpp
// [Q-Digits] Edge-case: `n==0` must give count 1. For negatives, take absolute or handle sign.
#include<iostream>
using namespace std;
int main(){
    int count=0;
    int n;
    cin>>n;
    if (n == 0) {
        cout << 1;
        return 0;
    }
    int temp_n = n; // Use a temporary variable to preserve original n
    if (temp_n < 0) temp_n = -temp_n; // Handle negative numbers

    while(temp_n > 0){
        count+=1;
        temp_n=temp_n/10;
    }
    cout<<count;
    return 0;
}
```
**Explanation**: Repeatedly divides the number by 10 until it becomes 0, incrementing a counter. Special handling for `n=0` and negative numbers is crucial.

### Sum of Digits
Calculates the sum of the digits of an integer.
```cpp
// [Q-SumDigits] Use `%` and `/` repeatedly; watch `n==0` case and negatives.
#include<iostream>
using namespace std;
int main(){
    int sum =0;
    int n,last_digit;
    cin>>n;
    if(n==0){
        cout<<0;
        return 0;
    }
    int temp_n = n;
    if (temp_n < 0) temp_n = -temp_n; // Handle negative numbers

    while(temp_n > 0){
        last_digit = temp_n % 10;
        sum = last_digit + sum;
        temp_n /= 10;
    }
    cout<<sum;
    return 0;
}
```
**Explanation**: Uses the modulo operator (`%`) to get the last digit and integer division (`/`) to remove it, accumulating the sum in a `while` loop.

### Reverse a Number
Reverses the digits of an integer.
```cpp
// [Q-Reverse] Reverse by `rev = rev*10 + last`; watch overflow and negative numbers.
#include<iostream>
using namespace std;
int main(){
    int n,lastdigit,reversedigit = 0;
    cin>>n;
    if(n==0){
        cout<<0;
        return 0;
    }
    int sign = 1;
    if (n < 0) {
        sign = -1;
        n = -n; // Work with positive number for reversal
    }

    while(n > 0){
        lastdigit= n % 10;
        // Check for overflow before multiplying
        if (reversedigit > (2147483647 / 10) || (reversedigit == (2147483647 / 10) && lastdigit > 7)) {
            cout << "Overflow detected!" << endl;
            return 1; // Indicate error
        }
        reversedigit = lastdigit + reversedigit * 10;
        n = n / 10;
    }
    cout<<reversedigit * sign;
    return 0;
}
```
**Explanation**: Builds the reversed number by repeatedly taking the last digit, adding it to `reversedigit * 10`. Important to handle negatives and potential integer overflow.

### Alternating Series Sum
Calculates the sum of an alternating series (e.g., 1 - 2 + 3 - 4...).
```cpp
// [Q-Alternating] Alternating series can be calculated by sign or formula.
#include<iostream>
using namespace std;
int main(){
    int i,n,sum=0;
    cin>>n;
    for (i=1;i<=n;i++){
        if (i%2==0){
            sum += (-i); // Subtract even numbers
        }
        else{
            sum = sum+i; // Add odd numbers
        }
    }
    cout<<sum;
    return 0;
}

// Optimized solution for alternating series sum:
// int main(){
//     int n , sum=0;
//     cin>>n;
//     if(n%2==0) sum = -(n/2);
//     else sum = (-(n/2))+n;
//     cout<<sum;
//     return 0;
// }
```
**Explanation**: Uses conditional logic (`if-else`) inside a loop to alternate between adding and subtracting terms. An optimized mathematical solution is also noted.

### Fibonacci Series
Generates the Fibonacci sequence iteratively.
```cpp
// [Q-Fibonacci2] Iterative Fibonacci printing; consider whether `n` is count of additional terms.
#include<iostream>
using namespace std;
int main(){
    int a = 0, b = 1, n, sum = 0;
    cin>>n;
    if (n >= 1) cout<<a<<" ";
    if (n >= 2) cout<<b<<" ";
    for (int i = 3; i <= n; i++){ // Start from 3rd term
        sum = a + b;
        a = b;
        b = sum;
        cout<<sum<<" ";
    }
    cout << endl; // New line after series
    return 0;
}
```
**Explanation**: Uses three variables (`a`, `b`, `sum`) to iteratively calculate and print terms. Careful handling of initial terms and `n` value for output.

### Character Loop
Iterating through character values and their ASCII representations.
```cpp
// [Q-CharLoop] Iterating char values prints characters and their ASCII codes.
#include<iostream>
using namespace std;
int main(){
    for(char i = 'A';i<='Z';i++){
        cout<<i<<" "<<static_cast<int>(i)<<endl; // Use static_cast for clarity
    }
    return 0;
}
```
**Explanation**: A `for` loop can iterate through character ranges, and `static_cast<int>(i)` reveals their ASCII values.

### Using `continue` in loops
Demonstrates how `continue` skips the rest of the current loop iteration.
```cpp
// wap to print odd no. from 1 to 100
#include<iostream>
using namespace std;
int main(){
    for(int i = 1; i<=100;i++){
        if(i%2==0) continue; // If 'i' is even, skip to next iteration
        cout<<i<<endl;
    }
    return 0;
}
```
**Explanation**: `continue` is useful for skipping processing for certain conditions and moving directly to the next iteration of the loop (including the update step for `for` loops).

### Break vs Continue
An example demonstrating the difference between `break` and `continue` in altering loop flow.
```cpp
// int main(){
// [Q-LoopControl] `continue` moves control to top — be mindful of variable updates and infinite loop risks.
//     int x = 4,y=0,z; // 'z' is unused
//     while(x>=0){
//         x--;
//         y++;
//         if(x==y){
//             continue; // Skips printing and goes to next while iteration
//         }
//         else{
//             cout<<x<<" "<<y<<endl;
//         }
//     }
//     return 0;
// }

// Example using break
#include<iostream>
using namespace std;
int main(){
    int x = 4,y=0;
    while(x>=0){
        if(x==y){
            break; // Exits the loop completely
        }
        else{
            cout<<x<<" "<<y<<endl;
            x--;
            y++;
        }
    }
    return 0;
}
```
**Explanation**: `continue` skips the remainder of the current loop iteration and proceeds to the next. `break` immediately terminates the entire loop.

### Compound Assignment in While
Demonstrates how compound assignment operators (like `/=`) within a `while` condition can affect loop execution.
```cpp
// [Q-CompoundAssign] `while(t/=2)` both assigns and tests — understand value after assignment; may produce unexpected iterations.
#include<iostream>
using namespace std;
int main(){
    int t = 10;
    while(t/=2){ // t is updated (t = t / 2) AND then tested (if t is non-zero)
        cout<<"Hello"<<endl;
    }
    return 0;
}
```
**Explanation**: The expression `t/=2` first performs the division `t = t / 2` and then uses the *new* value of `t` as the condition for the `while` loop. The loop continues as long as `t` is non-zero.

---

## Best Practices
*   **Clear Initialization & Conditions**: Ensure loop variables are correctly initialized and termination conditions are precise to avoid infinite loops or off-by-one errors.
*   **Appropriate Loop Type**: Choose `for`, `while`, or `do-while` based on whether the iterations are fixed, condition-driven (pre-check), or guaranteed-once (post-check).
*   **Variable Scope**: Declare loop control variables in the narrowest possible scope (e.g., within the `for` loop header) unless they are needed outside the loop.
*   **Handle Edge Cases**: Always test loops with boundary values (e.g., `n=0`, `n=1`), negative inputs, and large inputs to check for overflow.
*   **Readability**: Use clear variable names and proper indentation. Comment complex loop logic or tricky conditions.
*   **Efficiency**: Consider the time complexity of nested loops. For very large inputs, look for more efficient algorithms (e.g., `sqrt(n)` for primality, exponentiation by squaring for powers).
*   **Avoid Assignment in Conditions**: Prefer `==` for comparison in loop conditions. Using `=` (assignment) often leads to subtle bugs, especially in `while` loops.

## Common Mistakes
*   **Infinite Loops**:
    *   Forgetting to update the loop control variable.
    *   Incorrect loop condition that always evaluates to true.
    *   Using assignment (`=`) instead of comparison (`==`) in the loop condition (`while(i=10)` instead of `while(i==10)`).
*   **Off-by-one Errors**:
    *   Incorrectly using `<` versus `<=` (or `>` versus `>=`) in loop conditions.
    *   Wrong starting or ending values for loop variables.
    *   Not accounting for zero-based vs. one-based indexing.
*   **Scope Issues**: Attempting to access a loop variable outside its declared scope.
*   **Integer Overflow**: Not using appropriate data types (`long long`, `double`) for calculations that might exceed the capacity of `int`, especially in factorials, powers, or large sums.
*   **Inefficient Primality Check**: Forgetting to optimize prime checks beyond `n/2` or `sqrt(n)`.
*   **Ignoring Edge Cases**: Not explicitly handling inputs like `n=0`, negative numbers, or specific problem constraints (e.g., `0^0` in power calculation).

---

## Interview Prep Questions & Answers

**Q1: What are the three main loop types in C++ and when to use each?**
**A1**: `for` for counted/repeatable iterations; `while` when condition-first; `do-while` when you need body to run at least once. Choose by control flow needs.

**Q2: What are the parts of a `for` header?**
**A2**: Initialization, condition, update. Example: `for(int i=0;i<n;i++) { /*body*/ }`. Key concepts: init executes once, condition checked each iteration, update runs after body; all three optional.

**Q3: Why does `cout<<i;` after `for(int i=0; i<n; i++)` give an error?**
**A3**: `i` was declared inside the `for` scope; it's not visible outside. Declare `int i;` before the loop if you need it after. Key concepts: variable scope, lifetime, shadowing, declaration location matters.

**Q4: How do `break`, `continue`, and `return` behave inside loops?**
**A4**: `break` exits the nearest loop; `continue` skips to the next iteration (then does the loop update); `return` exits the function. Key concepts: control-flow modifiers, nearest-loop effect, update step behavior in `for` when `continue` used.

**Q5: Common causes of infinite loops and an example of a subtle bug.**
**A5**: Not updating loop variable, wrong condition, assignment instead of comparison (e.g., `while(i=10)`), wrong step direction. Key concepts: loop invariants, termination condition, debugging by printing variables, careful use of `=` vs `==`.

**Q6: How to count digits, sum digits, and reverse a number using loops?**
**A6**: Repeatedly use `last = n % 10; n = n / 10;` accumulate `count`, `sum += last`, and `rev = rev*10 + last`. Edge-case: `n == 0` should return count 1; handle negatives and overflow for `rev`. Key concepts: modulus/division loop pattern, initial-edge handling (`n==0`), sign/overflow considerations.

**Q7: How to check primality using a loop and how to optimize it?**
**A7**: Trial divide from 2 to `n-1` (simple). Optimize to check 2, then odd divisors up to `sqrt(n)` and stop early on first divisor. Key concepts: trial division, complexity O(n) naive vs O(sqrt(n)) optimized, skip even numbers, early exit.

**Q8: How to compute factorial iteratively and what to watch for?**
**A8**: Multiply `fact *= i` in a loop 1..n. Use `long long` or big-int and watch overflow for moderate `n` (20+ for 64-bit). Key concepts: iterative accumulation, overflow limits, types (`int` vs `long long`), iterative vs recursive tradeoffs.

**Q9: How to compute integer power with positive and negative exponents?**
**A9**: Repeated multiplication for positive exponent. For negative exponent, compute positive power then invert: `result = 1.0 / power;` handle `0^0` as undefined. Key concepts: repeated multiplication, negative exponent inversion (use floating), `0^0` special-case, consider fast exponentiation.

**Q10: Fibonacci iterative pattern (space O(1)).**
**A10**: Keep two vars `a=0, b=1`; loop: `sum = a + b; a = b; b = sum;` print `a` or `b` as needed. Watch off-by-one for Nth term. Key concepts: constant space iterative update, order of updates, seed values, off-by-one tests for sequence indexing.

**Q11: AP / GP generation using loops.**
**A11**: AP: start `a`, do `a += diff` each iteration. GP: start `a`, do `a *= ratio` each iteration. Key concepts: arithmetic vs geometric progression formulas, loop update patterns, stopping conditions for positive/negative ratios.

**Q12: Using `continue` to skip iterations.**
**A12**: Example: print only odd numbers: `for(i=1;i<=100;i++){ if(i%2==0) continue; cout<<i; }`. Key concepts: `continue` skips rest of body, still performs `for` update; use to simplify conditional bodies.

**Q13: Off-by-one errors — how to avoid them.**
**A13**: Decide inclusive/exclusive boundaries (`<=` vs `<`), test with small `n` (0,1,2), and trace the loop variables for edges. Key concepts: boundary selection, test cases, loop invariants, example-driven tracing.

**Q14: Time complexity of loops.**
**A14**: Single loop O(n). Nested loops multiply complexities (two nested loops with `n` iterations each => O(n^2)). Be explicit about loop bounds. Key concepts: Big-O, nested iteration multiplication, impact of early `break` on average vs worst-case.

**Q15: Detecting and handling edge cases in loops.**
**A15**: Check `n==0`, negative inputs, `0^0`, divisions by zero, and integer overflow; prefer typed variables (`long long`, `double`) when appropriate. Key concepts: guard conditions, input validation, use of appropriate data types, defensive programming.

**Q16: Practical coding tasks to practice loops (implement these in this file):**
**A16**: These are practical tasks for self-practice: count digits, sum digits, reverse number; print multiplication table; factorial and detect overflow; iterative & series Fibonacci; AP and GP generators; prime check (naive and sqrt-optimized); power with negative exponent handling. Key concepts: cover digit ops, sequence generation, complexity vs correctness, edge-case handling.

**Q17: Advanced thinking — when should you replace a loop with a more efficient algorithm?**
**A17**: When repeated work can be avoided (use sieve instead of checking each number for primality), or use exponentiation by squaring for fast powers. Key concepts: algorithm selection, precomputation (sieve), divide-and-conquer for power, tradeoffs memory vs time.

**Q18: Debugging checklist for loop bugs**
**A18**: Print loop variables, check initialization, condition, update steps; test boundary values and small cases; ensure variables are initialized. Key concepts: systematic debugging, assertions/logging, small test cases, invariant checks.

**Q19: Interview question formulation tips**
**A19**: State assumptions, mention complexity, handle edge cases, and then implement—prefer clarity over cleverness. Key concepts: communication, problem decomposition, complexity analysis, edge-case discussion.

**Q20: Quick recall checklist (read before an interview)**
**A20**: Know loop types, scope rules, `break/continue`, common off-by-one traps, digit ops pattern, prime sqrt trick, and integer overflow concerns. Key concepts: quick mental checklist — scope, control flow, edge cases, algorithmic optimizations, numeric limits.

---

## Quick Reference
-   **`for (init; condition; update)`**: Counted iterations.
-   **`while (condition)`**: Condition-first iterations.
-   **`do { ... } while (condition)`**: At least one iteration guaranteed.
-   **`break`**: Exits loop immediately.
-   **`continue`**: Skips current iteration, proceeds to next.
-   **Scope**: Variables declared in loop header/body are local to the loop.
-   **`n % 10`, `n / 10`**: Common pattern for digit manipulation.
-   **`long long`**: Use for large numeric results (e.g., factorial) to avoid overflow.
-   **Primality Optimization**: Check up to `sqrt(n)`.
-   **Off-by-one**: Carefully check `<` vs `<=`.

---

**Master these loop patterns and interview concepts to excel in C++ programming!**
