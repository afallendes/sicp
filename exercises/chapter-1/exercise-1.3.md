# Exercise 1.3

## Problem

Define a procedure that takes three numbers as arguments and returns the sum of the squares of the two larger numbers.

# Solution

```scheme
(define (1larger2 a b)
    (if (> a b) a b))

(define (sum-square2 a b)
    (+ (expt a 2) (expt b 2)))

(define (sum-square-2larger3 a b c)
    (if (> a b)
        (sum-square2 a (1larger2 b c))
        (sum-square2 b (1larger2 a c))))
```
