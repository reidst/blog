---
layout: post
author: "Katherine Reid"
title:  "Functional Programming & Sokoban"
date:   2024-02-19 21:53:00 -0600
categories: "365"
---

Hello again from a new semester! The only CSCI class I'm currently taking is [CSCI 365 Functional Programming](https://hendrix-cs.github.io/csci365/), but I'm having a blast with it. We're learning how to use the Haskell programming language and associated tools (via the [`ghcup`](https://haskell.org/ghcup/) toolchain), and this month we have been tasked to create a basic text-based game. We haven't talked about IO or other side-effects yet, so our games are all built upon a template that handles IO and RNG, but outside of that constraint it's complete freedom.

I decided to make a sokoban engine; I was inspired by David W. Skinner's [Microban](https://sokobanonline.com/play/web-archive/david-w-skinner/microban) level pack and I thought it would be a good use of functional programming and a good exercise for learning Haskell. For a brief introduction to sokoban, it is a puzzle game in which the user can move the player orthogonally around a grid of play and push boxes. The level is complete when all the boxes are placed on the special goal tiles. The game doesn't require any randomness, so the entertainment value comes entirely from the hardcoded levels (my stretch goal is to find a way to import levels from a text file or directory of files, so that the user could add their own levels), but in my experience a lot of puzzling fun can come from a few well-crafted sokoban levels.

The biggest challenge I faced was deciding what data structure to use to store level data. In the prototype I created in Python, I stored levels as a player location alongside lists of walls, goals, and boxes, all wrapped in a tuple. In Haskell types, this would be `(Vec2, [Vec2], [Vec2], [Vec2]) where Vec2 = (Int, Int)`. It worked fine for a prototype, but I knew it wasn't a robust solution: it has very little protection against illegal state. Specifically, the state invariants I needed were as follows (in order of importance):

1. There must be exactly one player.
2. The positions of all walls, boxes, and the player must be unique.
3. The positions of all walls and goals must be unique.
4. The positions of walls and goals must remain constant.
5. There must be at least as many boxes as goals.

The Python solution ensured invariant 1 and made 4 and 5 easy to hold but gave no protection against incompatible tiles existing at the same location. This wasn't too difficult to hold, but I really wanted to see how many invariants I could get for free from the right type system. The solution to ensure 1, 3, and (mostly) 2 was to store all non-player data in a mapping of positions to tiles, then to store the player position alongside it, thusly:

```haskell
data Tile where
  Wall  ::         Tile
  Box   :: Bool -> Tile -- Bool: is this tile a goal tile?
  Empty :: Bool -> Tile
type Vec2  = (Int, Int)
type Level = (Map Vec2 Tile, Vec2)
--            ^ tile data    ^ player
```

I currently have a working implementation using this structure. It ensures invariant 1, just as the original solution does, and thanks to algebraic data types and maps, it ensures 3 as well as most of 2. However, it still allows for the player to exist in the same space as a wall or box, and it gives no ensurance for 4. Despite these flaws, however, I ultimately settled with this solution for two reasons: efficient usage and practical level creation.

The point of sokoban is to move things, so efficient reading and writing of the data is just as important as the data's structure. I could solve the player position problem by encoding it as part of the `Tile` data, but (besides losing invariant 1) that would make player movement take time proportional to the tile count - a terrible tradeoff. Secondly, since these levels are parsed from a text-based representation of the initial state, many of the state rules can be imposed on the level creator rather than the engine. If I were to create a procedural level generator then it would be more important for such rules to be kept in-engine, but it takes very little work for a human to ensure there is only one player, there aren't more goals than boxes, etc. Technically, it is also important that the player is bounded on all sides by walls and that the level is solvable, but it would be absurd to consider such constraints to be the responsibility of the data structure.

Fundamentally, the job of a data structure is to create an efficient abstraction for reading and writing data - in this case, moving the player, printing the board, and checking if the level is complete - and not to prevent malicious levels from being created. In my feverish excitement over algebraic data types, I forgot this simple truth. Forgive me, professors.

...

All that aside, my sokoban game is almost finished! As long as I don't trap myself in code review hell, I just need to add a level select screen and a restart button and it's good for a 1.0 release. I'll update this article with a link to the github page once it's finished.
