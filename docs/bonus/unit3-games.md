# Bonus Unit 3 — Agents in Games (Pokémon)

## Overview

This bonus unit applies agent techniques to a game environment — specifically a **Pokémon battle simulator**. It is a fun way to test agent decision-making in a fully observable, turn-based setting.

## Why games?

Games provide:

- **Clear win/lose signal** — easy to evaluate agent performance
- **Structured action space** — finite set of valid moves
- **Reproducible environments** — easier to debug
- **No real-world consequences** — safe to experiment

## The Pokémon environment

The course uses [Pokémon Showdown](https://pokemonshowdown.com/) via the `poke-env` library:

```bash
pip install poke-env
```

```python
from poke_env.player import Player

class MyAgent(Player):
    def choose_move(self, battle):
        # Use the LLM to decide which move to make
        context = self._build_context(battle)
        move_name = self._llm_decide(context)
        return self.create_order(battle.available_moves[0])  # simplified
```

## Agent design considerations

- **State representation** — how to describe the battle state to the LLM
- **Action grounding** — ensuring the LLM picks a *valid* move
- **Memory** — tracking HP, status conditions, and previous turns
- **Strategy** — type matchups, priority moves, switching

## Notes & experiments

_Add your game agent notes, battle logs and win-rate experiments here._
