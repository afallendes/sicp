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

When using `new-if` procedure:

```scheme
(define (sqrt-iter guess x)
    (new-if (good-enough? guess x)
        guess
        (sqrt-iter (improve-guess guess x) x)))
```

The program does not return a result and stays computing indefinitely instead.

```scheme
> (sqrt (square 2))
...
```

This is due to the applicative-order evaluation forcing the `new-if` to return a all primitives before evaluation, creating an infinite cycle of invoking and evaluation.

```scheme
> (sqrt (1 2))
. (new-if (good-enough? 1 2)
    1
    (sqrt-iter (improve-guess 1 2) 2))
. (new-if #f 1 (sqrt-iter 1.5 2))

... many iterations later ...

. (new-if (good-enough? 2 2)
    2
    (sqrt-iter (improve-guess 2 2) 2))
. (new-if #t 2 (sqrt-iter 2 2))
. (new-if (good-enough? 2 2)
    2
    (sqrt-iter (improve-guess 2 2) 2))
. (new-if #t 2 (sqrt-iter 2 2))
. (new-if (good-enough? 2 2)
    2 
    (sqrt-iter (improve-guess 2 2) 2))
. (new-if #t 2 (sqrt-iter 2 2))

... indefinitely ...
```
