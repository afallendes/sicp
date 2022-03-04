# Exercise 1.10

The following procedure computes a mathematical function called Ackermann’s
function.

```scheme
(define (A x y)
  (cond ((= y 0) 0)
        ((= x 0) (* 2 y))
        ((= y 1) 2)
        (else (A (- x 1) (A x (- y 1))))))
```

What are the values of the following expressions?

```scheme
(A 1 10)
(A 2 4)
(A 3 3)
```

Consider the following procedures, where `A` is the procedure defined above:

```scheme
(define (f n) (A 0 n))
(define (g n) (A 1 n))
(define (h n) (A 2 n))
(define (k n) (* 5 n n))
```

Give concise mathematical definitions for the functions computed by the
procedures `f`, `g`, and `h` for positive integer values of `n`.
For example, `(k n)` computes 5n<sup>2</sup>.

## Answer

The results for the first, second, and third expresions are:

```scheme
> (A 1 10)
> 1024
```

```scheme
> (A 2 4)
> 65536
```

```scheme
> (A 3 3)
> 65536
```

With `(f n)` or `(A 0 n)` series can be express as 2n.

```scheme
f(0) = 0
f(1) = 2
f(2) = 4
f(3) = 6
f(4) = 8
f(5) = 10
```

With `(g n)` or `(A 1 n)` series can be express as 2<sup>n</sup>.

```scheme
g(0) = 0 = (2 ** 0)
g(1) = 2 = (2 ** 1)
g(2) = 4 = (2 ** 2)
g(3) = 8 = (2 ** 3)
g(4) = 16
g(5) = 32
```

With `(h n)` or `(A 2 n)` series can be express as 2<sup>h(n-1)</sup>.

```scheme
h(0) = 0  = (2 ** 0)
h(1) = 2  = (2 ** 1)
h(2) = 4  = (2 ** 2)
h(3) = 16 = (2 ** 4)
h(4) = 65536 = (2 ** 16)
h(5) = 20035... = (2 ** 65536)
```
