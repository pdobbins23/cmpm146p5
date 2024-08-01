# Write-up

Peter Dobbins, Navya Gulati

We are not participating in the competition.

## Explanations

### Individual_DE - generate_children

This function starts by picking a random range of both parent individual's genomes,
specifically the range from 0 to the length of the genome's - 1.
Then, it uses these ranges to perform a crossover between both parent's genome, and
generates two new child individuals.
Each of the children have opposite amounts of each parent's genome, specifically
if the parent genome length is 10, and child 1 has the first 6 of these traits,
then child 2 has the last 4.
This function also calls the mutation function on each of the resulting genomes when
constructing the resulting children individuals.

### Individual_DE - mutate

This function starts by randomly deciding if a mutation should occur.
It does this by generating a random number and checking if it is less than 0.1 (mutation rate)
and if so, it begins determining the mutation.
To determine the mutation, the function first determines which gene in the genome to change.
It does this by randomly selecting an index in the genome.
It then determines what type of tile the gene was, and does different mutations depending on the type.
For 4_block (blocks) and 5_qblock (question blocks), the mutation assigns a 33% chance of offsetting the gene horizontally.
It also assigns a 33% change of offsetting a gene vertically.
For 3_coin (coins), 7_pipe (pipes), and 0_hole (air/gaps), the mutator assigns a 50% change to horizontally or vertically offset the placement.
For 6_stairs (staircases made of blocks), the mutator assigns a 33% chance to horizontal and vertical offsets, and a 33% chance of flipping the direction of the staircase.
For 1_platform (platforms), the mutator assigns a 25% chance to horizontally and vertically offsetting, a 25% chance to alter the width of the platform, and a 25% chance to change the composition block of the platform.
For enemy placements, no mutation is made.

## Changes

We chose to use two selection strategies: rank and tournament selection.
The choice was mostly arbitrary, but we found them to work the best in our tests.
These selection strategies are used by randomly selecting which one to use on each call to generate_successors. Our crossover function has several of its own constraints to try and make the level generation more playable.

## Favorite Levels

NOTE: Just to clarify, our level we provided is beatable, even if it doesn't look like it :D

We picked our two favorite levels because they were fun and also challenging, with awkward platforms and jumps, making the levels more interesting and unique.
They definitely aren't the prettiest levels, but they are fun and entertaining and feel like a puzzle.

Each of the levels were generated until the 30th generation, which took about 3 minutes of computation time.
