---
date: 2020-09-13T18:58
tags:
  - haskell
  - pattern
---

# Make illegal states unrepresentable

This pattern is closely related to [[[42c1547a]]] and [[[994b43d6]]] patterns.

## Description

Data types precisely describe the domain allowing to create all valid values and making it impossible to construct invalid values.

## When to use

1. To restrict domain of possible values.
2. When it is feasible to describe the domain precisely.

## Benifits

1. Correctness.
2. Need to write fewer tests.
3. Harder to introduce bugs fo people not knowing the while context of a big picture.

## Costs

1. May require writing custom helper data types and functions.
2. Code can increase in size.
3. Harder to introduce logic changes.

## Usage

Functional Programming features such as Algebraic Data Types, parametric polymorphism and others allow describing the shape of the valid data more precisely to the extend that it is possible to construct any invalid values.

- The function assumes that you won't pass only a single value without the second element.
  
```haskell
handleTwoOptionals :: Maybe a -> Maybe b -> IO ()

-- to

handleTwoOptionals :: Maybe (a, b) -> IO ()
```



```haskell
processTwoLists :: [a] -> [b] -> Int

-- to

processTwoLists :: [(a, b) -> Int
```


```haskell
data Settings = Settings
    { settingsBackend  :: Maybe BackendSettings
    , settingsFrontend :: Maybe FrontendSettings
    }

-- to 

data Settings
    = OnlyBackend BackendSettings
    | OnlyFrontend FrontendSettings
    | BothSettings BackendSettings FrontendSettings
```
