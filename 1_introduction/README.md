# Randomness in Computers

Randomness in computers is a tricky subject. That is because of the very definition of randomness itself. Randomness inherently means something that you _cannot_ predict. Emphasis on the word _cannot_. So there should be no way to not only predict the outcome, but to also not be able to 
reproduce the outcome.

This becomes particularly tricky in computers, since by their very nature, computers are deterministic systems. They are complex circuits that are designed to interpret and execute instructions. So how can we make a deterministic system produce a random output?

## What do we do?

One approach, that is taken quite commonly is the pseudo random number generator. This is a deterministic algorithm that produces a sequence of numbers that appear to be random. The key word here is _appear_. The numbers are not actually random, but they appear to be random. This is because the algorithm is designed to produce a sequence of numbers that are not easily predictable.

This has quite a few use cases despite seeming to be a bit of a hack.
For example, if you are writing a game, you might want to have some
randomness in the game. But you also want the game to be deterministic,
think of games like Minecraft, which either randomly generates the world or asks you for a seed.
This is a good example of a pseudo random number generator.
The game appears to be random, but it is actually deterministic.

There are many types of pseudo random number generators and they are talked more in
detail in the [next section](/2_pseudo_random_generators/README.md).

However, there are also some major set backs to using this approach.
For one, in places like cryptography, you want to have true randomness.
The point of cryptography is to make it so that the data is not easily
predictable. If you use a pseudo random number generator, then you are
essentially making it easier for the attacker to predict the data.
Hence, in places like cryptography, is places where this system fundamentally fails.

## Random Libraries

Nearly every major programming language has a library that provides a pseudo random number generator.
In Python, this is the `random` library. In Java, this is the `java.util.Random` class and in C++, this is the `std::rand` function.
The most popular one however is the JavaScript `Math.random` function.
This is because JavaScript is the most popular programming language in the world and is used in nearly every website.
I am sure you might have at some point used the `Math.random` function in JavaScript.

All these libraries however, are pseudo random number generators.
Hence, they are not suitable for cryptography.
For cryptography, we use a special algorithm that we will talk about in a [later section](/3_crypto_random/README.md).