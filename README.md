# Project description

The program is implemented in the Naumaxia class. A snapshot of this class represents a game (a lot) of naval battle. So in the main a Naumaxia object is created and from there on it is given control of the program by calling the play method. Prior to this, the necessary values ​​are assigned to certain parameters of the game, such as the time limit for causing damage. These parameters have predefined values, but in this way we have the ability, programmatically, to determine the difficulty of the game. Thus it is possible to implement different levels of difficulty.

Game loop

The play method implements a very simple game loop. In repetition he applies the rules of the game at the beginning of the step, then calls for each ship the methods of movement and operation and finally applies certain rules at the end of the step. All this is in the body of a while that checks if the termination condition of the game is met. As long as it is not satisfied, the loop continues. Ship Class / Inheritance In order to be able to call the movement and operation of each ship without even knowing what type it is, there is a Ship class that each type of ship inherits. Thus, in a std :: vector <Ship *> we keep a table with all the active ships of the game. This vector is a member of the Naumaxia class.

Game map

In addition to the vector with base pointers on ships, there is as a member of the Naumaxia class a two-dimensional table called map, implemented as a vector by vectors representing the game map. Each location on the map is a Cell object. The Cell class contains information about each individual point on the map. In addition to the obvious, {weather, treasure, port} contains a Ship pointer * that shows the ship of this location, if any, otherwise it is NULL. So, we have an alternative way to access the ships, making it much more cost-effective to find the neighboring ships of a ship given its location on the map. Otherwise, that is, if we kept the ships exclusively in a table structure, in order to find out if a place has a ship and what it is, we would have to (search) the whole table.

Ship access to the environment

In the operating method, some ships have to make decisions that do not depend exclusively on themselves, but also on their environment (weather, neighbors, etc.). To enable the implementation of such functions, each Ship object has a Naumaxia type index and the Naumaxia class in turn a series of public methods through which ships can "ask" the necessary information about their environment. χ. std :: vector getFreeNeigbourCells (const int row, const int col) ;.

User interface

The interface is done via the command line. At each step the simulation performs a short Sleep so that the user can pause to ask for information. It also controls any input from the keyboard without having to wait for enter (non-blocking). With the space bar, the flow of the simulation is interrupted and through a menu the user can request information. .
