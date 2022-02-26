# Exercise 1.8

Newton's method for cube roots is based on the fact that if `y` is an
approximation to the cube root of `x`, then a better approximation is given
by the value:

![equation](https://latex.codecogs.com/svg.image?\bg_white&space;\frac{\frac{x}{y^{2}}&space;&plus;&space;2y}{3})

Use this formula to implement a `cube-root` procedure analogous to the
`square-root` procedure.

## Answer

```scheme
(define (cube x)
    (expt x 3))

(define (average x y)
    (/ (+ x y) 2))

(define (percent-error xi x)
    (abs (/ (- x xi) x)))

(define (good-enough? xi x)
    (< (percent-error xi x) 0.001))

(define (improve-guess guess x)
    (/ (+ (/ x (expt guess 2)) (* 2 guess)) 3))

(define (cube-root-iter guess x)
    (if (good-enough? (cube guess) x)
        guess
        (cube-root-iter (improve-guess guess x) x)))

(define (cube-root x)
    (cube-root-iter 1.0 x))
```
