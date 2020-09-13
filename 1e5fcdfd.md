---
date: 2020-09-13T22:33
tags:
  - haskell
  - pattern
---

# Recursive go

## Description

Moving recursion over data types into the separate function.

## When to use

1. When recursion reuses some arguments and you want to avoid passing them again.
2. When recursion uses some internal state.
3. To avoir revalidating the same data.

## Benefits

1. Cleaner code.
2. Possible performance improvements.

## Costs

1. More code.
2. Requires to know about and enable the `ScopedTypeVariables` extension.

## Usage

```haskell
sum :: Num a => [a] -> a
sum [] = 0
sum (x:xs) = x + sum xs

-- to

{-# LANGUAGE BangPatterns        #-}
{-# LANGUAGE ScopedTypeVariables #-}

sumGo :: forall a . Num a => [a] -> a
sumGo = go 0
  where
    go :: a -> [a] -> a
    go !acc [] = acc
    go acc (x:xs) = go (acc + x) xs
```
