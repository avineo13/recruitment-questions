# Question 1: The Scalability Horizon

## Background

You are a Cloud Infrastructure Architect at a rapidly growing SaaS company. Currently, your application handles 1,000 concurrent users across its global cluster. Your marketing team predicts a steady growth rate of 15% every month.

However, your current Nutanix cluster has a hard physical limit. Due to hardware constraints and IP address space, your current environment can support a maximum of 10,000 concurrent users. Beyond this point, you must migrate to a new data center—a process that takes significant lead time to plan.

## Problem Statement

Calculate exactly how much time (in months) you have before the system hits the "Scalability Horizon" (10,000 users).

Specifically, find $t$ where:

$$P(t) = P_0 \cdot (1 + r)^t$$

Where:
- $P_0$ = Initial users (1,000)
- $P(t)$ = Maximum capacity (10,000)
- $r$ = Monthly growth rate (0.15)
- $t$ = Time in months

## Input Format

Three space-separated floating-point numbers: `InitialUsers`, `MaxCapacity`, and `GrowthRate` (as a percentage, e.g., 15 for 15%).

## Output Format

An integer representing the number of full months you can operate safely before exceeding capacity. (Round down to the nearest whole month).

## Sample Input

```
1000 10000 15
```

## Sample Output

```
16
```

## Constraints

- $1 \le InitialUsers < MaxCapacity \le 10^6$
- $0.1 \le GrowthRate \le 100$ (as a percentage)
- The growth rate is applied monthly.
- Round down to the nearest integer month.

## Notes

- Use the exponential growth formula: $P(t) = P_0 \cdot (1 + r)^t$
- To solve for $t$, you'll need to use logarithms: $t = \frac{\log(P(t)/P_0)}{\log(1 + r)}$
- Remember to convert the growth rate percentage to a decimal (divide by 100).
- The answer should be rounded down (floor function) to the nearest whole month.
- Consider edge cases where the initial users might already exceed or be very close to the maximum capacity.

## Expected Skills Tested

- Exponential growth modeling
- Logarithmic calculations
- Mathematical problem-solving
- Understanding of compound growth
- Real-world application of mathematical concepts

