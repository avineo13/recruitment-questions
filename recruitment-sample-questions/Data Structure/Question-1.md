# Question 1: Challenge: The Ghost in the Logs

## Background

Your team has just deployed a new microservice, but the monitoring dashboard is showing intermittent "Connection Refused" errors. The application logs are being dumped into a single text file, but they are cluttered with "INFO" and "DEBUG" messages.

To identify the root cause, you need to extract specific error patterns and clean up the data so it can be fed into an incident report.

## Problem Statement

You are given a stream of log entries. Each entry contains a timestamp (which you can ignore for this task) and an IP Address. Your goal is to:

1. Count how many times each unique IP address appears in the log.
2. Identify "Suspect IPs"—those that appear strictly more than a specific threshold $T$.
3. Report these Suspect IPs in a specific order for the security team to block.

## Input Format

The first line contains an integer $N$ ($N \le 10,000$), the number of log entries.

The second line contains an integer $T$, the frequency threshold.

The next $N$ lines each contain log entries in comma-separated format. Each line contains a datetime and an IPv4 Address, separated by a comma. The datetime can be ignored for this task (e.g., `2024-01-15T08:23:15,10.0.0.1`).

## Output Format

Print the Suspect IPs that appeared strictly more than $T$ times.

- The IPs must be printed in descending order of frequency.
- If two IPs have the same frequency, sort them lexicographically (ascending).
- If no IPs exceed the threshold, print `System Stable`.

## Constraints

- $1 \le N \le 10,000$
- $0 \le T \le N$
- Each IP address is a valid IPv4 string.

## Sample Input

```
18
3
2024-01-15T08:23:15,10.0.0.1
2024-01-15T08:24:32,192.168.1.5
2024-01-15T08:25:47,172.16.0.10
2024-01-15T08:26:12,10.0.0.1
2024-01-15T08:27:03,203.0.113.42
2024-01-15T08:28:19,192.168.1.5
2024-01-15T08:29:45,10.0.0.1
2024-01-15T08:30:22,198.51.100.17
2024-01-15T08:31:08,172.16.0.10
2024-01-15T08:32:34,10.0.0.1
2024-01-15T08:33:51,192.168.1.5
2024-01-15T08:34:27,203.0.113.42
2024-01-15T08:35:14,10.0.0.1
2024-01-15T08:36:42,172.16.0.10
2024-01-15T08:37:19,203.0.113.42
2024-01-15T08:38:55,192.168.1.5
2024-01-15T08:39:31,10.0.0.1
2024-01-15T08:40:18,203.0.113.42
```

## Sample Output

```
10.0.0.1: 6
192.168.1.5: 4
203.0.113.42: 4
```

**Note:** 
- `10.0.0.1` appeared 6 times (strictly greater than threshold 3)
- `203.0.113.42` appeared 4 times (strictly greater than threshold 3)
- `192.168.1.5` appeared 4 times (strictly greater than threshold 3)
- `172.16.0.10` appeared exactly 3 times, which is not strictly greater than the threshold of 3
- Other IPs appeared less than 3 times

## Notes

- Use appropriate data structures to efficiently count IP address frequencies.
- Consider the sorting requirements: first by frequency (descending), then lexicographically (ascending).
- Remember that "strictly more than" means the count must be greater than $T$, not equal to it.
- The output format should be `IP_ADDRESS: COUNT` for each suspect IP, one per line.

