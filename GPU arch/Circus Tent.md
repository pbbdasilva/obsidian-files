### Transactional Memory
Is an approach to patch up some set of instructions to be a unique transaction. In this way, it is able to cancel the whole transaction if needed. (unit based)

### RDMA (Remote Direct Memory Access)
First, it is important to talk about DMA. DMA is a feature to let hardware access the main memory data without blocking the CPU to wait for the fetch occurs (and they are usuallly busy with other computing tasks). So, this would accelerate memory bandwidth. DMA controller issues interruptions in order to do that when the transaction is done

RDMA is similar do DMA, you have some sort of hardware device that is able to bring memory from one computer to the other without using either OSs. Usually, they do it using the RoCE protocol through ethernet networks.

### iWARP protocol
Also implements RDMA but unlike RoCE, it is based on TCP-like protocols for transmission and uses something called DDP as well. In summary, it seems to be a RoCE but slower (since it accounts for packet loss, traffic congestion, etc)










### to-do
- [ ] Read more about the kernels and results
- [ ] 