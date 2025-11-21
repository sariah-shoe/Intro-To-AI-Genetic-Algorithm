# Intro to AI Assignment 2

This is my implementation for Intro to AI Assignment 2. There were two parts, a GA for a bitstring and a GA for Robby's World.

## Bit Strings (Part 1)
I implemented a genetic algorithm that maximizes the number of ‘1’s in a bit string. Selection is performed using fitness-proportionate selection (roulette-wheel sampling). I used single point crossover, and mutation which is characterized as flipping a bit.

The goal is for the bitstring to be all ones. I used the following fitness function to reach the goal:

f(x) = number of ones in x, where x is a genome of length 20.

Eg. [01001110011001101000] would have a fitness of 9.

## Robby's World (Part 2)

I implemented a genetic algorithm to evolve control strategies for Robby the Robot, as described in Chapter 9 of Complexity: A Guided Tour by
Melanie Mitchell, A control strategy will be represented as a string of characters that code for the following robot actions:

- 0 = MoveNorth
- 1 = MoveSouth
- 2 = MoveEast
- 3 = MoveWest
- 4 = StayPut
- 5 = PickUpCan
- 6 = MoveRandom

Robby’s reward is increased when Robby picks up a soda can, and decreased if Robby hits a wall. The 
GA evolves a good control strategy that maximizes Robby’s average cumulative reward as it collects empty soda
cans for 200 time steps.

The GA maintains a population of genomes representing control strategies. Each genome is a 243-character
string specifying the action that Robby should take for every possible situation it might find itself in. Robby’s
”situation” will be encoded as a 5-character percept string specifying what Robby currently sees in their immediate
vicinity. For example, the string ’WECWC’ means there is a wall to the north, an empty grid cell to the south, a
soda can to the east, another wall to the west, and a soda can in Robby’s own grid cell.

Each percept string corresponds to a unique code number in the range 0-242, which indicates the (0-based) index
number of the situation, for more details on this check out page 132 in the chapter noted above. We will use mainly
use the percept codes in our problem rather than the strings. (e.g. If the percept code is 240, Robby will perform
the action described by the 240th gene of the genome)

For example, if the genome were all 0’s, in any given situation the Robot would move north.

I used rank selection, single point crossover, and mutation which is characterized
as randomly replacing one or more characters in the string.
