---
layout: lab
num: lab10
ready: false
desc: "Recursion"
assigned: 2021-11-18 08:00
due: 2021-12-03 23:59
---

# NOT READY YET
# NOT READY YET
# NOT READY YET
# NOT READY YET
# NOT READY YET
# NOT READY YET

<div style="font-size:300%">
I really mean it.<br />
Please wait to start this lab</br>
until you are told it is ready.</br>
Thanks!
</div>


# Goals for this lab


This lab will have you do programming exercises with C-strings, string class objects, recursive functions, and Makefiles. You will also get more practice writing programs from scratch with little skeleton code.

# Step by Step Instructions

## Step 1: Getting Ready

1. Go to github and find a repo for this lab assigned to your GitHub id.
2. Log on to your CSIL account.
3. Change into your `~/cs16` directory
4. Clone your empty lab06 repo into your `~/cs16` directory.
5. In your empty repo, do `git checkout -b main` to establish that you are on the `main` branch as your default branch.


## Step 2: Obtain the starter code

The starter code is in this repo:

* <https://github.com/ucsb-cs16-f21/STARTER-lab10>

The URL for cloning this repo is this: `git@github.com:ucsb-cs16-f21/STARTER-lab10.git`

Previous labs contain instruction for the process of:
* Adding a `starter` remote for this repo
* Pulling the code from that `starter` remote into your own repo.

Please do those steps now, and then do a `git push origin main` to populate your own repo with the starter code.

If you need help with these steps:
* First consult previous labs for more detailed instructions.   
* Then, if you are still having trouble, ask the staff for help during discussion section or office hours.

Once you've populated your repo, typing the `ls` command should show you the following files in your current directory

```
$ ls
linkedList.h            recLinkedListFuncs.cpp  strFuncs.h
linkedListFuncs.cpp     recLinkedListFuncs.h    tddFuncs.cpp
linkedListFuncs.h       strFuncs.cpp            tddFuncs.h
$ 
```

This lab will have you write two functions that are specified in `strFuncs.h` and two functions that are specified in `recLinkedListFuncs.h`. You must implement these functions in `strFuncs.cpp` and `recLinkedListFuncs.cpp`. You must follow the instructions carefully. It is not enough to pass the gradescope check as the instructor and the TAs *will* be checking your submitted code to make sure your solution is using recursion where required.  

If you use an iterative solution (i.e. one that uses loops rather than recursion to solve the problem) you are missing the point of the assignment. So please do ask a staff member to check your solution during office hours or lab if you are not sure whether it qualifies.  (We will not accept requests over email or Campuswire to check solutions for recursion; you must come to either lab or office hours, either in person or via Zoom to request this check.)

## Program to find if two strings are anagrams

 In the file `strFuncs.cpp`, write a function called isAnagram that takes two strings as arguments and returns a boolean true if the two strings are anagrams, otherwise it returns false. The function should not be case sensitive and should disregard any punctuation or spaces. Two strings are anagrams if the letters can be rearranged to form each other. For example, “Eleven plus two” is an anagram of “Twelve plus one”. Each string contains one “v”, three “e’s”, two “l’s”, etc. Similarly "Rats and Mice" and "in cat's dream" are anagrams of each other. You may use any of the C-string library or string class functions to complete this code. You may **not** use built-in C++ functions that we have NOT discussed in lecture. You should follow a TDD style of coding where you write tests before writing your code. 
 
 ## Possible approaches

  Let's see if the strings `I Am Lord Voldemort` and `Tom,marvolo,riddle` are anagrams. First, since the function is not case-sensitive and doesn't care about puctiation, we should do some work on the strings to bring them to the same format: use Lowercase characters and ignore puncutation. The strings become `iamlordvoldemort` and `tommarvoloriddle`. Then, we need to check if the cleaned strings contain the same characters - there are multiple paths we could take here. 
  
  We could sort the strings based on characters' ASCII values, and we expect the sorted strings to be exactly the same for anagrams. 
  
  We could also look for string 1 characters in string 2: for every character in string 1, try to find that character in string 2. This will be a little tricky because of repeating characters: if you are trying to find the first 'o' from `iamlOrdvoldemort`, you should find the 'o' in Tom: `tOmmarvoloriddle`. However, looking for the 'o' in 'lord': `iamlOrdvoldemort`, you should look past the 'o' in 'tom', since you've already used that character. The "unused" 'o' would be the next one: `tommarvOloriddle`. It is doable, but you would need to somehow keep track of the characters you already used from the second string. 
  
  The third approach would be to count each letter from the alphabet. For instance, the first string has 1 letter 'a', and the second string has 1 letter 'a'. There are no 'b's or 'c's in either string. There are 2 letter 'd's in both strings. If you find at least one letter count that doesn't match, the strings are not anagram. The count of letters would match for each letter only for anagrams.


## Write your own test code and Makefile

