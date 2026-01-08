# Question 1: The Cloud Capacity Optimizer

## Background

You are managing a fleet of bare-metal servers. Multiple engineering teams have requested exclusive access to a high-performance GPU server for specific time windows. These requests often overlap.

To maximize efficiency, you need to consolidate these overlapping requests into Continuous Allocation Blocks. This allows the hardware team to see exactly when the server is "Busy" and when it has "Maintenance Windows" (gaps between blocks).

## Problem Statement

Given a list of time intervals representing server reservations, merge all overlapping intervals and return a list of consolidated blocks.

## Rules

- An interval is defined as `[start, end]`.
- If two intervals overlap (e.g., `[1, 5]` and `[4, 8]`), they must be merged into a single interval covering the entire range (`[1, 8]`).
- Intervals that "touch" (e.g., `[1, 4]` and `[4, 6]`) are also considered overlapping and should be merged.

## Input Format

The first line contains an integer $N$, the number of reservation requests.

The next $N$ lines each contain two space-separated integers: `start` and `end`.

## Output Format

The merged intervals, one per line, sorted by their start time.

Each line should contain two space-separated integers: `start` and `end`.

## Constraints

- $1 \le N \le 10^5$
- $0 \le start \le end \le 10^9$
- All intervals are valid (start $\le$ end).

## Sample Input

```
4
1 3
2 6
8 10
15 18
```

## Sample Output

```
1 6
8 10
15 18
```

## Explanation

- The intervals `[1, 3]` and `[2, 6]` overlap, so they merge into `[1, 6]`.
- The intervals `[8, 10]` and `[15, 18]` do not overlap with anything else, so they remain separate.

## Additional Test Cases

### Test Case 1

**Input:**
```
3
1 4
4 5
5 6
```

**Output:**
```
1 6
```

**Explanation:** All three intervals touch each other, so they merge into a single interval.

### Test Case 2

**Input:**
```
2
1 2
3 4
```

**Output:**
```
1 2
3 4
```

**Explanation:** The intervals do not overlap or touch, so they remain separate.

### Test Case 3

**Input:**
```
5
1 10
2 3
4 5
6 7
8 9
```

**Output:**
```
1 10
```

**Explanation:** All intervals are contained within `[1, 10]`, so they all merge into a single interval.

## Notes

- Sort the intervals by their start time first to make merging easier.
- When merging, update the end time to be the maximum of the current end and the next interval's end.
- Consider edge cases such as:
  - Single interval
  - All intervals overlapping
  - No overlapping intervals
  - Intervals that only touch at boundaries
- The algorithm should run efficiently for large inputs (consider time complexity).

## Expected Skills Tested

- Interval merging algorithms
- Sorting and array manipulation
- Greedy algorithm design
- Edge case handling
- Time complexity optimization

