# Exercise 1.4

Observe that our model of evaluation allows for combinations whose operators are
compound expressions. Use this observation to describe the behavior of the
following procedure:

```scheme
(define (a-plus-abs-b a b)
  ((if (> b 0) + -) a b))
```

# Answer

The procedure uses a combination of `+` and `-` to compound an expression that evaluates as a sum expression if the value is `b` is greater than zero or as a subtraction otherwise.