Write your own test code in a separate file and write a `Makefile` to compile all of your code.  Consult the Makefiles from previous labs, and the lecture notes on Makefiles to guide you in constructing your Makefile.    You may look at test code in previous labs to get an idea of how to write good test code.

You may find it helpful to consult the [slides from 11/09](https://docs.google.com/presentation/d/1-D-LByk2uNYYlDzLMzYJN5qaboc3L_kAtbQzkEsRJZc/edit?usp=sharing), particularly slide 11, that talks about the structure of a `Makefile`.   A few things to remember:
* Makefiles consist of targets, dependencies and recipes (see the slide)
* Remember that each target starts in the leftmost column, and is followed by a colon, and then a (possibly empty) list of dependencies.
* Remember that each "recipe" in the Makefile follows a target line, and must be on a line that starts with a "tab" character, not a sequence of spaces.

## Program to check if an input string is a palindrome

A palindrome is a word (or other sequence of characters) that read the same forwards and backwards (see [Wikipedia article](https://en.wikipedia.org/wiki/Palindrome).  For example: "redivide" is not a palindrome, while "detartrated" is a palindrome.  

Other examples of palindromes include "madam" and "racecar".

When asking whether a sentence is a palindrome, it it traditional to ignore case (`M` vs `m`), punctuation and spacing. Thus, the following sentences are palindromes:

* "Madam, I'm Adam."  (A person named "Adam" introduces himself, politely, to a woman.)
* "Able was I, ere I saw Elba".  (Attributed to the french leader Napolean, who suffered a military defeat at a place called Elba).

Think about what the base case is for a palindrome, and what the recursive step would be that moves you towards that base case.

In `strFuncs.cpp` you are asked to a function to check if a string is a palindrome.  Read the instructions in the file carefully to understand the constraints specified for the function. Ignore case when comparing characters of the string.

```
bool isPalindrome(const string s1);
```

The above function takes a C++ string as input and returns true if an input string is a palindrome and false if it is not. You can do this by checking if the first character equals the last character, and so on. 

You may choose a recursive implementation in this case, although it is not required. If you chose a recursive implementation you may or may not choose to write one or more *helper functions*, where a helper function is one that would be called by `isPalindrome` (or another helper function) to help it compute its result. 

There is a way to do this without a helper function using the `substr` (substring) function appropriately in your recursive calls, but it's fine to come up with any solution.

## Possible approach

Dealing with a "raw" string with punctuation and a combination of upper/lowercase characters is hard. We recommend that you write a function to "clean" the string, and then call the recursive helper function to see if it is a palindrome.

This is a possible code block with a helper function:
```
bool isPalindrome(const string s1) {
 // make a new string that is editable (the one passed in is constant)
 string myString;
 // assign the new string to s1, and "clean" it from punctuation and bring to either uppercase or lowercase format
 
 // call the recursive function
 bool isStringRecursive = isPalindromeRecursive(string myString);
 
 // ...
}

bool isPalindromeRecursive(string s1) {
  // think about the base case: when a string is too short, and we can answer if it is a palindrom very quickly
  
  // think about a string B*******B, where * is some character we don't care about. Can this string be a palindrome? 
  // what about the string B*******E ? Can it be a palindrome? 
  
  // remember that a palinrdome has the same sequence of characters, mirrored in the center. For instance, ABCDEFEDCBA.
  // what is a check you can do in this step of the function? What will your recursive call be?
  
  // to indicate this is a recursive function
  bool recursiveStep = isPalinrdomeRecursive(some substring of s1)
}
```


## Program to recursively find the sum of elements of a linked list

```
int recursiveSum(Node* head);
```
In `recLinkedListFuncs.cpp` you are asked to reimplement the sum function from [lab09](https://ucsb-cs16.github.io/f21/lab/lab09/), this time recursively. If there are no elements of the list, return the value 0;

## Program to recursively find the largest value of a linked list

```
int recursiveLargestValue(Node* head);
```

In recLinkedListFuncs.cpp you are asked to reimplement the largestValue function from [lab09](https://ucsb-cs16.github.io/f21/lab/lab09/) this time recursively. For this function, you may assume that the linked list contains at least one value. 

## Step 3: Turn in your code on Gradescope

Commit and push the latest version of your code on github

Then, submit all the code for this assignment on Gradescope via your github repo. Then visit Gradescope and check that you have a correct score.

* You must check that you have followed these style guidelines:

1. Indentation is neat, consistent and follows good practice (see below)
2. Variable name choice: variables should have sensible names.
	More on indentation: Your code should be indented neatly. Code that is inside braces should be indented, and code that is at the same "level" of nesting inside braces should be indented in a consistent way. Follow the examples from lecture, the sample code, and from the textbook.
3. Your solutions to the problems (e.g. `recursiveSum` and `recursiveLargestValue`) should use recursion. You will not receive credit otherwise (even if Gradescope marks your code as correct).  However, your solution to `isPalindrome` may use either an iterative or recursive approach, as you see fit.




