- [x] Understand computing time on OSU
- [x] Read more about OSU
- [ ] See all offloading protocols to calculate the latency between transfer
- [x] Come up with a initial algo\
- [ ] Get code CFG
- [ ] Understand edge probabilities
- [ ] Spread probabilities through graph
- [ ] Understand block frequencies
- [ ] Get block frequencies



#### Initial Algorithm
t_h(w) = min(t_comph(w), t_comph(w/n_h)) + 2 * n_h * t_transf(w/n_h) + n_h * t_d(w/n_h))

t_d(w) = min(t_compd(w), t_compd(w/n_d)) + 2 * n_d * t_transf(w/n_d) + n_d * t_d(w/n_d))


where:
- w is current workload
- t_compd(inf) = inf
- t_transf(inf) = inf
- already visited graphs should not be sent new workload, it should go as a BFS.
- O(V) for computing at first but may be bigger due to pre computations for using infos regarding transf and computing times (could have a init portion cost)