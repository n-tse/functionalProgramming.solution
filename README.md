# Functional Programming with JavaScript

#### By: Nick Tse

#### A markdown file to prepare for whiteboarding

## Question 1: Turning String to URLs

URLs cannot have spaces. Instead, all spaces in a string are replaced with %20. Write an algorithm that replaces all spaces in a string with %20.

You may not use the replace() method or regular expressions to solve this problem. Solve the problem with and without recursion.

Example
Input: "Jasmine Ann Jones"

Output: "Jasmine%20Ann%20Jones"

Clarifying questions:
* can we assume the input will always be a string?
* can we assume there will always be only one space between each word?

function convertToURL (string) {
  let wordArray = string.split(" ");
  let outputString = wordArray[0];
  for (let i = 1; i < wordArray.length; i++) {
    outputString += "%20" + wordArray[i];
  }
  return outputString;
}

function convertToURL (string) {
  let outputString = "";
  for (let i = 0; i < string.length; i++) {
    if (string[i] === " ") {
      outputString += "%20";
    } else {
      outputString += string[i];
    }
  }
  return outputString;
}

## Question 2: Array Deduping

Write an algorithm that removes duplicates from an array. Do not use a function like filter() to solve this. Once you have solved the problem, demonstrate how it can be solved with filter(). Solve the problem with and without recursion.

Example
Input: [7, 9, "hi", 12, "hi", 7, 53]

Output: [7, 9, "hi", 12, 53]

## Question 3: Compressing Strings

Write an algorithm that takes a string with repeated characters and compresses them, using a number to show how many times the repeated character has been compressed. For instance, aaa would be written as 3a. Solve the problem with and without recursion.

Example
Input: "aaabccdddda"

Output: "3ab2c4da"


