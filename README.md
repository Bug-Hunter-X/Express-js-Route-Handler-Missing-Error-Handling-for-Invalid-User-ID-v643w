# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers:  missing error handling for invalid input. Specifically, the code attempts to parse a user ID as an integer without validating whether the input is actually a number. This can lead to unexpected behavior or crashes.

The `bug.js` file shows the erroneous code. The `bugSolution.js` file provides a corrected version with robust error handling.

## How to Reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `node bug.js` (Make sure you have Node.js and npm installed).
4. Access the route `/users/<invalid_id>` (e.g., `/users/abc`).  Observe the error.
5. Run `node bugSolution.js`.  Access the same route.  Observe the improved error handling.

## Bug

The primary issue is the lack of validation for `req.params.id`. If this parameter is not a valid integer, `parseInt(userId)` will return `NaN`, causing the `users.find()` method to fail silently or potentially throw an error in some cases.  This leads to unpredictable application behavior.

## Solution

The solution involves adding input validation.  The corrected code explicitly checks whether `parseInt(userId)` returns a valid integer before proceeding.
