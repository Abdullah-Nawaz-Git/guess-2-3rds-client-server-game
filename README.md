# Guess ⅔ of the Average — Multiplayer Client-Server Game

## Project Overview

This project is a Java-based client-server application that implements the "Guess ⅔ of the Average" game, designed to demonstrate key Operating System concepts including:

- **Process Communication:** Using sockets for client-server communication.  
- **Multi-threading:** Managing multiple players and games concurrently with threads and thread pools.  
- **Synchronization:** Ensuring data consistency with locks around critical sections and shared resources.  

The server supports multiple simultaneous games, each with multiple players interacting in real-time.

---

## Game Description

- Each game consists of multiple rounds where each player picks an integer between 0 and 100 within a fixed time frame.  
- The winner of a round is the player whose guess is closest to two-thirds of the average of all guesses. Multiple winners per round are possible if guesses tie.  
- Players start with 5 points and lose 1 point each round they do not win. When a player’s points reach zero, they are eliminated but can continue observing the game.  
- The game ends when only one player remains, who is declared the winner.  
- Special rule: If two players remain and one guesses 0 in the last round, the other player automatically wins.

---

## Features

- Supports up to 6 players per game, with a minimum of 2 to start.  
- Players receive a unique ticket (ID + nickname) for identification and rejoining.  
- Real-time updates after each round include round number, player guesses, points left, round outcomes, and eliminated players.  
- Server maintains a leaderboard of top 5 players by games won, shown at connection.  
- Players can join existing games or create new ones. Games lock once started to prevent late joins.  
- Timeout mechanism to drop inactive players.  
- Thread-safe game state management using synchronization techniques.  

---

## Server Details

- Implemented in Java using socket programming and thread pools.  
- Runs on fixed port `13337`.  
- Separate `Player` and `Game` classes manage client logic and game rules respectively.  
- Tickets uniquely identify players across connections and games.  

---

## How to Run

Compile the server classes:

```bash
javac Server.java Player.java Game.java
