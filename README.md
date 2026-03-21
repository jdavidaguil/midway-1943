# Midway 1943: Pacific Inferno

A retro, arcade-style vertical shooter built with plain HTML5 Canvas and vanilla JavaScript.

The game is inspired by classic 1940s-themed scrolling shooters and runs directly in the browser with no build step or external dependencies.

## Features

- Smooth vertical scrolling ocean background with wave and foam effects.
- Sprite-based player, enemies, bullets, explosions, and power-ups.
- Multiple enemy archetypes (planes, boats, cruisers, heavy ships).
- Wave-based difficulty progression that ramps over time.
- Auto-fire combat with firepower upgrades.
- Player resources and survivability systems: HP, lives, fuel, temporary invincibility.
- Procedural sound effects generated through Web Audio API.
- Title, pause, and game over screens.

## Controls

- Move: Arrow keys or WASD
- Start / restart: Enter
- Pause / resume: Space

Combat uses auto-fire while the player is active.

## Gameplay Systems

### Player

- Starts with 3 lives and 3 HP.
- Has a fuel tank that drains over time.
- When fuel reaches 0, movement speed is reduced.
- Gains temporary invincibility after respawn or when hit.

### Enemies

- Enemies spawn continuously based on wave progression.
- Later waves introduce tougher and more varied enemy types.
- Some enemies fire aimed projectiles toward the player.
- Tankier enemies render health bars.

### Power-ups

- P: increases firepower up to level 3.
- POW: triggers a bomb that clears enemies and enemy bullets.
- FUEL: restores fuel.

### Scoring and Progression

- Destroying enemies increases score.
- Every 30 seconds the wave increases.
- Spawn rate becomes more aggressive as wave number grows.

## Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript (single-file game loop)
- Canvas 2D API
- Web Audio API

## Project Structure

```text
.
|-- index.html
|-- README.md
`-- resources/
	|-- sprites.png
	|-- sprites.jpg
	|-- sheet_preview.png
	|-- quad_0.png ... quad_3.png
	`-- crop_blob*.png
```

## Run Locally

You can run the game in either of these ways.

### Option 1: Open directly

Open index.html in your browser.

### Option 2: Serve with a local HTTP server (recommended)

From the project root:

```bash
python3 -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

## Notes on Assets

- The game currently loads the sprite sheet from resources/sprites.png.
- The sprite coordinates are defined in the JavaScript SPRITES map inside index.html.
- Additional files in resources are intermediate crops and previews used during sprite extraction/iteration.

## Core Architecture

The game is implemented as a single script with these major subsystems:

- Sprite and rendering utilities
- Scrolling background generator
- Input manager
- Audio and SFX helpers
- Entity arrays for bullets, enemies, particles, explosions, and power-ups
- Collision detection and combat resolution
- Wave and spawn manager
- HUD and overlay screens
- State machine for title, playing, paused, and game over
- requestAnimationFrame-based main loop

## Browser Compatibility

Tested design assumptions are for modern desktop browsers with Canvas and Web Audio support.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Future Improvements

- Split game logic into modules for maintainability.
- Add boss encounters and scripted stage events.
- Add mobile/touch controls.
- Add persistent high scores.
- Add options menu for audio and difficulty.