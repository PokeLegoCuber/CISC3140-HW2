#lang racket
(define luhnalgo
  (lambda (n)
    (let loop ((num n)(index 0)(final 0))
      (if (= 0 num)(= 0 (remainder final 10))
          (loop (quotient num 10) (+ index 1)(+ final
                   (if (even? index)
                       (remainder num 10)
                       (let ((part (* 2 (remainder num 10))))
                         (+ (remainder part 10) (quotient part 10))))))))))
;To run this program
;1)Hit run
;2)Type (map luhnalgo '(4111111111111111)) and the result should be (#t) meaning true
;3)Type (map luhnalgo '(4111111111111112)) and the result should be (#f) meaning false
;4)You can also type (map luhnalgo '(4111111111111111 4111111111111112)) and the result should be (#t #f) 