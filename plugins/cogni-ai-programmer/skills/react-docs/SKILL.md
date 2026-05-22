---
name: react-docs
description: >-
  React documentation.
  You MUST load this skill when asked to read React documentation, Hooks, Rules of React, or React APIs.
license: MIT
---

# React Docs

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

React is a library for web and native user interfaces.

## When to Use

- When developing applications using React for the web or native platforms.
- When you need documentation on React Hooks (e.g., `useState`, `useEffect`, `useActionState`, `useOptimistic`).
- When you need to look up React APIs, Server Components, Rules of React, or ESLint plugin rules.

## When Not to Use

- When the task requires documentation specific to React Native components or Next.js routing features (use `reactnative-docs` or `nextjs-docs` instead).

## Core Process

1. **Identify the Topic**: Identify the specific React Hook, Component, or API you need details for.
2. **Fetch the Documentation Index**: Read the primary `llms.txt` file from the References section using an available web fetching tool.
3. **Locate Specific Documents**: Find the specific topic's link in the index and fetch its documentation.
4. **Apply Context**: Use the retrieved guidelines, especially focusing on React's Rules and pure components, to complete your implementation safely.

## Core Principles

- **Avoid Hallucination**: React APIs (like Server Components and new Hooks in React 19) change rapidly. Always refer to the official docs to ensure correctness.

## References

- [React Documentation Index](https://react.dev/llms.txt)
  MUST read this index when working with React,
  in order to find documentation for React Hooks, built-in components, APIs, or React Server Components.
  Learn React, API Reference, Hooks, Components, Client APIs, Server APIs, Rules Of React, React Server Components.
