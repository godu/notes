---
date: 2021-05-06T12:59
tags:
  - haskell/extension
---

# FlexibleInstances

Allows you to define instance with type variables.

```haskell
{-# LANGUAGE FlexibleInstances #-}

instance Eq a => C a
```

## References

- [GHC User’s Guide](https://downloads.haskell.org/~ghc/latest/docs/html/users_guide/exts/instances.html)
