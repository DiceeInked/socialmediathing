# Mix

Mix creates a connection and collection relationship.

## What can be Mixed

A Post can be Mixed into:
- A Tonic
- A Barrel

Direct Post-to-Post Mix is not part of the current system.

## Basic behavior

1. The user opens a Post.
2. The user selects Mix.
3. A menu allows the user to choose a Tonic or Barrel.
4. The current Post is added to that collection.
5. The relationship contributes to the Potion Tree network.

Mix is conceptually similar to putting a Post into a folder, but the relationships are also used for discovery.

## Potion Tree relationship

Everything inside a Tonic or Barrel is connected for Potion Tree exploration.

The platform can track which connected Posts users actually select from a given Post. Those click-through relationships can determine which connected Posts are shown first in the Tree viewer.

The current target is to show approximately the top 10 connections from each Post.

## Feed behavior

Mix does not directly modify feed recommendations.

It is primarily a connection and organization mechanism.

## UX principle

Mix should be fast. Users should not manually construct a graph. The Potion Tree is generated automatically from Mix relationships.