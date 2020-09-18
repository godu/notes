---
date: 2020-09-13T21:24
tags:
  - haskell
  - pattern
---

# Polymorphisation

## Description

Assigning a more general type to a function reduces the chances of writing an incorrect implementation or providing incorrect inputs.

## When to use

1. To reduce risks of using function incorrectly.
2. To use the same function on values of different types.
3. To make illegal states unrepresentable.

## Benefits

1. Need to write fewer tests.
2. Increases code reusability.

## Costs

1. Can make type signatures look more complicated.
2. Reusing polymorphic types in `where` requires enabling the `ScopedTypeVariables` extension, and this might be confusing for beginners.

## Usage

```haskell
maybeConcat :: [Maybe [Int]] -> [Int]
maybeConcat = error ""

maybeConcatList :: [Maybe [a]] -> [a]
maybeConcatList = concat . catMaybes

maybeConcatFunctor :: Monoid m => [Maybe m] -> m
maybeConcatFunctor = mconcat . catMaybes

foldMaybes :: (Foldable a, Monoid m) => a (Maybe m) -> m
foldMaybes = fold . fold
```

```haskell
containsInt :: Int -> [[Int]] -> [[Int]]
containsInt = error ""

containsElem :: Eq a => a -> [[a]] -> [[a]]
containsElem a = filter (elem a)

containsElem_ :: (Foldable f, Eq a) => a -> [f a] -> [f a]
containsElem_ = filter . elem
```

## References

- [Haskell mini-patterns handbook](https://kowainik.github.io/posts/haskell-mini-patterns
