# React useEffect Cleanup Function Not Called on Unmount

This repository demonstrates a common issue with React's `useEffect` hook where the cleanup function is not called when the component unmounts.  The issue arises when a component unmounts before the `useEffect` cleanup function has a chance to execute.

## Problem
The provided code uses `useEffect` with a dependency array that includes `count`. While this is typically correct for managing side effects that depend on the value of `count`, it has an unintended side effect when the component itself is unmounted before the `useEffect` hook's next invocation.

## Solution
The solution uses a flag to track whether the component is still mounted. By checking this flag in the `useEffect` cleanup function, we prevent executing the cleanup function if the component has already been unmounted, thereby solving the memory leak issue. Additionally, using `useRef` makes `isMounted` independent of renders.