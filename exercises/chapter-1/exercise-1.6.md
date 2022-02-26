# Exercise 1.6

Alyssa P. Hacker doesn’t see why `if` needs to be provided as a special form. “Why can’t I just define it as an ordinary procedure in terms of `cond`?” she asks. Alyssa's friend Eva Lu Ator claims this can indeed be done, and she
defines a new version of if:

```scheme
(define (new-if predicate then-clause else-clause)
    (cond (predicate then-clause)
        (else else-clause)))
```

Eva demonstrates the program for Alyssa:

```scheme
> (new-if (= 2 3) 0 5)
5
```

```scheme
> (new-if (= 1 1) 0 5)
0
```

Delighted, Alyssa uses `new-if` to rewrite the `square-root` program:

```scheme
(define (sqrt-iter guess x)
    (new-if (good-enough? guess x)
        guess
        (sqrt-iter (improve guess x) x)))
```

What happens when Alyssa attempts to use this to compute
square roots? Explain.

## Solution

With the following program:

```scheme
(define (square x)
    (expt x 2))

(define (average x y)
    (/ (+ x y) 2))

(define (good-enough? guess x)
    (< (abs (- x (square guess))) 0.001))

(define (improve-guess guess x)
    (average guess (/ x guess)))

(define (sqrt-iter guess x)
    (if (good-enough? guess x)
        guess
        (sqrt-iter (improve-guess guess x) x)))

(define (sqrt x)
    (sqrt-iter 1.0 x))
```

When using `if` special form:

```scheme
(define (sqrt-iter guess x)
    (if (good-enough? guess x)
        guess
        (sqrt-iter (improve-guess guess x) x)))
```

```
> (sqrt (square 2))
2.0000000929222947
```

However, when using `new-if` procedure:

```scheme
(define (sqrt-iter guess x)
    (new-if (good-enough? guess x)
        guess
        (sqrt-iter (improve-guess guess x) x)))
```

```
> (sqrt (square 2))
...
```
