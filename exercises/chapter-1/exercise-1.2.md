# Exercise 2

Translate the following expression into prefix form:

![equation](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D%20%5Cbg_white%20%5Cfrac%7B5%20&plus;%204%20&plus;%20(2%20-%20(3%20-%20(6%20&plus;%20%5Cfrac%7B4%7D%7B5%7D)))%7D%7B3(6%20-%202)(2%20-%207)%7D)


## Answer

```scheme
(/ (+ 5
      4
      (- 2 (- 3 (+ 6 (/ 4 5)))))
   (* 3
      (- 6 2)
      (- 2 7)))
```
