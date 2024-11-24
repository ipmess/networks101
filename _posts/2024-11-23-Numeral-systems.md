# Numeral Systems

The best resource to understand what numeral systems are is the Wikipedia page for [Numeral Systems](https://en.wikipedia.org/wiki/Numeral_system).

In essence, a numeral system is a method for representing values using glyphs. Even though there are quite a few numeral systems, when it comes to computer networking, we mainly concern ourselves only with the modern base systems. In particular we must understand how base-10, base-2, and base-16 numeral systems represent values, and how to quickly and efficiently convert between representations of the same value in each of these systems.

## Base-10

Base-10 is the decimal system. The decimal system is the most commonly used, and standard, numeral system today. For example, the number `11` represents the value _eleven_. To denote that the number 11 is a decimal number, you can strictly write the number as <span>$$ 11_{10} $$</span>. This means that the number uses the base-10 system.

In the base-10 system, every digit has two attributes:

* Its position in the whole number. We start counting from the right-most digit, and start from position 0.
* Its value of the digit.

The value that the entire _decimal numeral_ represents is equal to the sum of the product of each digit's value multiplied by the digit's position's weight. The digit's position's weight depends on the position in the numeral.

The weight of each position <span>$$ p $$</span> is equal to <span>$$ 10^p $$</span>.

For example, consider number <span>$$4378_{10}$$</span>.

The total value of the decimal numeral can be calculated as

<div>
$$\begin{align}&8\times 10^0 + 7\times 10^1 + 3\times 10^2 + 4\times 10^3 =\\
&8\times 1 + 7\times 10 + 3\times 100 + 4\times 1000\end{align}$$
</div>

The exact same logic applies to all positional numeral systems, such as base-2 and base-16.

## Base-2 (binary)

In binary, the weight of each position of a binary numeral is essentially <span>$$ 2^p $$</span>.

This gives rise to the following table:


| Position  | weight | math representation   |
| --------- | ------ | --------------------- |
| 0         | 1      | <span>$$2^0$$</span>  |
| 1         | 2      | <span>$$2^1$$</span>  |
| 2         | 4      | <span>$$2^2$$</span>  |
| 3         | 8      | <span>$$2^3$$</span>  |
| 4         | 16     | <span>$$2^4$$</span>  |
| 5         | 32     | <span>$$2^5$$</span>  |
| 6         | 64     | <span>$$2^6$$</span>  |

For example, let us consider the binary numeral <span>$$1010_2$$</span>.
