# Question 1: Email Address Detection

## Problem Statement

Write a program that uses Regular Expressions to detect all email addresses within a given text fragment.

## Input Format

The first line contains an integer $N$ ($N \le 100$), which represents the number of lines in the text fragment.

The following $N$ lines contain the unstructured text (narrative, dialogue, and technical jargon).

## Output Format

A single line containing all unique email addresses detected in the text.

- The addresses must be in lexicographical (alphabetical) order.
- The addresses must be delimited by a semi-colon (`;`).

## Sample Input

```
3
The world has fractured into lines of green code and colliding realities. Under the guidance of Victor von Doom and the Architect, we are building a new reality where chaos is a forgotten word. Reach out to our lead administrator at v.doom@latveria.gov because the prophecy says you are the one. By identifying and reinforcing anchor points of each timeline with Latverian technology, we can prevent the collapse of existence. If you have intelligence on rogue Avengers or Sentinels, contact oversight@stark-remnant.com or eyes-only@shield-underground.net.

Wait, the rabbit hole goes deeper. Multiversal Surveyor: incursions@latveria.gov. The culture of an empire is reflective of its Sovereign's DNA. Nanotech Refiner: stark-tech.recovery@doom.com. To work hard, you have to be plugged in. We will cover your health, dental, and visual insurance with no wait period. Quantum Realm Navigator: scott.lang.archive@pym-labs.org. This is your last chance. After this, there is no turning back. You take the blue pill—the story ends, you wake up in your bed and believe whatever you want to believe. Time-Slip Analyst: tva.refugee@chronos.io. You take the red pill—you stay in Wonderland, and I show you how deep the rabbit hole goes. Vibranium Metallurgist: shuri.contact@wakanda.net

Working for a startup is hard work, but there are plenty of benefits for joining a small, fun, growing team like the Resistance. Doomsday Device Architect: final.protocol@latveria.gov. Everyone's perfect workspace is unique to them. Former Avengers looking for amnesty can reach out to redemption@latveria.gov. Alternatively, you can write to the primary recruitment office at enlist@doomsday.earth! We will get you set up with whatever equipment you need to start hacking—a new 15" Macbook Pro or a neural-link chair. For technical support, contact support@latveria.gov.
```

## Sample Output

```
enlist@doomsday.earth;eyes-only@shield-underground.net;final.protocol@latveria.gov;incursions@latveria.gov;oversight@stark-remnant.com;redemption@latveria.gov;scott.lang.archive@pym-labs.org;shuri.contact@wakanda.net;stark-tech.recovery@doom.com;support@latveria.gov;tva.refugee@chronos.io;v.doom@latveria.gov
```

## Constraints

- Emails follow the standard format: `username@domain.extension`.
- The text may contain special characters, symbols, and "noise" immediately adjacent to the email addresses.
- The extraction must be case-insensitive, but the output should be lowercase.

## Notes

- Ensure your regex pattern correctly identifies valid email addresses while ignoring invalid patterns.
- Handle edge cases where email addresses might appear at the beginning or end of lines.
- Consider that email addresses may be surrounded by punctuation or whitespace.

