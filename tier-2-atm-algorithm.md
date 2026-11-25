# Tier 2 - Algorithm Thinking: The ATM

## Problem vs Algorithm
- **Problem:** "Withdraw money from an ATM." This is the goal, not the solution.
- **Algorithm:** An ordered sequence of steps that solves the problem, including what to do when something goes wrong.

## Main goal
Withdraw money

## Broken into smaller steps
1. **Start:** The ATM waits for a card.
2. **Insert card:** The customer inserts the card.
3. **Read card:** The ATM reads the card data.
   - If the card **cannot be read**: reject it, show "Card cannot be read," return the card, end.
4. **Verify card:** Check that the card is valid, not expired, and not blocked.
   - If invalid: show a message, keep or return the card, end.
5. **Request PIN:** Ask the customer to enter their PIN.
6. **Validate PIN:** Compare the entered PIN with the bank's record.
   - If **incorrect**: show "Incorrect PIN" and count the failed attempt.
     - If attempts are fewer than 3: go back to step 5.
     - If attempts reach 3: block the card, keep it, end.
7. **Select withdrawal:** The customer chooses "Withdraw."
8. **Enter amount:** The customer types the amount.
   - If the amount is invalid (zero, negative, or not a multiple of the smallest note): ask again.
9. **Check account balance:** Compare the amount with the available balance.
   - If the amount is **greater than the balance**: show "Insufficient funds," offer a smaller amount or cancel.
10. **Check ATM cash:** Confirm the machine holds enough notes.
    - If the ATM **does not have enough cash**: show "ATM cannot dispense this amount," offer a smaller amount or cancel.
11. **Process the transaction:** Deduct the amount from the account.
    - If the transaction **cannot be completed** (network or system error): cancel it, make sure **no money is deducted**, show an error message, return the card, end.
12. **Dispense cash:** The ATM releases the notes.
    - If the cash fails to dispense: reverse the deduction and log the error.
13. **Update account:** Record the transaction and the new balance permanently.
14. **Offer receipt:** Print one if requested.
15. **Return card:** Eject the card and wait for the customer to take it.
16. **End:** Return to the waiting state.

## Flow overview
```
Insert card -> Read card -> Verify card -> Request PIN -> Validate PIN
-> Select withdrawal -> Enter amount -> Check balance -> Check ATM cash
-> Process transaction -> Dispense cash -> Update account -> Return card
```

## Thinking about failure
| What goes wrong | What the algorithm should do |
|---|---|
| Card cannot be read | Show an error, return the card, end the session |
| PIN is incorrect | Show an error, allow up to 3 attempts, then block the card |
| Amount is greater than the balance | Refuse the withdrawal, offer a lower amount or cancel |
| ATM does not have enough cash | Refuse, explain, offer a lower amount or cancel |
| Transaction cannot be completed | Cancel, deduct nothing, show an error, return the card |

## Why each step is necessary
- **Verify card and PIN:** Prevent fraud. The ATM must be sure who is asking.
- **Check balance:** Prevents customers from spending money they do not have.
- **Check ATM cash:** The ATM cannot promise money it cannot physically give.
- **Update account only after a successful dispense:** Prevents the bank from charging for cash that never came out.
- **Return the card:** The customer needs it back. Leaving it would be a security risk.

## Problem -> Algorithm -> Program
- **Problem:** The goal ("Withdraw money from an ATM").
- **Algorithm:** The solution procedure (the steps above, including failures).
- **Program:** The algorithm written in a language the computer can execute.