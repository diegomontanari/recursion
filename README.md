# Introduction to Recursion

Recursion is a powerful programming technique where a function calls itself in order to solve smaller instances of the same problem. This technique is commonly used to break down complex problems into simpler subproblems, and it is especially useful for tasks involving repeated operations, such as searching, sorting, and traversing data structures like trees and graphs.

## Key Concepts

1. **Base Case**: The condition under which the recursive function stops calling itself. Without a base case, the recursion would continue indefinitely, causing a stack overflow.

2. **Recursive Case**: The part of the function where it calls itself with a modified argument, usually a simpler or smaller problem.

3. **Stack**: Each recursive call creates a new frame on the call stack. Once the base case is reached, the recursion starts unwinding, and each frame is removed from the stack in reverse order.

## When to Use Recursion

Recursion is ideal for problems that have the following characteristics:

- A problem can be broken down into similar subproblems.
- The solution to the subproblems is easier to solve.
- The problem involves a natural hierarchical structure (e.g., tree traversal).

## Performance Considerations

Although recursion can be a very elegant solution, it is important to keep in mind that:

- Recursive calls can consume significant memory due to the call stack, especially for large inputs.
- Iterative solutions may be more efficient in certain cases, particularly when the recursion depth is large.

---

## Recursive Printing - How the Order Changes: the analogy of the two arrows.

I came up with this analogy that helped me understand recursion better. I hope it can help you too.

First, take a look at this recursive function:

```python
def recursive(n):
    if n == 0:
        return
    recursive(n // 10)  # Recursive call first
    print(n)  # Print after the recursion

recursive(5248)
```
The execution order will be as follows:

recursive(5248) is called, but it is suspended because it calls recursive(524).
recursive(524) is suspended because it calls recursive(52).
recursive(52) is suspended because it calls recursive(5).
recursive(5) is suspended because it calls recursive(0).
recursive(0) reaches the base case → we start returning from the recursive calls, printing the numbers in increasing order as we go back up (5, 52, 524, 5248).

This means that the output will be:
```
5
52
524
5248
```
Note that all suspended functions are momentairly stored in the stack, until they are used.

You can Immagine this flow as 2 arrows pointing different directions: one is pointing down, reducing the number but not printing anything, since the function calls itself and "starts over" and the print function is not "seen" by the program.

When the recursive process is completed, the stack starts from the last function stored to be freed, imagine this as an arrow pointing up. In this case, the number is printed and incremented every time.

Good, but this is not the ......










Imagine the recursive process as a sequence of arrows:

### Printing after the recursive call (descending order):

- The arrow goes down first, meaning we call the recursive function to reduce the number and solve the smaller subproblem.
- During the "downward path," the program suspends each recursive call and accumulates the results in the call stack, without printing anything.
- Once we reach the base case (n=0), the function stops making additional calls, and at that point, it starts ascending, printing the numbers in reverse order: starting from the smallest number (e.g., 5, then 52, then 524, and finally 5248).

```python
def recursive(n):
    if n == 0:
        return
    recursive(n // 10)  # Recursive call first
    print(n)  # Print after the recursion

recursive(5248)


