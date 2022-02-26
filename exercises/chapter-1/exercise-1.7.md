# Exercise 1.7

The `good-enough?` test used in computing square roots will not be very effective
for finding the square roots of very small numbers. Also, in real computers,
arithmetic operations are almost always performed with limited precision. This
makes our test inadequate for very large numbers. Explain these statements, with
examples showing how the test fails for small and large numbers. An alternative
strategy for implementing `good-enough?` is to watch how guess changes from one
iteration to the next and to stop when the change is a very small fraction of the
guess. Design a `square-root` procedure that uses this kind of end test. Does
this work better for small and large numbers?

## Answer

We can improve the `good-enough?` procedure implementing a percent error formula defined as:

![equation](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;%Error&space;=&space;\left|&space;\frac{x&space;-&space;x_{e}}{x}&space;\right|)

Where `x`<sub>`e`</sub> is the estimated value and `x` is the known or actual value.


```scheme
(define (square x)
    (expt x 2))

(define (average x y)
    (/ (+ x y) 2))

(define (percent-error xi x)
    (abs (/ (- x xi) x)))

(define (good-enough? xi x)
    (< (percent-error xi x) 0.00001))

(define (improve-guess guess x)
    (average guess (/ x guess)))

(define (sqrt-iter guess x)
    (if (good-enough? (square guess) x)
        guess
        (sqrt-iter (improve-guess guess x) x)))

(define (sqrt x)
    (sqrt-iter 1.0 x))
```
