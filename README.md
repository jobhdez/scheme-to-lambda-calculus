# Compiler web service
My first compiler!

Todo:
- add a closure conversion pass and generate some assembly!
# Some Examples
```
(compile-scheme '(if ltrue 1 1))
(((LAMBDA (T) (LAMBDA (F) (T (LAMBDA (VOID) VOID))))
  (LAMB NIL (LAMBDA (F) (LAMBDA (Z) (F Z)))))
 (LAMB NIL (LAMBDA (F) (LAMBDA (Z) (F Z)))))
 
* (compile-scheme '(and 1 1))
(((LAMBDA (F) (LAMBDA (Z) (F Z))) (LAMB NIL (LAMBDA (F) (LAMBDA (Z) (F Z)))))
 (LAMB NIL (LAMBDA (T) (LAMBDA (F) (F (LAMBDA (VOID) VOID))))))
 
* (compile-scheme '(- 1 1))
(((LAMBDA (N)
    (LAMBDA (M)
      ((M
        (LAMBDA (N)
          (LAMBDA (F)
            (LAMBDA (Z)
              (((N (LAMBDA (G) (LAMBDA (H) (H (G F))))) (LAMBDA (U) Z))
               (LAMBDA (U) U))))))
       N)))
  (LAMBDA (F) (LAMBDA (Z) (F Z))))
 (LAMBDA (F) (LAMBDA (Z) (F Z))))
 
* (compile-scheme '(+ 0 0))
(((LAMBDA (N) (LAMBDA (M) (LAMBDA (F) (LAMBDA (Z) ((M F) ((N F) Z))))))
  (LAMBDA (F) (LAMBDA (Z) Z)))
 (LAMBDA (F) (LAMBDA (Z) Z)))
 
* (compile-scheme '(* 0 0))
(((LAMBDA (N) (LAMBDA (M) (LAMBDA (F) (LAMBDA (Z) ((M (N F)) Z)))))
  (LAMBDA (F) (LAMBDA (Z) Z)))
 (LAMBDA (F) (LAMBDA (Z) Z)))
 
* (compile-scheme '(= 0 0))
((((LAMBDA (N)
     ((N (LAMBDA () (LAMBDA (T) (LAMBDA (F) (F (LAMBDA (VOID) VOID))))))
      (LAMBDA (T) (LAMBDA (F) (T (LAMBDA (VOID) VOID))))))
   (((LAMBDA (N)
       (LAMBDA (M)
         ((M
           (LAMBDA (N)
             (LAMBDA (F)
               (LAMBDA (Z)
                 (((N (LAMBDA (G) (LAMBDA (H) (H (G F))))) (LAMBDA (U) Z))
                  (LAMBDA (U) U))))))
          N)))
     (LAMBDA (F) (LAMBDA (Z) Z)))
    (LAMBDA (F) (LAMBDA (Z) Z))))
  (LAMB NIL
   ((LAMBDA (N)
      ((N (LAMBDA () (LAMBDA (T) (LAMBDA (F) (F (LAMBDA (VOID) VOID))))))
       (LAMBDA (T) (LAMBDA (F) (T (LAMBDA (VOID) VOID))))))
    (((LAMBDA (N)
        (LAMBDA (M)
          ((M
            (LAMBDA (N)
              (LAMBDA (F)
                (LAMBDA (Z)
                  (((N (LAMBDA (G) (LAMBDA (H) (H (G F))))) (LAMBDA (U) Z))
                   (LAMBDA (U) U))))))
           N)))
      (LAMBDA (F) (LAMBDA (Z) Z)))
     (LAMBDA (F) (LAMBDA (Z) Z))))))
 (LAMB NIL (LAMBDA (T) (LAMBDA (F) (F (LAMBDA (VOID) VOID))))))
 
* (compile-scheme '(quote ()))
(LAMBDA (ON-CONS) (LAMBDA (ON-NIL) (ON-NIL (LAMBDA (VOID) VOID))))


* (compile-scheme '(letrec ((f (lambda (n) (if (= n 0) 1 (* n (f (- n 1))))))) (f 5)))
((((LAMB F) (F (LAMBDA (F) (LAMBDA (Z) (F (F (F (F (F Z)))))))))
  ((LAMB (Y) (LAMB (F) (F (LAMB (X) (((Y Y) F) X)))))
   (LAMB (Y) (LAMB (F) (F (LAMB (X) (((Y Y) F) X)))))))
 ((LAMB (F (LAMB (VOID) VOID)))
  (LAMB (N)
   ((((((LAMBDA (N)
          ((N (LAMBDA () (LAMBDA (T) (LAMBDA (F) (F (LAMBDA (VOID) VOID))))))
           (LAMBDA (T) (LAMBDA (F) (T (LAMBDA (VOID) VOID))))))
        (((LAMBDA (N)
            (LAMBDA (M)
              ((M
                (LAMBDA (N)
                  (LAMBDA (F)
                    (LAMBDA (Z)
                      (((N (LAMBDA (G) (LAMBDA (H) (H (G F))))) (LAMBDA (U) Z))
                       (LAMBDA (U) U))))))
               N)))
          N)
         (LAMBDA (F) (LAMBDA (Z) Z))))
       (LAMB NIL
        ((LAMBDA (N)
           ((N (LAMBDA () (LAMBDA (T) (LAMBDA (F) (F (LAMBDA (VOID) VOID))))))
            (LAMBDA (T) (LAMBDA (F) (T (LAMBDA (VOID) VOID))))))
         (((LAMBDA (N)
             (LAMBDA (M)
               ((M
                 (LAMBDA (N)
                   (LAMBDA (F)
                     (LAMBDA (Z)
                       (((N (LAMBDA (G) (LAMBDA (H) (H (G F)))))
                         (LAMBDA (U) Z))
                        (LAMBDA (U) U))))))
                N)))
           (LAMBDA (F) (LAMBDA (Z) Z)))
          N))))
      (LAMB NIL (LAMBDA (T) (LAMBDA (F) (F (LAMBDA (VOID) VOID))))))
     (LAMB NIL (LAMBDA (F) (LAMBDA (Z) (F Z)))))
    (LAMB NIL
     (((LAMBDA (N) (LAMBDA (M) (LAMBDA (F) (LAMBDA (Z) ((M (N F)) Z))))) N)
      (F
       (((LAMBDA (N)
           (LAMBDA (M)
             ((M
               (LAMBDA (N)
                 (LAMBDA (F)
                   (LAMBDA (Z)
                     (((N (LAMBDA (G) (LAMBDA (H) (H (G F))))) (LAMBDA (U) Z))
                      (LAMBDA (U) U))))))
              N)))
         N)
        (LAMBDA (F) (LAMBDA (Z) (F Z)))))))))))
```

# Acknowledgement
This tiny compiler is based on the one [compiler](https://matt.might.net/articles/compiling-up-to-lambda-calculus/) by Dr. Might. This tiny compiler, so far, it is just a re-write of his.
