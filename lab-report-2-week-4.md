# Week 4 Lab Report 2

## Fixing Bugs

*By: **Francisco Garcia***

*Course: CSE15L*

---
**CODE CHANGE #1**
![Image](bugfix1.png)

Here is [test-file1](https://github.com/FrancGarcia/markdown-parse/blob/main/test-file1.md) for the **first** *failure-induced input*.

![Image](test1.png)

**Relationship between sympton-failure induced input-bug:**

---

**CODE CHANGE #2**
![Image](bugfix2.png)

Here is [test-file2](https://github.com/FrancGarcia/markdown-parse/blob/main/test-file2.md) for the **second** *failure-induced input*.

![Image](test2.png)

**Relationship between sympton-failure induced input-bug:**

---

**CODE CHANGE #3**
![Image](bugfix3.png)

Here is [test-file3](https://github.com/FrancGarcia/markdown-parse/blob/main/test-file3.md) for the **third** *failure-induced input*.

![Image](test3.png)

**Relationship between sympton-failure induced input-bug:**
Within the example, the *symptom produced* from the *failure-induced input* (e.g. the contents) in `test-file3.md` was the output: `java.lang.OutOfMemoryError`. This implies that there was a *bug* in our code that was causing an `infinite-loop` which led to excepeding the Java heap space. After careful observation, we found that the *bug* was within the `while-loop` in which the condition `currentIndex < markdown.length()` was always true since `currentIndex` was always `0` and less than the length of the contents in `test-file3.md`, whenever there were no brackets or parantheses in the *failure-induced input*.

---

Date: January 28, 2022
