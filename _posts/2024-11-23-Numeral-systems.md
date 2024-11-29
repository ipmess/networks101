---
title: "Numeral Systems"
date: 2024-11-23
---

# Numeral Systems

The best resource to understand what numeral systems are is the Wikipedia page for [Numeral Systems](https://en.wikipedia.org/wiki/Numeral_system).

In essence, a numeral system is a method for representing values using glyphs. Even though there are quite a few numeral systems, when it comes to computer networking, we mainly concern ourselves only with the modern standard positional systems. In particular you must understand how base-10, base-2, and base-16 numeral systems represent positive integer values, and be able to quickly and efficiently convert between representations of the same value in each of these systems.

## Base-10

Base-10 is the decimal system. The decimal system is the most commonly used, and standard, numeral system today. For example, the number `11` represents the value _eleven_. To denote (Strictly) that the number 11 is a decimal numeral, you must write the number as <span>$$ 11_{10} $$</span>. This means that the number uses the base-10 system.

In the all modern standard positional systems, every digit has two attributes:

* Its position in the whole number. We start counting from the right-most digit, and start from position 0.
* Its value of the digit.

The value that the entire _decimal numeral_ represents is equal to the sum of the product of each digit's value multiplied by the digit's position's weight. The digit's position's weight depends on the position in the numeral.

In base-10, the weight of each position <span>$$ p $$</span> is equal to <span>$$ 10^p $$</span>. In general though, the weight of of each position <span>$$p$$</span> is equal to <span>$$b^p$$</span>, where <span>$$b$$</span> is the numeral system's _base_.

For example, consider number <span>$$4378_{10}$$</span>.

The total value of the decimal numeral can be calculated as

<div>
$$\begin{align}&8\times 10^0 + 7\times 10^1 + 3\times 10^2 + 4\times 10^3 =\\
&8\times 1 + 7\times 10 + 3\times 100 + 4\times 1000\\
&8+70+300+4000=4378\end{align}$$
</div>

The exact same logic applies to all positional numeral systems, such as base-2 and base-16.

## Base-2 (binary)

In binary, the weight of each position of a binary numeral is essentially <span>$$2^p$$</span>.

This gives rise to the following table of weights per position:

| Position  | weight | math representation     |
| --------- | ------ | ----------------------- |
| 0         | 1      | <span>$$2^0$$</span>    |
| 1         | 2      | <span>$$2^1$$</span>    |
| 2         | 4      | <span>$$2^2$$</span>    |
| 3         | 8      | <span>$$2^3$$</span>    |
| 4         | 16     | <span>$$2^4$$</span>    |
| 5         | 32     | <span>$$2^5$$</span>    |
| 6         | 64     | <span>$$2^6$$</span>    |
| 7         | 128    | <span>$$2^7$$</span>    |
| 8         | 256    | <span>$$2^8$$</span>    |
| 9         | 512    | <span>$$2^9$$</span>    |
| 10        | 1024   | <span>$$2^{10}$$</span> |

For example, let us consider the binary numeral <span>$$1010_2$$</span>.

Even though the mathematically strict way to denote the base is as a subscript following the numeral, in Computer Science the widely accepted notation is to prepend `0x` to base-16 numerals, `0d` to decimal numerals, and `0b` to binary. From now on, I will try to use this notation as it is quite more convenient to write.

`0b1010` = 

<div>
$$\begin{align}&0\times 0^0 + 1\times 2^1 + 0\times 2^2 + 1\times 2^3 =\\
&0\times 1 + 1\times 2 + 0\times 4 + 1\times 8\\
&0+2+0+8=10_{10}\end{align}$$
</div>

So, `0b1010 = 0d10`.

Another restriction of all standard positional numeral systems is that the number of glyphs you need to represent digits is exactly equal to the base. So, you need 10 glyphs for base-10, 2 glyphs for base-2, and 16 glyphs for base-16.

This gives rise to the table below:

| Digit Value | base-2 | base-10 | base-16 |
| ----------- | ------ | ----------------- |
| 0           | 0      | 0       | 0       |
| 1           | 1      | 1       | 1       |
| 2           |        | 2       | 2       |
| 3           |        | 3       | 3       |
| 4           |        | 4       | 4       |
| 5           |        | 5       | 5       |
| 6           |        | 6       | 6       |
| 7           |        | 7       | 7       |
| 8           |        | 8       | 8       |
| 9           |        | 9       | 9       |
| 10          |        |         | A       |
| 11          |        |         | B       |
| 12          |        |         | C       |
| 13          |        |         | D       |
| 14          |        |         | E       |
| 15          |        |         | F       |

At this point, we can see that <span>$$10_b=b_{10}$$</span>:

<div>
$$\begin{align}&0\times b^0 + 1\times b^1=\\
&0\times 1 + 1\times b =\\
&0+b=b_{10}\end{align}$$
</div>

# Base-16

Base-16, more commonly referred to as _hexadecimal_ notation, is often used to represent large binary numbers such as MAC and IPv6 addresses.

The logic behind determining the weight of each position in a base-16 numeral is the same as with all other standard positional systems:

| Position  | weight | math representation      |
| --------- | ------ | ------------------------ |
| 0         | 1      | <span>$$16^0$$</span>    |
| 1         | 16     | <span>$$16^1$$</span>    |
| 2         | 256    | <span>$$16^2$$</span>    |
| 3         | 4096   | <span>$$16^3$$</span>    |
| 4         | 65,536 | <span>$$16^4$$</span>    |

For example, let us consider the hexadecimal numeral <span>$$A6_{16}$$</span>.

`0xA6` = 

<div>
$$\begin{align}&6\times 16^0 + A\times 16^1 =\\
&6\times 1 + 10\times 16 =\\
&6+160=166_{10}\end{align}$$
</div>


