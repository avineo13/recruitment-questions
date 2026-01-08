# Question 1: The System Audit Trail

## Background

You are a Systems Administrator at a high-growth startup. Your security team noticed unusual activity on one of the application servers. A legacy log file, `raw_audit.log`, contains a mixture of user sessions, system pings, and unauthorized access attempts.

To prepare a report for the CTO, you need to extract specific unauthorized events, sanitize the data for privacy, and provide a summary of unique offenders.

## Problem Statement

Write a shell script or a single piped command to process `raw_audit.log` and perform the following operations:

1. **Search & Filter**: Find all lines that contain the keyword `UNAUTHORIZED` or `FAILED_LOGIN`.

2. **Sanitize (Privacy)**: The logs contain user IDs in the format `user_ID:XXXXX` (where XXXXX is a 5-digit number). Use `sed` to replace the digits with the word `HIDDEN` (e.g., `user_ID:HIDDEN`).

3. **Field Extraction**: The original logs are tab-separated or contain extra metadata like `[Thread-ID]`. Use `awk` to extract only the Timestamp (Fields 1 & 2) and the Event Message (the rest of the line), ignoring the process/thread IDs.

4. **Unique Audit**: Some automated scripts hit the server multiple times a second. Ensure your final list contains only unique entries.

5. **Reverse Chronology**: Sort the results so the most recent events appear at the top.

## Input Format

The input is provided as a log file named `raw_audit.log` in the working directory.

Format: `YYYY-MM-DD HH:MM:SS [PID] EVENT_TYPE - user_ID:XXXXX - MESSAGE`

## Output Format

Lines should be formatted as: `YYYY-MM-DD HH:MM:SS EVENT_TYPE - user_ID:HIDDEN - MESSAGE`

- Sorted by time (descending).
- Only unique entries.

## Sample Input (raw_audit.log)

```
2026-01-07 20:45:12 [101] SUCCESS - user_ID:12345 - Login successful from 192.168.1.100
2026-01-07 20:46:33 [102] SUCCESS - user_ID:23456 - File access granted: /var/www/index.html
2026-01-07 20:47:15 [103] FAILED_LOGIN - user_ID:99887 - Incorrect password attempt
2026-01-07 20:47:18 [103] FAILED_LOGIN - user_ID:99887 - Incorrect password attempt
2026-01-07 20:48:22 [104] UNAUTHORIZED - user_ID:55443 - Access to /root directory denied
2026-01-07 20:49:05 [105] SUCCESS - user_ID:34567 - Database query executed successfully
2026-01-07 20:50:12 [106] FAILED_LOGIN - user_ID:11223 - Authentication failed: invalid credentials
2026-01-07 20:51:30 [107] UNAUTHORIZED - user_ID:55443 - Attempted access to restricted API endpoint
2026-01-07 20:52:45 [108] SUCCESS - user_ID:45678 - Logout successful
2026-01-07 20:53:10 [109] FAILED_LOGIN - user_ID:99887 - Incorrect password attempt
2026-01-07 20:54:22 [110] UNAUTHORIZED - user_ID:66789 - Permission denied for /etc/passwd access
2026-01-07 20:55:15 [111] SUCCESS - user_ID:12345 - Configuration file updated
2026-01-07 20:56:33 [112] FAILED_LOGIN - user_ID:77890 - Multiple failed authentication attempts
2026-01-07 20:57:45 [113] UNAUTHORIZED - user_ID:55443 - Access to /var/log/system.log denied
2026-01-07 20:58:12 [114] SUCCESS - user_ID:88901 - Backup operation completed
2026-01-07 20:59:30 [115] FAILED_LOGIN - user_ID:99887 - Incorrect password attempt
2026-01-07 21:00:05 [116] SUCCESS - user_ID:12345 - Login successful from 10.0.0.5
2026-01-07 21:01:22 [117] UNAUTHORIZED - user_ID:99012 - Attempted privilege escalation
2026-01-07 21:02:15 [118] FAILED_LOGIN - user_ID:11223 - Authentication failed: account locked
2026-01-07 21:03:45 [119] UNAUTHORIZED - user_ID:55443 - Access to /root denied
2026-01-07 21:04:30 [120] SUCCESS - user_ID:23456 - Session established
2026-01-07 21:05:10 [121] FAILED_LOGIN - user_ID:99887 - Incorrect password attempt
2026-01-07 21:06:22 [122] UNAUTHORIZED - user_ID:44556 - Unauthorized file modification attempt
2026-01-07 21:07:15 [123] FAILED_LOGIN - user_ID:77890 - Invalid username or password
2026-01-07 21:08:22 [124] FAILED_LOGIN - user_ID:99887 - Incorrect password attempt
2026-01-07 21:09:45 [125] UNAUTHORIZED - user_ID:55443 - Access to /root denied
2026-01-07 21:10:45 [126] UNAUTHORIZED - user_ID:55443 - Access to /root denied
2026-01-07 21:11:30 [127] SUCCESS - user_ID:34567 - Transaction completed successfully
```

## Sample Output

```
2026-01-07 21:10:45 UNAUTHORIZED - user_ID:HIDDEN - Access to /root denied
2026-01-07 21:08:22 FAILED_LOGIN - user_ID:HIDDEN - Incorrect password
2026-01-07 21:05:10 FAILED_LOGIN - user_ID:HIDDEN - Incorrect password
```

## Constraints

- The script should handle the full `raw_audit.log` file provided.
- All user IDs must be sanitized (replaced with `HIDDEN`).
- Process/Thread IDs in square brackets `[PID]` must be removed.
- Duplicate entries must be eliminated.
- Output must be sorted in reverse chronological order (newest first).

## Notes

- You can use a combination of `grep`, `sed`, `awk`, `sort`, and `uniq` commands.
- Consider using pipes (`|`) to chain commands together.
- The timestamp format is `YYYY-MM-DD HH:MM:SS`.
- User IDs are always in the format `user_ID:` followed by exactly 5 digits.
- Process IDs are always in square brackets like `[123]`.

## Expected Skills Tested

- Shell scripting and command-line tools
- Text processing with `grep`, `sed`, and `awk`
- Sorting and deduplication
- Understanding of pipe operations
- Data sanitization and privacy considerations

