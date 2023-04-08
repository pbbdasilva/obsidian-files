[link](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9835539) to paper

[22] is a compiler cost function w/o accouting number of operations for computing time

### Summary
They predict the time needed for a kernel to be executed from the gpu to run combining features that they say it is extracted by the compiler
They do it using supervised learning and code tons of different kernels and some variations for each one to feed the dataset

### Worth mentioning
They have to set some constraints related to number of for loops (common to openMP programs since they are directive-based).
