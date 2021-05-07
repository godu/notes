---
date: 2020-09-13T15:41
tags:
  - haskell/extension
---

# DerivingVia

This allow `deriving` a class instance for a type by specifying another type of equal runtime representation.

```haskell
{-# LANGUAGE DerivingVia #-}

newtype Point = Point Int
    deriving Num
        via Int

score :: Point Int
score = Point 2 + Point 3
```

## References

- [Language options -- Glasgow Haskell Compiler](https://downloads.haskell.org/ghc/latest/docs/html/users_guide/glasgow_exts.html#deriving-via)
