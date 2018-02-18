---
title: Peculiar Haskell indentation
layout: post
excerpt: >
  An explanation of how Haskell indentation works inside <code>do</code>
  blocks.
category: Haskell
custom_css:
  - syntax.css
---
A Haskell indentation pitfall I've fallen into.
I think it must be common, so I'm describing it here.

The problem is that indentation rules in `do` blocks are not intuitive to me.
For example, the following function is valid Haskell syntax:

```haskell
foo1 :: IO ()
foo1 =
    alloca $ \a ->
    alloca $ \b ->
    alloca $ \c -> do
        poke a (1 :: Int)
        poke b (1 :: Int)
        poke c (1 :: Int)
        return ()
```

In fact, this funnier version is also OK:

```haskell
foo2 :: IO ()
foo2 = alloca $ \a ->
     alloca $ \b ->
   alloca $ \c -> do
       poke a (1 :: Int)
       poke b (1 :: Int)
       poke c (1 :: Int)
       return ()
```

If you add an outer `do` however, things become a little more complicated.
For example, this is the valid version of the functions above with an outer
`do`:

```haskell
foo3 :: IO ()
foo3 = do
    alloca $ \a ->
        alloca $ \b ->
            alloca $ \c -> do
                poke a (1 :: Int)
                poke b (1 :: Int)
                poke c (1 :: Int)
                return ()
```

Notice the extra indentation for each of the `alloca`s.
When I tried to remove these seemingly excessive indents, GHC complained with
the usual `parse error (possibly incorrect indentation or mismatched
brackets)`.

```haskell
foo4 :: IO ()
foo4 = do
    alloca $ \a ->
    alloca $ \b ->
    alloca $ \c -> do
        poke a (1 :: Int)
        poke b (1 :: Int)
        poke c (1 :: Int)
        return ()
```

The truth is, the rules for desugaring `do` blocks are surprisingly simple and
literal.
First, GHC inserts semicolons according to the rules described here:
https://en.wikibooks.org/wiki/Haskell/Indentation#Explicit_characters_in_place_of_indentation.
So it inserts semicolons between the `alloca`s on the same level, so `foo4`
becomes:

```haskell
foo4 :: IO ()
foo4 = do
    { alloca $ \a ->
    ; alloca $ \b ->
    ; alloca $ \c -> do
        { poke a (1 :: Int)
        ; poke b (1 :: Int)
        ; poke c (1 :: Int)
        ; return ()
        }
    }
```

The semicolons after `->` are clearly invalid Haskell syntax, hence the error.

P.S. To compile the functions above, you need to include them in a module and
add proper imports, e.g.

```haskell
module PeculiarIndentation where

import Foreign.Marshal.Alloc (alloca)
import Foreign.Storable      (poke)
```
