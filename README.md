# React useEffect setInterval Memory Leak

This repository demonstrates a common error in React applications: using `setInterval` within the `useEffect` hook without proper cleanup. This leads to memory leaks as the interval continues indefinitely even after the component unmounts.

## Bug

The `bug.js` file contains a React component that uses `setInterval` to update a count every second. However, it lacks the cleanup function required by `useEffect` to stop the interval when the component is unmounted. This results in a memory leak.

## Solution

The `bugSolution.js` file provides the corrected implementation.  The `useEffect` hook now returns a cleanup function that uses `clearInterval` to stop the interval when the component is unmounted, preventing memory leaks.

## How to Reproduce

1. Clone the repository.
2. Open `bug.js` and run the component. Observe the increasing count.
3.  Un-mount the component by either navigating away from the page or updating the code. The memory leak may not be immediately apparent but tools for memory inspection will confirm resource use. 
4. Open `bugSolution.js` and run the component. Observe the increasing count.
5. Un-mount the component. The interval should stop, preventing any memory leaks. 