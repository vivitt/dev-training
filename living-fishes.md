# Living Fish Exercise

In this exercise, the goal is to write a function that calculates the living fish.
The function receives two arrays of the same size: Array A stores the size of the fish, and Array B, their directions.
When two fish meet, only the biggest stays alive. So, the goal is to get the number of fish that will survive.

First create an array to store the size currently living fish and a variable to store the direction of the last fish in the stack.

There are two possible directions 0 and 1.

Initialize the variables created with the values for the firs fish, then iterate trough the rest of fish in the array.

If the fish in the stack is going in the 0 direction, the new fish can’t meet because they’re moving in the same direction.
If the fish in the stack is going in the 1 direction:
  - If the new fish also goes in the 1 direction, they don’t meet.
  - But if the new fish goes in the 0 direction, they meet, and only the biggest survives.

The direction of the survivor will be the last direction stored, but first, it’s necessary to check the current stack to see if there are more collisions.

```

```
