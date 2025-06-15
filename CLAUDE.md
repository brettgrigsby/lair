# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Lair is a 2 player game built with Phaser 3, where 1 player is building a super
villian secret lair and the other player is a secret agent trying to sneak in
and disarm a doomsday device.

The game integrates with the Farcade platform using the Farcade SDK for multiplayer functionality.

## Code Structure

- `index.html`: Contains all the game code, including:
  - HTML structure and CSS styling
  - Game constants and configuration
  - The `GameScene` class with game logic
  - Phaser initialization

## Technical Implementation

- The game is built with Phaser 3 (loaded from CDN)
- Input handling uses Phaser's pointer events (pointerdown, pointermove, pointerup)
- Graphics are drawn programmatically (no image assets)
- The game is responsive and mobile-friendly using Phaser's scaling system
- Integrates Farcade SDK for multiplayer features:
  - Uses `sdk.multiplayer.actions.ready()` when game loads
  - Implements `game_info` event listener to get player information
  - Uses `game_state_updated` event for synchronizing game state between players
  - Calls `sdk.multiplayer.actions.updateGameState()` for game state changes
  - Reports scores with `sdk.multiplayer.actions.gameOver()` when game ends
  - Implements haptic feedback for key game events using `sdk.multiplayer.actions.hapticFeedback()`
  - Validates incoming game states and uses `refuteGameState()` when invalid
