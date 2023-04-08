link: https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8866714

They formulate a model with a directed graph formed by components of the workload.

#### Local execution

A = (C,D) where C are the components and d_{x,y} is the output data from component x and input data from component y. (essentially edges in graph)

W_c is the workload for the component c (weight in graph)
W_c = V . d_{c-1,c}

and they say V is calculated in [28]

so T_local(c) = W_c / f_u
Where f_u is CPU rate in MIPS


#### Remote execution

They have some similar Time function for remote execution. All those components have some sort of parameter to be defined by the DL model.

#### Optmization problem

Here, they see that the solution problem space is non-convex, then, they choose to generate a bunch of decision solutions for all the components and calculate the best one to train a DL model based on it
They can do it bc the number of components is small enough c <= 10
