# Chess - Planning the development of pieces

## Overview

This project uses the `unified-planning` library and FOL to model a chess piece development problem.

The setting is considering only the white pieces on an 8x8 chessboard with no opponent.

The idea of the project is to eventually have a PDDL that can be used to plan the development of the white pieces.

## Features
- **Board Representation**:
  - Files (`a`-`h`) and ranks (`s`-`z`, mapped to 1-8).
  - Types: `Piece` (super type), `P` (Pawn), `R` (Rook), `N` (Knight), `B` (Bishop), `K` (King), `Q` (Queen).
  - Objects for each file and rank representing the chess board itself.
- **Fluents**:
  - `file_idx`, `rank_idx`: Map files and ranks to indices (1-8).
  - `at(piece, file, rank)`: Tracks piece positions.
  - `occupied(file, rank)`, `free(file, rank)`: Tracks square occupancy.
  - `moved(piece)`: Tracks if a piece has moved at least once.
- **Actions**:
  - `move_pawn_up_by_1`: Moves a pawn up one rank (same file), if not on rank 8 and target is free.
  - `move_rook_horizontally`, `move_rook_vertically`: Moves a rook along a file or rank, checking clear paths.
  - `move_knight`: Moves a knight in an L-shape, checking target is free.
  - `move_bishop`: Moves a bishop diagonally, checking clear paths.
- **Initial State**:
  - Pawns on `a2`-`h2` (rank `t`).
  - Rooks on `a1`, `h1` (rank `s`).
  - Knights on `b1`, `g1` (rank `s`).
  - Bishops on `c1`, `f1` (rank `s`).
- **Goal**:
  - The idea of the project is to eventually have a PDDL that can be used to plan the development of the white pieces.
  - On a board where black is absent, so as to go through all possible plans that achieve the state where all pieces are considered developed.
  - For starters, simple test goals have been defined, such as moving the e pawn up to e6.

## TODOs
- **Next steps**:
  - Add movement action(s) and object for the Queen.
  - Add movement action(s) and object for the King.
- **Issues**:
  - Find an engine that is fully compatible with the problem setup.
  - So far all engines tested has at least one missing feature or technical problem.
