# C++ If-Else Mastery & Interview Prep

## Table of Contents
- [Overview](#overview)
- [Key Concepts](#key-concepts)
- [Code Snippets & Explanations](#code-snippets--explanations)
- [Best Practices](#best-practices)
- [Common Mistakes](#common-mistakes)
- [Interview Prep Questions](#interview-prep-questions)
- [Quick Reference](#quick-reference)

---

## Overview
This guide covers essential if-else logic in C++, including practical examples, explanations, and interview questions. Use it to master control flow and ace technical interviews.

## Key Concepts
- Conditional statements: `if`, `else if`, `else`
- Logical operators: `&&`, `||`, `!`
- Operator precedence and use of parentheses
- Input/output with `cin` and `cout`
- Type casting and ASCII values

---

## Code Snippets & Explanations
### 1. Even or Odd
```cpp
int n;
cout << "Enter a no. :";
cin >> n;
if (n % 2 == 0) {
    cout << "even";
} else {
    cout << "odd";
}
```
**Explanation:** Checks if a number is even or odd using modulo operator.

### 2. Divisibility by 5
```cpp
int n;
cout << "Enter a no. : ";
cin >> n;
if (n % 5 == 0) {
    cout << "it is divisible by 5";
} else {
    cout << "no. is not divisible by 5";
}
```
**Explanation:** Tests divisibility using modulo.

### 3. Absolute Value
```cpp
int n;
cout << "Enter an int. :";
cin >> n;
if (n < 0) {
    n = -n;
}
cout << n;
```
**Explanation:** Converts negative input to positive.

### 4. Profit or Loss Calculation
```cpp
float cp, sp;
cout << "Enter CP: ";
cin >> cp;
cout << "Enter SP: ";
cin >> sp;
if (sp > cp) {
    cout << "Gain :" << sp - cp;
} else if (sp == cp) {
    cout << "No loss or gain";
} else {
    cout << "Loss :" << cp - sp;
}
```
**Explanation:** Determines profit, loss, or break-even.

### 5. Three-Digit Number Check
```cpp
int n;
cout << "Enter an integer: ";
cin >> n;
if (n > 99 && n < 1000) {
    cout << "Number is consist of 3 digit";
} else {
    cout << "No. is not made with 3 digits";
}
```
**Explanation:** Checks if input is a three-digit number.

### 6. Divisible by 3 and 5
```cpp
int n;
cout << "Enter a number: ";
cin >> n;
if (n % 5 == 0 && n % 3 == 0) {
    cout << "No. is divisble by 5 as well as 3";
} else {
    cout << "No.  is not divisible by 5 and 3";
}
```
**Explanation:** Uses logical AND for multiple conditions.

### 7. OR Operator Example
```cpp
int n;
cout << "Enter a no.: ";
cin >> n;
if (n % 3 == 0 || n % 5 == 0) {
    cout << "The no. is divisible by 3 or 5";
} else {
    cout << "the no. is not divisible by 5 and 3";
}
```
**Explanation:** Uses logical OR for alternative conditions.

### 8. Greatest of Three Numbers
```cpp
int a, b, c;
cout << "Enter three no.: ";
cin >> a >> b >> c;
if (a >= b && a >= c) {
    cout << "The greatest no. is: " << a;
} else if (b >= c) {
    cout << "the greatest no. is: " << b;
} else {
    cout << "the greatest no. is: " << c;
}
```
**Explanation:** Finds the largest of three numbers.

### 9. Alphabet Check
```cpp
char c;
cout << "Enter a character: ";
cin >> c;
int l = int(c);
if ((l >= 65 && l <= 90) || (l >= 97 && l <= 122)) {
    cout << "The character entered is an alphabet";
} else {
    cout << "the character entered is not alphabet";
}
```
**Explanation:** Checks if input is an alphabet using ASCII values.

### 10. Vowel or Consonant
```cpp
char c;
cin >> c;
int b = int(c);
if ((b >= 65 && b <= 90) || (b >= 97 && b <= 122)) {
    if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ||
        c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U') {
        cout << "the char is a vowel";
    } else {
        cout << "char is a consonant";
    }
} else {
    cout << "the character is not an alphabet";
}
```
**Explanation:** Nested if-else for vowel/consonant check.

### 11. Triangle Side Check
```cpp
int a, b, c;
cout << "Enter 1st no.: ";
cin >> a;
cout << "Enter 2nd no.: ";
cin >> b;
cout << "Enter 3rd no.: ";
cin >> c;
if ((a + b) > c && (a + c) > b && (b + c) > a) {
    cout << "the given input are the sides of a triangle";
} else {
    cout << "the given input are not the sides of a triangle";
}
```
**Explanation:** Validates triangle side conditions.

---

## Best Practices
- Always use parentheses to clarify complex logical expressions.
- Validate user input for expected types and ranges.
- Comment your code for clarity.
- Test edge cases (e.g., zero, negative numbers).

## Common Mistakes
- Using `=` instead of `==` in conditions.
- Forgetting to use curly braces `{}` for multi-line blocks.
- Not considering operator precedence—use parentheses!
- Not handling all possible input cases.

---

## Interview Prep Questions
1. What is the difference between `if`, `else if`, and `else`?
2. How does operator precedence affect logical expressions?
3. How do you check if a character is an alphabet in C++?
4. How do you find the greatest of three numbers?
5. What is the difference between `&&` and `||` operators?
6. How do you check if a number is divisible by multiple values?
7. How do you validate triangle sides?
8. What are common pitfalls in writing if-else statements?
9. How do you check for vowels and consonants?
10. Why is input validation important?

---

## Quick Reference
- `if (condition) { ... } else { ... }`
- `&&` = AND, `||` = OR, `!` = NOT
- ASCII: A-Z (65-90), a-z (97-122)
- Use parentheses for clarity: `(cond1 || cond2) && cond3`

---

**Master these patterns and you'll be ready for C++ interviews and real-world coding!**
