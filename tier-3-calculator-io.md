# Tier 3 - Input -> Process -> Output: The Simple Calculator

## The model
```
INPUT -> PROCESSING -> OUTPUT
```

Given:
```
number_1 = 20
number_2 = 5
```

## Operations

### Addition
- **Input:** 20, 5
- **Processing:** 20 + 5
- **Output:** 25

### Subtraction
- **Input:** 20, 5
- **Processing:** 20 - 5
- **Output:** 15

### Multiplication
- **Input:** 20, 5
- **Processing:** 20 x 5
- **Output:** 100

### Division
- **Input:** 20, 5
- **Processing:** 20 / 5
- **Output:** 4

## Summary table
| Operation | Input | Processing | Output |
|---|---|---|---|
| Addition | 20, 5 | 20 + 5 | 25 |
| Subtraction | 20, 5 | 20 - 5 | 15 |
| Multiplication | 20, 5 | 20 x 5 | 100 |
| Division | 20, 5 | 20 / 5 | 4 |

## Reasoning challenge: dividing by zero
```
number_1 = 20
number_2 = 0
```

**What happens when the program attempts 20 / 0?**
Division by zero has no valid answer. Asking "how many times does 0 fit into 20?" has no meaningful result. If the program tries anyway, it may crash, stop with an error, or return a wrong or undefined value.

**What should a well-designed program do?**
It should **check the input before processing**:
1. Receive the two numbers.
2. If the operation is division **and** the second number is 0:
   - Do **not** perform the division.
   - Output a clear message such as "Error: cannot divide by zero."
   - Optionally ask the user to enter a different number.
3. Otherwise, perform the division and output the result.

## Key lesson
A program should not blindly process whatever it receives. Good design asks: "Is this input valid for the operation I am about to perform?" and handles impossible requests safely, without crashing.