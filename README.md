# FP Server Overview

The server consists of many parts but the two biggest are the game server and web server.
Written in C# using .NET 9

### Game Server

**Notes**
- Loads game data from disk which are stored in XMLs so it can be easily modified by people.
- Initializes worlds which contain thousands of objects and enemies.
- Handles networking using TCP to make sure no packets are missed 
- Tick system to keep worlds, players, objects and enemies updated.
- Behaviour system to allow for creation of complex patterns for any enemy.
- Main game logic runs on the main thread while networking is on another.

### Web Server
A simple HTTP Server. 

**Notes**
- Runs on a separate thread from Game Server
- Handles common requests such as registering, logging in etc. 

### Shared Library
A library with data structures and methods that multiple projects might want to use.
Currently using Redis for the database.

**Notes**
- Such as database models (Account Model, Character Model, Market Model etc).
- Byte readers and writers to allow easy storage and transfer of byte arrays.
- Redis PUB/SUB methods to allow for easy communications between servers connected to the database.

### DISCLAIMER

- This repo is private can showcase upon request