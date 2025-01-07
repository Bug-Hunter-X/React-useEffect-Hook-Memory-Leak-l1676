# React useEffect Hook Memory Leak

This example demonstrates a common error in React's `useEffect` hook: creating a memory leak by returning a cleanup function from an effect that doesn't require one. 

The `useEffect` hook with an empty dependency array `[]` is intended to run only once after the component mounts.  Returning a cleanup function in this scenario is unnecessary and causes a memory leak because the cleanup function will never be executed, and the resources it might reference will never be released.

## How to fix

To resolve this, simply remove the returned cleanup function if the effect doesn't manage any resources that need to be cleaned up.

See `bugSolution.js` for a corrected version of the code.