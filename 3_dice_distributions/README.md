# Random Dice Distributions

This is a simple experiment to look a bit into the central limit theorem.

## 0. Code

The code for this experiment can be found [here](notebook.ipynb).

This is the main function that determines the distribution of the sum of `dice_n` dice rolls. You can just copy paste this function and use it in your code.

```python
def plot_rolls(dice, n=100000):
    rolls = [sum(random.randint(1, 6) for _ in range(dice))
             for _ in range(n)]

    sum_outcomes = np.arange(dice, dice * 6 + 1)
    sum_counts = [rolls.count(sum_val) for sum_val in sum_outcomes]

    probabilities = np.array(sum_counts) / n

    # Means and standard deviations

    mean = np.mean(rolls)
    stdev = np.std(rolls)

    print(f"Mean: {mean:.2f}")
    print(f"Standard deviation: {stdev:.2f}")

    plt.style.use('seaborn-whitegrid')
    plt.figure(figsize=(10, 6))
    plt.plot(sum_outcomes, probabilities, marker='o', linestyle='-', color='b')
    plt.xlabel(f"Sum of {dice} Dice Rolls")
    plt.ylabel("Probability")
    plt.title(f"Probability of Sum Outcome by Rolling {dice} Dice")
    plt.grid(axis='y', linestyle='--', alpha=0.7)
    plt.show()
```

You will need to have `numpy`, `matplotlib` and `seaborn` installed to run this code.

## 1. Introduction

### What is the central limit theorem?

Central limit theorem states that any distribution with a finite mean and variance will tend to a normal distribution as the number of samples increases.
The number of samples required for this to happen is not fixed. It depends on the distribution.

So, in case, a general trend of about 40 samples is where it starts to look like a normal distribution. It may be more or less for other distributions.

### Why is it important?

The central limit theorem is important because it allows us to use normal distribution to model a lot of real world phenomenon.
So, for example, without it, we would never be able to say without context that dice rolls follow a uniform distribution.

This might not seem like a big deal but it is. It allows us to use a lot of mathematical tools to model real world phenomenon.

## 2. Experiment

In the experiment, a simple function a written that emulates the roll of a dice. The function returns a random number between 1 and 6.
This number is not truly random. It is generated using a pseudo random generator. However, for the purposes of this experiment, it is good enough.

Next, another function plots the distribution of the sum of `dice_n` dice rolls and the number of times it occurs.

So, if we roll 2 dice, the sum can be anywhere between 2 and 12. The function plots that using a standard seaborn stylized graph.

This plot is analyzed for different values of `dice_n` to see how the distribution changes. The `dice_n` at which the distribution starts to look like a normal distribution is noted.

## 3. Results

The results are as expected. The distribution starts to look like a normal distribution at around 40 samples.

However, 50 samples is where it starts to look like a proper normal distribution. Now, we can use a normal distribution to model the sum of dice rolls.

This can also be empirically verified by plotting the distribution of the sum of dice rolls for a large number of samples, which is probably too much work.

## 4. Conclusion

Hence, as you can see, the central limit theorem holds quite good for any random distribution with a finite mean and variance.
In our case, when we used `n=50`, the distribution had a mean of 174.97
and standard deviation: 12.08. These satisfy the conditions for the central limit theorem, hence we had a normal distribution.

The central limit theorem, theoritically starts to hold at `n=31`, so in statistics, you will see that `n>30` is used as a rule of thumb.

## 5. References

- [Central Limit Theorem](https://en.wikipedia.org/wiki/Central_limit_theorem)
- [Dice Roll Distribution](https://en.wikipedia.org/wiki/Probability_distribution#Discrete_probability_distribution)