# multiplayer-server-game🎲
University project that creates a local server on the University of Toronto main servers and allows users to join and play a simple battle game

## Introduction
For this project, I developed a real-time server for a text-based multiplayer battle game, inspired by Pokemon battles. The game server, written in C and compiled using a makefile, allows multiple players to connect, engage in combat, and interact in real-time. Players join the server, get matched with opponents, and take turns attacking or using special moves until one player wins. This project provided hands-on experience with Unix sockets, process control, and network programming.

## Design and Implementation
The server was implemented using Unix sockets to handle multiple client connections simultaneously. The main function resides in `battle.c`, and the executable is created through a makefile. When a client connects to the server, they enter their name and wait for an opponent. The server manages client connections, matches players for battles, and ensures that multiple matches can occur concurrently without blocking.

To manage the connections and communication, the server uses the `select` function to monitor multiple file descriptors, ensuring it never blocks waiting for input from any single client. When a match begins, each player is assigned random hitpoints and powermoves. Players alternate turns, choosing between regular attacks, which are weak but guaranteed to hit, and powermoves, which are stronger but have a chance to miss. Players can also send messages to their opponents during their turn, enhancing the interactive aspect of the game.

The server handles various scenarios such as clients dropping out mid-game, in which case the remaining player is declared the winner, and they wait for a new opponent. The server uses non-canonical mode (`stty -icanon`) to ensure immediate action on key presses, enhancing the real-time experience of the game.

![image](https://github.com/user-attachments/assets/7e2b098d-715c-438a-a6c0-d5899d5e82de)


## Features and Enhancements
The game server was designed to support various gameplay features and enhancements. Players start each match with randomized hitpoints and a limited number of powermoves, adding an element of unpredictability to each game. The server provides a menu of valid commands before each move, guiding players through their options without revealing their opponent's resources, thus maintaining strategic gameplay.

An additional enhancement implemented is the ability for players to send messages during their turn without consuming their attack opportunity, simulating in-game chat. This feature fosters communication and adds a layer of strategy as players can bluff or mislead their opponents. While our personal team feature was implementing a leaderboard system to keep track of player wins for a single game session.

To ensure robust functionality, the server was tested using the `nc` tool to simulate multiple client connections and various gameplay scenarios. The server's resilience to client drops and its ability to manage multiple simultaneous matches were key aspects of the testing process.

Overall, this project involved designing a complex, interactive networked application that required a deep understanding of Unix sockets, process control, and real-time server management, significantly enhancing my skills in systems programming and network application development.

![image](https://github.com/user-attachments/assets/165d78ab-61c8-4a85-a4a1-c9e1eb5c45b7)

