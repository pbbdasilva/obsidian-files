LLVM is a powerful tool which we can use to extract meta-data from our code and transform/analyze it.

Those 2 tools are Passes, which get Intermediate Representation from the source file and parse them. The parsed object is called **Module**. A Module has within it global variables and functions.

A **Function** has basic blocks within it
**Basic Blocks** are a set of instructions to be executed.

The CFG is composed of BasicBlocks, so we need to convert a module into a weighted Graph where the edges are probabilities.
