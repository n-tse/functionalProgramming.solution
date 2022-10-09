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
* will the input ever be empty?

function convertToURL (string) {
  let wordArray = string.split(" ");
  let outputString = wordArray[0];
  for (let i = 1; i < wordArray.length; i++) {
    outputString += "%20" + wordArray[i];
  }
  return outputString;
}

// solution that accounts for all cases
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

function deDupe(array) {
	let set = new Set();
  for (let i = 0; i < array.length; i++) {
		set.add(array[i]);
  }
  console.log(Array.from(set));
}

## Question 3: Compressing Strings

Write an algorithm that takes a string with repeated characters and compresses them, using a number to show how many times the repeated character has been compressed. For instance, aaa would be written as 3a. Solve the problem with and without recursion.

Example
Input: "aaabccdddda"

Output: "3ab2c4da"

function compress(string) {
  let outputString = "";
  let l = 0;
  while (l < string.length) {
    let r = l;
    while (r+1 < string.length && string[r+1] == string[l]) {
      r++;
    }
    let num = r-l+1;
    if (num > 1) outputString += num;
    outputString += string[l];
  }
  return outputString;
}


function compress(string) {
  let outputString = "";
  let currentLetter = string[0];
  let count = 1;
  for (let i = 1; i <= string.length; i++) {
    if (i < string.length && string[i] === currentLetter) {
    	count++;
    } else if (count !== 1) {
    	outputString += count + currentLetter;
      currentLetter = string[i];
      count = 1;
    } else {
    	outputString += currentLetter;
      currentLetter = string[i];
    }
  }
  <!-- if (count === 1) {
  	outputString += currentLetter;
  } else {
  	outputString += count + currentLetter;
  } -->
  console.log(outputString);
}

## Question 4: Checking for Uniqueness

Write an algorithm that determines whether all the elements in a string are unique. You may not convert the string into an array or use array methods to solve this problem. The algorithm should return a boolean.

Example
Input: "hello"

Output: false

Input: "copyright"

Output: true

function isUnique(string) {
	let letterSet = new Set();
	for (let i = 0; i < string.length; i++) {
  	letterSet.add(string[i]);
  }
  console.log(letterSet.size === string.length);
}

## Question 5: Array Sorting

Write an algorithm that sorts an array without using the sort() method. There are many different sorting algorithms — take the time to read about the following:

Quick sort
Merge sort
Heap sort
Insertion sort
Bubble sort
Selection sort
You may implement any of the above algorithms (or your own) to solve the problem — as long as it doesn't use sort().

Example
Input: [9, 2, 7, 12]

Output: [2, 7, 9, 12]

function sort(array) {
  for (let i = 0; i < array.length; i++) {
    for (let j = i + 1; j < array.length; j++) {
      if (array[i] > array[j]) {
        let temp = array[i];
        array[i] = array[j];
        array[j] = temp;
      }
    }
  }
  console.log(array);
}