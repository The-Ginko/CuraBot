Project Summary: NanoHealer - Internal Odyssey
This document serves as a comprehensive overview of the NanoHealer: Internal Odyssey project, a 2D canvas-based game created through an iterative, collaborative process. The game's primary goal is to simulate a nanobot (CuraBot) navigating the human body to heal organs and fight pathogens.

The core development of this project was a continuous, long-running chat session. Over time, we expanded the game's features, moving from a basic prototype to a multi-level experience with complex mechanics. A significant portion of our work focused on debugging and refining core systems, especially the audio and the Bezier curve editor.

Game Description & Key Functions
NanoHealer: Internal Odyssey is a top-down, 2D game where players pilot the CuraBot. The game features multiple levels, each representing a different anatomical system, and is characterized by its distinct physics, varied threats, and specialized tools.

Core Game States: The game operates in several states managed by the gameState variable:

'start': The initial state displaying the main menu and debug options.

'playing': The active game state where movement, combat, and resource management occur.

'gameOver': Triggered when the CuraBot runs out of energy or two organs fail.

'debugMenu': An in-game menu for toggling debug features and selecting levels.

'bezierEdit': A specialized mode for manipulating Bezier curves within the game's levels.

Key Functions & Features:

Audio System: A self-contained audio system using the native Web Audio API was implemented to bypass browser security restrictions. It includes functions like ensureAudioContext() (triggered by user gestures like clicking "Start Game") and a robust playSound() function with effects for pulses, sprays, damage, and teleporting.

Player Controls: The CuraBot is controlled via WASD/Arrow Keys. The pause menu can be accessed by pressing the 'P' key.

Physics & Collision: Movement and collisions are handled using mathematical functions for distance checks and clamping to world boundaries. For lung levels, the code includes checks for movement within defined pathways, tissue, and a resistive zone near the pleura.

Level Design: Levels are defined by the levelConfigurations object, which uses a deep copy mechanism to ensure that changes to one level do not affect the others.

Level A & B: Utilize predefined shapes and positions for organs.

Level C & C Beta: Feature a procedurally generated lung structure with pathways (trachea, bronchi) and a seamless outline defined by Bezier curves.

Bezier Curve Editor (bezierEdit mode): This powerful debug tool allows real-time manipulation of the Bezier curve's anchor points (blue dots) and control points (green dots).

Controls: Scrolling (WASD), Zooming (+/-), and a mousedown/mousemove event for dragging points.

Anchor Point Synchronization: The code ensures that when a shared anchor point is moved, the adjacent Bezier segments remain connected, preventing gaps.

Data Export: An "Export Current Bezier" button allows the user to copy the modified curve's data as a JSON string for backup and future integration.

Debugging Tools: The debug menu provides toggles for showOrganLabels and infiniteEnergy, and the "Detailed Lung Outline" toggle activates the Bezier editing mode.

Notes for Future Developers
Context Window Management: This project exists within a very long conversation. To avoid token-related memory issues, future development should consider breaking this project into new, separate chat sessions for major feature additions.

Browser-Specific Issues: The code for the audio system was a direct solution to Content Security Policy (CSP) and browser autoplay issues in sandboxed environments. If external libraries are ever used in the future, be prepared to encounter similar CORS or CSP challenges.

Bezier Editing: The Bezier editor is a functional prototype. While it ensures anchor points move in sync, the next logical step would be to implement an automatic smoothing algorithm that a developer can run on the exported JSON to ensure clean, professional-looking curves without manual, pixel-perfect adjustments.

Deep Copying: The use of JSON.parse(JSON.stringify(levelConfigurations[levelName])) is a critical part of the code. It prevents unintentional state corruption and ensures that every time a level is loaded, it starts with a fresh, clean copy of the original configuration data.

I hope this document provides a clear and useful reference for our work on the NanoHealer project!
