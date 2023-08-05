# Linear Congruential Generator

Linear Congruential Generator (LCG) is a popular Psuedo Random Generator (PRG). It is a very simple algorithm that is very easy to implement. It is also very fast and efficient. However, it is not very secure and should not be used in cryptography.

## 1. Definition

The most common form of LCG is defined by the following recurrence relation:

$$
X_{n+1} = (aX_n + c) \mod m
$$

Here, in this equation:

- m, 0 < m - Modulus
- a, 0 < a < m - Multiplier
- c, 0 <= c < m - Increment
- X0, 0 <= X0 < m - Seed or Starting Value

Usually, the m, a and c values are chosen to be large prime numbers. The X0 value is chosen to be a large number that is coprime to m. This is done to ensure that the period of the LCG is as large as possible.

Larger the period, the better the LCG.

The period of an LCG is defined as the number of unique values that the LCG can generate before it starts repeating itself. The period of an LCG is at most m, but it is usually much smaller than that.

The reason for this to happen is quite complicated and is beyond the scope of this research. However, it is important to know that the period of an LCG is at most m.

## 2. Lehmer Random Number Generator

Also known as Park-Miller Random Number Generator, Lehmer Random Number Generator is a special case of LCG.

The most simple form of LCG is the Lehmer Random Number Generator, where the Increment is 0. The Lehmer Random Number Generator is defined by the following recurrence relation:

$$
X_{n+1} = (aX_n) \mod m
$$

In fact, this is the random number generator that is implemented in 
the C++ standard library. The values of m and a are 2^31 and 7^5 respectively.
These values are chosen because they are large prime numbers and they produce a period of 2^31.

The following is a simple implementation of the Lehmer Random Number Generator in C++:

**DONOT RUN THIS**:
This going to run forever and print very large numbers. This is just to show how the LCG works.

```cpp
#include <iostream>

using namespace std;

int main() {
    int m = 2147483648;
    int a = 16807;
    int x = 1;

    for (int i = 0; i < 10; i++) {
        x = (a * x) % m;
        cout << x << endl;
    }

    return 0;
}
```

Output:

```text
16807
282475249
1622650073
984943658
1144108930
470211272
...
```

This code would give you unique numbers for the first 2^31 iterations. After that, it would start repeating itself.

However, for most applications, this is not a problem. 2^31 is a very large number and it is very unlikely that you would need more than 2^31 random numbers.

## 3. RANDU

RANDU is a very popular LCG that was used in IBM mainframe computers in the 1960s. It is defined by the following recurrence relation:

$$
X_{n+1} = (65539X_n) \mod 2^{31}
$$

The RANDU LCG is very fast and efficient. It, similar to the Lehmer Random Number Generator, has a period of 2^31. However, it is not very secure and should not be used in cryptography.

The thing about RANDU is that it produces very bad random numbers. The numbers that it produces are not uniformly distributed. This means that some numbers are more likely to occur than others.

Hence, for that, I am not going to go too much into detail about RANDU.

## 4. Implementations

The Linear Congruential Generator is a very simple algorithm and it is very easy to implement.
Hence, till we had more efficient algorithms, it was the most popular algorithm for generating random numbers.

It is implemented in a lot of programming languages and libraries. It is also implemented in a lot of hardware.

You can find the full table of implementations [here](https://en.wikipedia.org/wiki/Linear_congruential_generator#Parameters_in_common_use) on Wikipedia.

## 5. Code

You can get the code implementation of the LCG in python [here](notebook.ipynb).

## 6. References

- [Linear Congruential Generator - Wikipedia](https://en.wikipedia.org/wiki/Linear_congruential_generator)

- [Linear Congruential Generator - GeeksForGeeks](https://www.geeksforgeeks.org/linear-congruential-generator/)

- [Linear Congruential Generator - Wolfram MathWorld](https://mathworld.wolfram.com/LinearCongruentialGenerator.html)

- [Linear Congruential Generator - Rosetta Code](https://rosettacode.org/wiki/Linear_congruential_generator)

- [Linear Congruential Generator - C++ Reference](https://en.cppreference.com/w/cpp/numeric/random/linear_congruential_engine)

- [Lehmer Random Number Generator - Wikipedia](https://en.wikipedia.org/wiki/Lehmer_random_number_generator)

- [RANDU - Wikipedia](https://en.wikipedia.org/wiki/RANDU)