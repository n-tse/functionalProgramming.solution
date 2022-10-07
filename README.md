# Functional Programming with JavaScript

#### By: Nick Tse

#### A markdown file to prepare for whiteboarding

## Question #1: Turning String to URLs

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