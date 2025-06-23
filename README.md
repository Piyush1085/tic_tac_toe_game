# tic_tac_toe_game

# 🎮 Tic Tac Toe Game (Verilog - FPGA)

A digital hardware implementation of the classic **Tic Tac Toe** game built in **Verilog HDL**, playable between a **Human Player** and a **Computer**. The game features move validation, win/draw detection, and a finite state machine (FSM) to control gameplay.

---

## 🧠 Key Concepts

✅ **FSM Control**  
✅ **Synchronous Logic Design**  
✅ **Illegal Move Detection**  
✅ **Winner Detection & Draw Detection**  
✅ **Modular Verilog Design**  

Perfect for FPGA beginners and intermediate learners looking to apply **digital design concepts** in an engaging project.

---

## 🛠️ Features

- 🕹️ **Two-Player Game:** Human vs. Computer
- 🔄 **Resettable Game Logic**
- ❌ **Illegal Move Detection**
- 🧠 **Smart FSM-based Turn Controller**
- 🏁 **Automatic Win/Draw Detection**
- 💡 **Position Register Bank with Enable Decoder**

---

## 🧩 FSM Overview

The game controller uses a **4-state FSM** to manage game progression:

### 🔁 FSM States

| State      | Binary | Description |
|------------|--------|-------------|
| **IDLE**        | `00`   | Waiting for input or after reset |
| **PLAYER**      | `01`   | Human player’s turn (`01` stored in selected cell) |
| **COMPUTER**    | `10`   | Computer’s turn (`10` stored in selected cell) |
| **GAME_OVER**   | `11`   | Game ends due to win or draw |

---

### 🎮 FSM Input Behavior

| Input | Description |
|-------|-------------|
| **Reset** | `1`: Reset game (especially from `GAME_OVER`) <br> `0`: Game active |
| **Play** | `1`: Move from `IDLE` → `PLAYER` (starts human turn) <br> `0`: Stay in `IDLE` |
| **PC** | `1`: In `COMPUTER` state, play move and go to `IDLE` <br> `0`: Stay in `COMPUTER` |
| **Illegal_move** | `1`: Invalid move → return to `IDLE` <br> `0`: Valid → continue game |
| **No_space** | `1`: Board full → go to `GAME_OVER` <br> `0`: Continue game |
| **Win** | `1`: Winning condition met → go to `GAME_OVER` <br> `0`: No winner yet |

---

## 🧩 Module Breakdown

### 1. `tic_tac_toe_game.v` (Top Module)
Integrates all submodules and manages the game.

### 2. `fsm_controller.v`
Implements the 4-state FSM and controls turn logic.

### 3. `position_registers.v`
Stores board state (`pos1` to `pos9`) as 2-bit values.

### 4. `illegal_move_detector.v`
Prevents overwriting already filled positions.

### 5. `nospace_detector.v`
Detects draw condition when no cells are empty.

### 6. `winner_detector.v` & `winner_detect_3.v`
Checks for win patterns and identifies the winner.

### 7. `position_decoder.v`
Decodes position (0–8) into a 16-bit one-hot enable signal.

---

