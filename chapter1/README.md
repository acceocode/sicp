# 1 Building Abstractions with Procedures

## [1.1 The Elements of Programming](https://sarabander.github.io/sicp/html/1_002e1.xhtml#g_t1_002e1)

### [1.1.6](https://sarabander.github.io/sicp/html/1_002e1.xhtml#g_t1_002e1_002e6)

#### Exercise 1.1
```Scheme
10
> 10

(+ 5 3 4)
> 12

(- 9 1)
> 8

(/ 6 2)
> 3

(+ (* 2 4) (- 4 6))
> 6 

(define a 3)
>

(define b (+ a 1))
> 

(+ a b (* a b))
> 19

(= a b)
> #f (false)

(if (and (> b a) (< b (* a b)))
    b
    a)
> 4

(cond ((= a 4) 6)
      ((= b 4) (+ 6 7 a))
      (else 25))
> 16

(+ 2 (if (> b a) b a))
> 6

(* (cond ((> a b) a)
         ((< a b) b)
         (else -1))
   (+ a 1))
> 16
```

<br>

#### Exercise 1.2
```Scheme
(/ (+ 5 4 (- 2 (- 3 (+ 6 (/ 4 5))))) (* 3 (- 6 2) (- 2 7)))

; pretty
(/ (+ 5
      4 
      (- 2
        (- 3
            (+ 6
                (/ 4 5)))))
    (* 3
        (- 6 2)
        (- 2 7)))
```

<br>

#### Exercise 1.3
```Scheme
(define (square x)
    (* x x))

(define (sum-of-squares x y)
    (+ (square x) (square y)))

(define (max-two-sum-of-squares a b c)
    (cond ((and (>= a c) (>= b c)) (sum-of-squares a b))
          ((and (>= a b) (>= c b)) (sum-of-squares a c))
          (else (sum-of-squares b c))))
```

<br>

#### Exercise 1.4
```Scheme
; if b > 0 a + b else a - b
```

<br>

#### Exercise 1.5

```Scheme
(define (p) (p))

(define (test x y) 
  (if (= x 0) 
      0 
      y))

(test 0 (p)) 
#|
applicative-order evaluation,
the operator and operands are evaluated first on each step,
and the resulting procedure is applied to resulting arguments.
in other words, the subexpressions are evaluated first and then the operator is applied. 

(p) is a self-calling recursive procedure and so the evlauted result of (p) is (p).
thus, the operand evalutation is never resolved looping (test 0 (p)) infinitely.

|#
> infinite recursion

(test 0 (p)) 
#| 
normal-order evaluation

for normal-order evaluation, 
operands are not evaluated until their values are needed.
therefore, operand expressions would be replaced with parameters until they reach this state

(if (= 0 0)
    0
    (p)
)

because the predicate is evaluated as true, the result would be 0 
|#

> 0
```