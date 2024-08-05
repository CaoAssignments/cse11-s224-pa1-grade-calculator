# CSE 11 Summer Session II 2024 PA1 - Grade Calculator
**Due date: Sunday, August 11th @ 11:59PM PDT**

## Goal:
Programming Assignment 1 is an introduction to Java programming. In this PA, you will get exposure to primitive data types, variables, keyboard input, console output, if-else logic, and loops. 

## Overview
There are 3 parts in this assignment. All are required before the deadline.

- Part 1: Integrity of Scholarship Agreement [Google Form, 1 point]
- Part 2: Technology Access Survey (Financial Aid) [Canvas Quiz, 1 point]
- Part 3: Grade Calculator [Gradescope, 98 points]

## Part 1: Academic Integrity [1 point]
We take Academic Integrity (AI) very seriously at UCSD. Before beginning the assignment please fill out the [AI form](https://forms.gle/nUCQvvXJPiM9AcBv9). **You must fill this out in order to recieve points for any assignments.**

## Part 2: Technology Access Survey [1 point]
Please fill out this [Technology Access Survey](https://canvas.ucsd.edu/courses/57084/quizzes/179991) on Canvas to help us understand the background and goals of the students in this course and meet the new financial aid requirement.


## Part 3: Grade Calculator [98 points]

Write a program called `GradeCalculator` that
- reads a student's scores for programming assignments, midterm, and final
- calculates their PA score and overall score by applying weights 
- outputs the overall score and its corresponding letter grade

### Setup
Please follow the instructions in the recording **vscode and java setup**  to have Java 17 installed on your machine in order to complete this assignment. Additionally, familiarize yourself with some bash commands (optional):
- Essential Commands: https://www.hongkiat.com/blog/web-designers-essential-command-lines/
- Unix reference sheet: https://files.fosswire.com/2007/08/fwunixref.pdf


### Implementaion Details
Your file should be named as `GradeCalculator.java` and contains a single class `GradeCalculator` which has only 1 method: `main`.


There are a few restrictions on the implementation. 
- You should not import anything other than `java.util.Scanner`. If you import any other libraries, you may get a 0 for this part, even though if you had passed all the test cases.
- Please do not create multiple `Scanner` objects for `System.in`. They’ll fight each other to get the input and cause all of your test cases to fail.
- You should not use `System.exit`. Doing so will cause Autograder to throw exceptions and you'll get "EXCEPT" for all of your test cases.
- You should not print any prompt (e.g. “please enter your score”).

To get started on this PA, create a folder for "PA1" at the location of your choice and open that folder in Visual Studio Code (VS Code). Then create a class named `GradeCalculator` with a `main` method and save it as `GradeCalculator.java`.

#### Input

The program reads user inputs from `System.in` using a [Scanner](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html) (*remember to import it*). When an user runs `java GradeCalculator`, the input should be taken in via the keyboard and should contain exactly 2 lines detailing the number of programming assignments $n$. You can safely assume that all our inputs will follow this format.

The first line contains $n + 1$ space-separated integers: $n \hspace{1mm} ␣ \hspace{1mm} pa_1 \hspace{1mm} ␣ \hspace{1mm}pa_2\hspace{1mm} ␣ \hspace{1mm}pa_3 \hspace{1mm} ...  \hspace{1mm} pa_n$, where 
- $n$ is an integer representing the number of programming assignments
- $pa_1\hspace{1mm} ␣ \hspace{1mm}pa_2\hspace{1mm} ␣ \hspace{1mm}pa_3 \hspace{1mm} ...  \hspace{1mm} pa_n$ are integers representing the score for each programming assignment
- $␣$ means a space

The second line contains 2 space-separated integers: the first one represents the midterm score and the second one represents the final score.

If any score is less than 0 or greater than 100, or if the number of programming assignments $n$ is equal to 0, print `invalid input`. You may assume that $n$ will greater or equal to 0.

Additionally, you may also assume that when we divide the total PA score by the given $n$ (the number of PAs), the average will not be a repeating decimal. In other words, you don't need to round anything and recurring average scores such as $97.\overline{6}$ and $97.\overline{142857}$ will not be tested.

#### Calculation
1. find the average score of programming assignments
2. calculate the overall score by using the *Grade Breakdown* table below

    | Type                    | Weight|
    | ----------------------- | ----- |
    | Programming Assignment  | 50%   |
    | Midterm Score           | 12.5% |
    | Final Score             | 37.5% |

3. determine letter grade using the overall score
    - 90 <= overall score <= 100: `A`
    - 80 <= overall score < 90: `B`
    - 70 <= overall score < 80: `C`
    - 60 <= overall score < 70: `D`
    - 0 <= overall score < 60: `F`

#### Output

Write the output to the standard output, which prints the overall score in the first line and the letter grade in the second line. There should be a **newline character** at the end of line. 
**Note:** `System.out.println()` method prints the text on the console and the cursor remains at the start of the next line at the console (i.e. it appends a newline character at the end of the line, so you **do not** need to add a newline character by yourself if you are using `System.out.println`). 
**Please follow the exact output format, or otherwise you will not get any credit.**


### Example Input and Output

#### Example 1

- Input
    ```
    > java GradeCalculator
    5 90 100 91 95 84
    80 90
    ```
    First line: there are 5 programming assignment scores: 90, 100, 91, 95, and 84. 
    
    Second line: the midterm score is 80 and the final is 90. 
- Output
    ```
    89.75
    B
    ```
    $\frac{90 + 100 + 91 + 95 + 84}{5} \times 0.5 + 80 \times 0.125 + 90 \times 0.375 = 89.75$
    
    The overall score is in between 80 and 90, so the letter grade is B.


#### Example 2

- Input
    ```
    > java GradeCalculator
    8 90 85 82 98 95 87 65 84
    70 65
    ```

- Output
    ```
    76.0
    C
    ```
    $\frac{90 + 85 + 82 + 98 + 95 + 87 + 65 + 84}{8} \times 0.5 + 70 \times 0.125 + 65 \times 0.375 = 76.0$
    
    The overall score is in between 70 and 80, so the letter grade is C.

#### Example 3
- Input
    ```
    > java GradeCalculator
    3 110 99 90
    20 30
    ```

- Output
    ```
    invalid input
    ```
    *Note: As long as there is an invalid programming assignment score, we stop scanning exam scores. In this case, since the first PA score is above 100, print out the `invalid input` directly.*

#### Example 4
- Input
    ```
    > java GradeCalculator
    8 9 85 82 98 95 87 65 84
    -10 100
    ```

- Output
    ```
    invalid input
    ```

### Testing
Try the example inputs described above. Do you get the same results as their corresponding outputs? Now try some of your own inputs, do you get the results you would expect?

## Submission
Submit all of the following files to Gradescope by **Sunday, August 11 @ 11:59PM PDT**.
 - `GradeCalculator.java`


You can submit as many times as you want on Gradescope, and you will see the results right after each submission. **Only for this PA**, you are able to see all the test cases and results when you submit your assignment to Gradescope. It is your responsibility to test your program comprehensively. 

**Important:** Even if your code does not pass all the tests, you will still be able to submit your homework to receive partial points for the tests that you passed. **Make sure your code compiles on Autograder in order to receive partial credit. The name of the file needs to be `GradeCalculator.java`, otherwise no points.** 


### How your assignment will be evaluated [100 points]


* **Correctness** [98 points] You will earn points based on the autograder tests that your code passes. If the autograder tests are not able to run (e.g., your code does not compile or it does not match the specifications in this writeup), you may not earn any credit.
* **Integrity of Scholarship Agreement** [1 point]
* **Technology Access Survey** [1 point]
