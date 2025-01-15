# COP3330 Programming Assignment 7
Credit to Prof. Christopher Mills
For the final assignment in the course, you will create a limited functionality one-player role playing game. There are several additional requirements that can be met for extra credit, which will apply to this assignment and help offset issues you may have experienced in previous programming assignments. The requirements for the core assignment are as follows:

### Requirement 1
You must have a Party class that acts as a container class for objects of type Character. The container may contain up to five instances. When a character dies, it should be deallocated. When deallocating, all remaining Character instances should be re-sorted to the top of the list and the "current" counter for the container should be decremented such that a user of the container cannot access a deallocated Character.

### Requirement 2
You must have an interactive map that allows the party to move around the map using any keyboard shortcuts you want. Once the player moves, you should re-print your map to show its updated state. You are highly encouraged to use the code located here to build your map.

### Requirement 3
Your dungeon must have four types of "tiles" in addition to blank tiles:
- An 'X' tile that represents the current location of the player's party
- An 'M' tile that represents a group of Monsters that the player's party must fight (see bullet point 4 below for more information).
- A 'T' tile that represents treasure that the party can pick up. The amount of treasure rewarded for stepping on a T tile should be a random number between 1 and 10.

The location of these tiles must be randomly generated and different every time the game is played. The number of M and T tiles must be a randomly generated number between 5 and 10. The size of the dungeon must be at minimum 5x5

### Requirement 4
M tiles must correspond to an instance of a container that includes up to five instances of type Monster. When an encounter is triggered by a player (i.e., the 'X' tile) moving over a group of monsters (i.e., an 'M' tile), a randomly generated number of monsters (up to five) should be placed into a MonsterParty container with randomly generated stats (see bullet point 6 below for more information).

### Requirement 5
The Character class should contain two private data members of type int:

- Health - provides the current health of the character. Once this value falls to <= 0, the character dies and is removed from the party.
- Power - provides the current power of the character. When attacking a Monster, this is the amount to be removed from the Monster's health.
- When a party is generated, character instances should be created with a random amount of health between 80 and 100 and a random power between 4 and 10.
- In addition to being able to move the party, the player should be able to display the current status of all the characters in their party, and this should be implemented with an insertion operator for the Character class.

### Requirement 6
The Monster class should contain three private data members of type int:
- Health - provides the current health of the character. Once this value falls to <= 0, the character dies and is removed from the party.
- Power - provides the current power of the character. When attacking a Monster, this is the amount to be removed from the Monster's health.
- Reward - provides the amount of treasure the party should be rewarded for defeating all of the monsters in the group.
- When a group of monsters is generated, monster instances should be created with a random amount of health between 15 and 35 and a random power between 1 and 6.

### Requirement 7
The Party class should have a Treasure counter that is added to when picking up treasure by stepping on a T tile or when defeating a group of monsters.

### Requirement 8
Combat is triggered when the player's Party moves over an M tile. During combat, monsters may only attack and should attack a randomly chosen character in the player's party. During an attack, there should be a 50% chance the monster's attack misses. If the monster's attack hits, the monster's power should be subtracted from the character's health. Is the monster's attack misses, the character's health should remain unchanged. During combat, the player should be prompted for a target of each character in the party's attack. The character should have a 15% chance of missing the monster. If the character's attack hits, the monster's health should be reduced by the character's power. If the character's attack misses, the monster's health should remain unchanged. The character's party should go first in each encounter, and all of the characters in the party should attack before the group of monsters gets to attack. The player should also have the option of running away from the encounter. If the player runs, they should have a percent chance of success based on the number of monsters in the party. For 5 monsters, there is a 10% chance of success, for 4 monsters there is a 20% chance of success, for three monsters there is a 30% chance of success, for two monsters there is a 40% chance of success, and for 1 monster there is a 50% chance of success. If successful at running away, the player should be returned to the game board, the M tile should be moved elsewhere on the game board, and the group of monsters associated with the original M should be deallocated. If the player steps on the new M tile, a completely different group of monsters should be encountered. Any damage done to the player's Party in the original encounter remains after running away.

### Requirement 9
Winning. The player wins the game when all monsters on the board are defeated and all treasure is picked up.

### Requirement 10
Losing. The player loses the game when all the members of their Party die.

### Requirement 11
You are required to print a message indicating if either of the scenarios in bullet 9 or 10 are encountered in the game.

### BONUS REQUIREMENTS

- (5 points) Add a new type of tile 'R' that corresponds to a trap. If the player's party moves over an 'R' tile, generate a random number 0-99 inclusive. If the number is => 50, the player should be awarded treasure between 0 and 10 to be added to their treasure counter. If the number is <50, all members of the party take between 0 and 10 damage. If a character's health falls to <= 0 as a result, they should be deallocated as if they were defeated in combat.
- (10 points) Add a second layer to the dungeon by creating an 'S' tile that takes the player to the second level of the dungeon (if accessed from the first level) or to the first level (if accessed from the second level). To win the game, the player must clear both levels of the dungeon.
- (5 points) Use inheritance to create a base class from which both the Character and Monster classes derive; use Party for both characters and monsters.
- (5 points) Use inheritance to create two types of Character class: Fighter and Healer. Fighters work as described above, but when selecting a target for a Healer instance, the player should choose one of their characters and their health should be increased by the amount of the healer's power. When generating a party at the beginning of the game, the party should have four fighters and a healer allocated.