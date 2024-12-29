# Closure Issue in setTimeout Loop

This repository demonstrates a common closure-related issue in JavaScript when using `setTimeout` within a loop. The expected behavior is to log numbers 0 through 9 with a one-second delay between each. However, due to the way closures work in JavaScript, the loop completes before the `setTimeout` callbacks execute, resulting in the same value of `i` (10) being logged ten times.

## Bug

The `bug.js` file contains the problematic code.  The issue is that the `setTimeout` callback function does not capture the value of `i` at the time it is created. Instead, it captures a reference to the variable `i`. By the time the `setTimeout` callbacks finally execute, the loop has already finished, and `i` holds its final value of 10. 

## Solution

The `bugSolution.js` file provides a corrected version.  The problem is solved by using an Immediately Invoked Function Expression (IIFE) to create a new scope for each iteration of the loop, capturing the current value of `i` within that scope.