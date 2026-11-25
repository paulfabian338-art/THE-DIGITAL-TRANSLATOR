# Tier 4 - Data Translator

## The customer information

Customer name:   Victor
Age:             30
Account balance: 150000.50
Account active:  Yes


## Identifying the data
| Information | Kind of information | Why |
|---|---|---|
| Victor | Text | A sequence of characters (a name) |
| 30 | Whole number | A count of years, no decimal part |
| 150000.50 | Number with a decimal | A money quantity with a fractional part |
| Yes | True/false state | Only two possible states: active or not active |

## Why each needs its own representation
The computer must tell these apart:
- `Victor` is a name. You cannot add it to something or calculate with it.
- `30` is a quantity. You can compare it ("is the customer over 18?") or add to it.
- `150000.50` is a quantity with a decimal part, so it needs a representation that can hold fractions.
- `Yes` is not a word to the computer. It is a condition, a state that is either true or false.

If the computer did not know the kind of each value, it could not decide what operations are allowed.

## Going one level deeper: how it becomes digital

Real-world information
        |
Data representation
        |
Numerical / digital representation
        |
Binary data (0s and 1s)
        |
Stored by the computer


- **"Victor"** is stored as characters. Each letter is given a number code, and each code is stored as binary.
- **30** is stored as a whole number in binary.
- **150000.50** is stored using a number format that supports decimals, also in binary.
- **Yes (active)** is stored as one of two states, such as 1 for active and 0 for inactive.

Not every piece of information is stored in the same format, but everything ends up as binary.

## Reasoning challenge: the balance is stored incorrectly
**Instead of 150000.50, the system interprets the stored data as a different value. What could happen?**

- The customer could see the **wrong balance**, either too much or too little.
- If the value is too high, the customer might withdraw **money that does not exist**, and the bank loses money.
- If the value is too low, the customer might be **refused a legitimate withdrawal** or wrongly flagged as having insufficient funds.
- Reports, interest, and fees calculated from that balance would all be **wrong**.
- Trust in the system would be damaged.

**Lesson:** The bits stored are only meaningful if they are interpreted using the correct representation. The same bits read the wrong way give a completely different value.

## Key idea
> Data is information represented in a form that a computer can store, process, and communicate.