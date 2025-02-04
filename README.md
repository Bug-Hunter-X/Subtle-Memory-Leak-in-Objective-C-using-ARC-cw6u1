# Subtle Memory Leak in Objective-C using ARC

This repository demonstrates a common yet subtle memory leak that can occur in Objective-C applications using Automatic Reference Counting (ARC). The leak happens when a strong property isn't properly handled in methods that might exit prematurely (e.g., due to exceptions or early returns).

## Problem
The `bug.m` file contains an example of a class with a strong property (`myString`).  If the `someMethod` function exits before setting `myString` to `nil`,  the allocated `NSString` object will not be deallocated, leading to a memory leak.

## Solution
The `bugSolution.m` file provides a corrected version where the `myString` property is explicitly set to `nil` before returning from `someMethod`, ensuring proper memory management.

## How to Reproduce
1. Clone this repository.
2. Open the project in Xcode.
3. Run the application and observe memory usage with Instruments (or a similar tool) to detect the leak in the original code and its resolution in the corrected version.