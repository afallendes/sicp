# Exercise 1.5

Ben Bitdiddle has invented a test to determine whether the interpreter he is
faced with is using applicative-order evaluation or normal-order evaluation.
He defines the following two procedures:

```scheme
(define (p) (p))
(define (test x y)
  (if (= x 0) 0 y))
```
Then he evaluates the expression

```scheme
(test 0 (p))
```

What behavior will Ben observe with an interpreter that uses applicative-order evaluation? What behavior will he observe with an interpreter that uses
normal-order evaluation? Explain your answer.
(Assume that the evaluation rule for the special form if is the same whether the interpreter is using normal or applicative order: The predicate expression is evaluated first, and the result determines whether to evaluate the consequent
or the alternative expression.)

## Answer

Interpreter using *applicative-order evaluation*:

```scheme
> (test 0 (p))
. (test 0 (p))
. (test 0 (p))
> ...
```

The interpreter will try to evaluate `(p)` immediately. It will invoke `(p)` over and over trying to get an evaluation that returns a primitive procedure. However, due to `(p)` definition being a recursion without stop, this will run indefinitely.

Interpreter using *normal-order evaluation*:

```scheme
> (test 0 (p))
. (if (= 0 0) 0 (p))
. (if #t 0 (p))
> 0
```

The interpreter will not evaluate `(p)` yet. Instead, it will carry the evaluation until the whole procedure is compounded of primitives only and then evaluate. In this case, invoking `(p)` will not be required in the condition and will return `0`.
