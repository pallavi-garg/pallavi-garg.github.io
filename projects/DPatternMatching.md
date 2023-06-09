---
layout: project
type: project
image: img/patternmatching/logo.jpg
title: "Exact Pattern Matching"
date: "May 2023"
position: 4
published: true
labels:
  - C++
  - Algorithms
  - Pattern Matching
summary: "Analysis of various algorithms used for exact pattern matching. By evaluating their performance and considering factors such as time complexity and pattern length, the project aimed to provide insights into selecting the most suitable algorithm for efficient and accurate pattern matching tasks."
---

## Problem Statement
Analysis of various algorithms used for exact pattern matching. The analysis involves analyzing the time complexity by measuring the time taken by each algorithm to find the first occurrence of the given pattern in the given text. The scenarios where pattern does not appear in the text are not considered as they won’t tell us about the time taken (and number of comparisons) because pattern match would fail at the first comparison and the algorithms under consideration will move ahead in the text.

## Algorithms
For the solution, I am using three algorithms:

1. Brute Force
2. Knuth-Morris-Pratt (KMP)
3. Boyer-Moore-Horspool (BMH)
4. Bitap
5. Rabin Karp

## Test Setup
Each algorithm is run with the same text and pattern. Each iteration of the experiment is done on the same machine. I analyze the algorithms by considering two scenarios.
1. Random Strings
2. English strings and words

#### Random Strings Testing Setup
A random string of length 10,000 ASCII characters is characters. The initial test string is created without the letters - a, b, c, d, e, f, g, h, i, j. The letters in the initial string at three sets of fixed position are then replaced with
“abcdeabcdefghij”. The three position sets are: index 500 to 515, index 5000 to 5015, index 9000 to 9015. These ranges are chosen to analyze the algorithms where pattern is found in beginning, middle, and end of the large text. The pattern to be searched ranges with length 2 - 10. For example “ab”, “abc”, “abcd”, and so on up to “abcdefghij”. The test has just once occurrence of each pattern. The final results for each set of indices and each pattern length are then averaged in an effort to analyze the time complexity when the pattern is spread across the entire text.

#### English Strings and Words Testing Setup
In this setup, a long [text](../img/patternmatching/longtext.txt) is chosen. The patterns to be searched are of the length 2 - 10. For each length, 50 words are selected from the English dictionary. Each algorithm searches for the same pattern in the same text.

## Observations
- Overall the KMP algorithm performs the best in these test settings.
- The Brute force and the Bitap algorithm also perform about the same in random string test setting.
- The Bitap algorithm performance is quite close to that of KMP in english string test setup.

**Random Strings**
<img class="img-fluid" src="../img/patternmatching/random.png" >

**English Strings**
<img class="img-fluid" src="../img/patternmatching/english.png" >

## Conclusion
As per the observations, in both test settings KMP performs the best in both these test setups.
The BMH algorithm performed poorly in this setup.

The reason for this observation is that:
1. The KMP uses the information about the previous comparisons which makes it fast for
these scenarios. Because of the large degree of similarity among portions of pattern and
text in English words setup, the BMH algorithm makes a lot of comparisons before it is
able to find a match.
2. In both the test setups, text contains a large number of repeating characters and BMH
algorithm relies on the “bad character shift” to determine how far to move the pattern
when mismatch occurs. Which makes it shift the pattern by a small amount only,
resulting in greater number of comparisons. On the other hand, the KMP algorithm uses
the previous match information, which makes it much faster.

In general, it is noticeable from both the graphs, that brute force algorithm performance is better
than both Rabin Karp and BMH algorithms. This shows that depending on the problem, brute
force algorithm might be a better choice.

Overall, the performance of these algorithms depends on the characteristics of the specific
problem being solved. It is important to consider the properties of the text and pattern when
selecting an algorithm for string matching


[Source Code](https://github.com/pallavi-garg/PatternMatching).
