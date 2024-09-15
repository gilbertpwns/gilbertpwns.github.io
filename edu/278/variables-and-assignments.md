# variables-and-assignments

## floating-point numbers (float)

* A **floating-point number** is a real number, like 98.6, 0.0001, or -666.667. The term "floating-point" refers to the decimal point being able to appear anywhere ("float") in the number. A variable declared as type float stores a floating-point number.

* A **floating-point literal** is a number with a fractional part, even if that fraction is 0, as in 1.0, 0.0, or 99.573. Good practice is to always have a digit before the decimal point, as in 0.5, since .5 might mistakenly be viewed as 5.

---

*Scientific notation*

A system may print large or small floating-point values using scientific notation. Ex: If a float variable holds the value 299792458.0 (the speed of light in m/s), the value may be printed as 2.99792e+08. The printed value may have some rounding for conciseness, and the power of 10 makes the number's magnitude more apparent. The value held in the variable is unchanged.

## Choosing a variable type

A programmer should choose a variable's type based on the type of value held.

* Integer variables are typically used for values that are counted, like 42 cars, 10 pizzas, or -95 days.
* Floating-point variables are typically used for values that are measured, like 98.6 degrees, 0.00001 meters, or -666.667 grams.
* Floating-point variables are also used when dealing with fractions of countable items, such as the average number of cars per household.

---

↩️ [BACK](../README.md)
