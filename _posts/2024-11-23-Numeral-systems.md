# Numeral Systems

The best resource to understand what numeral systems are is the Wikipedia page for [Numeral Systems](https://en.wikipedia.org/wiki/Numeral_system).

In essence, a numeral system is a method for representing values using glyphs. Even though there are quite a few numeral systems, when it comes to computer networking, we mainly concern ourselves only with the modern base systems. In particular we must understand how base-10, base-2, and base-16 numeral systems represent values, and how to quickly and efficiently convert between representations of the same value in each of these systems.

## Base-10

Base-10 is the decimal system. The decimal system is the most commonly used, and standard, numeral system today. For example, the number `11` represents the value _eleven_. To denote that the number 11 is a decimal number, you can strictly write the number as 11<sub>10</sub>. This means that the number uses the base-10 system.

In the base-10 system, every digit has two attributes:

* Its position in the whole number. We start counting from the right-most digit, and start from position 0.
* Its value of the digit.

The value that the entire _decimal numeral_ represents is equal to the sum of the product of each digit's value multiplied by the digit's position's weight. The digit's position's weight depends on the position in the numeral.

The weight of each position _p_ is equal to 10<sup>p</sup>.

For example, consider number 4378<sub>10</sub> or $`4378_10`$.