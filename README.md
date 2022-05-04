# RuneScape-Private-Server-v550

## Introduction
This repository is a project I worked on a few years ago. The popular game called [RuneScape](https://runescape.com) by [Jagex](https://jagex.com) was a childhood favourite of mine and with various updates the appeal of the oldstyle game dimished.

As a result, I decided to entirely refactor their **Obfuscated** Java client and create a working backend server that would work.
This project is now at a playable state and most of the major game components have been fully identified and the server is at a position where we only need to re-implement the games content (i.e. the gameplay). 

A screen of the game running:
<img src="https://user-images.githubusercontent.com/76599223/166706272-2ae3bc97-04b5-4dfe-8243-16a60b6607ec.png" width="150" height="auto">

## Current Features
* Almost Full player updating and some NPC updating
* Update server for on-demand file retrival
* Most packet sizes have been identified
* Game clicking (buttons, npcs, objects etc)
* Item on item, item on player, item on object
* Wearing items - Most items go in correct slots
* Almost all item, object and NPC examinations
* Item definitions such as prices, bonuses, alch values, item-tradable, item-members, weight and a few others
* Weapon speeds
* Walking, talking etc

### Needs fixing
Walking in game is based on the A* Path Finding Algorithm. Though this works, there is a strange but where the path finder does not work when the players localX or localY is over 400. Computation takes too long causing the server to crash. Though, this won't be noticable as the locations in game are "dead content zones".

# Running the game
The project uses the Maven build system and should just work. The original unmodified client is used to launch the game. We use ASM to change the address the client connects to dynamically at runtime. See the `data/www/550.jar` for the client.

The following third-party libraries are used:
* JUnit
* SLF4J
* APIviz
* ObjectWeb ASM
* Netty 4
* MySQL Connector/J

## Acknowledgements
[Graham Edgecombe](https://github.com/grahamedgecombe) for providing a server base to work from. This includes pre-configuring netty and including all the utitlities to read the raw packets sent by the client. 

[Leanbow](https://github.com/leanbow) For helping me identify packets and refactoring the onfuscated client.
