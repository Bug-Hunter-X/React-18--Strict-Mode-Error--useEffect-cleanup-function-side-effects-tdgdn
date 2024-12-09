# React 18+ Strict Mode and useEffect Cleanup Function Side Effects

This repository demonstrates a common issue encountered when upgrading to React 18 or later: errors caused by side effects within the cleanup function of the `useEffect` hook when Strict Mode is enabled.

## Problem

In React 18+, Strict Mode is enabled by default in development.  It performs additional checks, including double-invoking lifecycle methods.  If your `useEffect` cleanup function contains side effects (like `console.log`), these will be executed twice, potentially leading to unexpected behavior or errors.

## Solution

The solution is to either remove side effects from the cleanup function or conditionally execute them based on the environment (development vs. production).

## Reproduction Steps

1. Clone this repository.
2. Run `npm install`.
3. Run `npm start`.
4. Observe the console logs in the browser's developer tools. You will see the console logs twice (or more) in the console due to Strict Mode, especially noticeable in the unmount process.

## Note

This error typically doesn't manifest in production builds because Strict Mode is usually disabled in production environments. However, ensuring your cleanup functions are free of side effects is a good practice to avoid potential future issues.