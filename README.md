On the table you see a greek alphabet.

\> get lambda

###Get Lambda

Get Lambda is a framework for writing Interactive Fiction in Haskell.
It aims to provide 
 + a good decoupled way of writing IF
 + text-based intermediate protocol for more representation freedom
 + means to implement complex logic in a clean fashion
 + and some more stuff

The engine concept can be described with this listing:

```
module Engine
( Object,
  Trait,
  Relation,
  Action,
) where

import Data.Map (Map)
import qualified Data.Map as Map
import Data.Set (Set)
import qualified Data.Set as Set

-- This module exports kinds, traits, relations, actions definitions

type Key     = String
data Value   = String | Number | Action
type KV      = Map.Map Key Value
type Action  = ([String] -> KV) -> KV

data Object  = Object { id :: String, kind :: String, traits :: Set.Set Trait, state :: KV }
data Trait   = Trait { trait :: String, actions :: Map.Map String Action }

data Relation a b = Relation { relation :: String, graph :: [(a -> b) -> Bool] }

```
