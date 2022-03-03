# Randomized Algorithm: Monte Carlo Algorithm (22/03/03)

## Some Intro and Definition

Idea of Monte Carlo Algo: use random samples of parameters or inputs to
explore the behavior of a complex system or process.

In computing, a Monte Carlo algorithm is a randomized algorithm whose
output may be **incorrect with a certain (typically small)
probability**. (Las Vegas algorithms are a dual of Monte Carlo
algorithms that always return an correct answer.)

For example, in physics problems, such as models of neutron diffusion,
that were too complex for an analytical solution, so they had to be
evaluated numerically.

Two laws you need to know before entering Monte Carlo Algorithm.

## [Law of Large Numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers) (proof in [Textbook](https://github.com/kickyourasss/textbook/blob/c99cfaa3333434dffd9aabf09799f178e8fb9ef7/A%20coincise%20course.pdf) PDF 79)

This theorem describes the if performing the same experiment a large
number of times, then average of the results obtained should be close to
the **expected** value and tends to become closer to the expected value
as more trials are performed.

Mathematical expression:

![](C:\Users\willc\AppData\Roaming\Typora\typora-user-images\image-20220303214827093.png)

The LLN, magical as it is, does not tell us the rate at which the
convergence takes place. How large does your sample need to be in order
for your estimates to be close to the truth? Central Limit Theorem
provides such a characterization, and more.

## [Central Limit Theorem](https://en.wikipedia.org/wiki/Central_limit_theorem) (proof in [Textbook](https://github.com/kickyourasss/textbook/blob/c99cfaa3333434dffd9aabf09799f178e8fb9ef7/A%20coincise%20course.pdf) PDF 89)

This theorem (CLT) establishes that, in many situations, when
independent random variables are summed up, their properly normalized
sum tends toward a normal distribution (informally a bell curve) even if
the original variables themselves are not normally distributed.
![image](https://user-images.githubusercontent.com/72336341/156584247-27e23831-6798-4b61-a045-95e431936fe5.png)


This theory implies that probabilistic and statistical methods that work
for normal distributions can be applicable to many problems involving
other types of distributions.
![image](https://user-images.githubusercontent.com/72336341/156584334-d58e40fa-29e4-4e57-90c1-a0b588427ede.png)

## Application of Monte Carlo Algorithm

Refer to
[here](https://github.com/wangshusen/AdvancedAlgorithms/blob/3f3e0b8db634cec2a09128fdc7c98dddea308b7c/Slides/17_Rand_1.pdf).

source:

<http://www-personal.umich.edu/~gaozheng/teaching/stats414/Simulation/simulation.html#fn1>

<https://github.com/kickyourasss/AdvancedAlgorithms>
https://www.math.arizona.edu/~jwatkins/J2_limit.pdf
