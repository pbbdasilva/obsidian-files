
## [MPI w/ RDMA paper](https://arxiv.org/pdf/cs/0310059.pdf)

### Summary
paper is related to how they implemented MPI with Infiniband

### [Infiniband overview](https://network.nvidia.com/pdf/whitepapers/IB_Intro_WP_190.pdf)

Infiniband is a networking connection technology that consists of several switches and processor nodes connected to it. (Called switch-fabric arch). This provides scalability since adding more connections is done by adding new switches and nodes. The communications is packet-based, supporting multicast and unicast.
It also supports DMA operations.

There are two types of packets
- Management packets
- Data packets

Management are responsible for setting up the new connections, handle errors, etc
Data are the ones that nodes send to each other to communicate. Those support up to 4Kb of payload

The switching is made through a LID (Local ID, 16 bytes)

### RDMA operations in Infiniband
RDMA operations are 1-sided and do not incur software overhead at the remote side.
RDMA read and write are the two supported operations. The sender starts the RDMA op by posting RDMA descriptors. Those descriptors have local and remote data segments and the completion can be reported through the Completion Queues from the Infiniband (being transparent to the receiver side at the software layer).

### MPICH2 implementation structure
![[Pasted image 20221206203201.png]]

The MPICH2 biggest concern is portability. To solve they use ADI3 (Abstract Design Interface) to provide a portability layer. From this interface, they implement the CH3 Interface, which implements some ADI3 functionality. Each Channel implements CH3 functionality, according to the purpose of it.

## RDMA Channel
Designed for global shared memory architectures or RDMA capabilities. Contains 5 functions:
- Process Mgmt
- Init
- Finalize
- Put (Write)
- Get (Read)

Put and Get work through a FIFO Pipe, and are non-blocking. 
![[Pasted image 20221206210928.png]]
The design of the operations are done as a ring with 2 pointers
![[Pasted image 20221206210856.png]]

### Basic Design
In a distributed system, there is no shared memory as shown by the previous section. In order to emulate that, they add to the receiver's main memory a shared-buffer and register it to the Infiniband (using the key-registering architecture). Also, there is a memory-buffer in the sender w/ the same size as the one in the receiver. All data is first copied to the buffer and then sent. Both pointers are replicated in both ends of the communication.

In summary, there are 3 buffers, one for each side of the communication and one that is shared and is located within the receiver node. Each operation requires copying/writing data and updating the pointers in all 3 buffers.



### Piggyback optmization
Piggybacking is a technique to try to combine data messages and update/correction messages together in order to minimize the number of messages sent. In their case, they intend to combine the RDMA operations w/ pointer updates.
Previously, the pointer update was done after the write/read to the ring buffer. Now, they combine the data with the new pointer location. In order for the other end be able to translate the message, they attach the message size and two flags (beginning and end flag) for each message. To make the flags distinguable from the message content, they partition the buffer in fixed-size chunks and each message would and each message would use a different one. (I sps this is to make it easier to tell apart different messages).

Also, they delay the updates from the receiver side until there is enough data to be read.

### Pipelining of Large Messages
Large messages require more than one chunk of the buffer. So, they start sending fragments of the message before copying everything to the buffer. (Pipelining)

### Zero-Copy Design
For large messages, instead of using the shared buffer, they create a new register to the infiniband with everything in it (key, data, address, size) and every new zero-copy put would return 0 since no data has been transferred. After the registration, a control packet is sent to the receiver letting him know the key,address and size of the message.
The receiver will fetch this message using an RDMA read operation and will send an ACK control packet to the sender. Afther the sender receives an ACK, he will deregister the buffer used for the message.
However, register operations are expensive in the current Infiniband implementation. To minimize the nr of operations, they started having a registration cache. (buffers are stored there and if it is used again they would not need to register them again) The deregistration only happens if the cache size reaches a certain threshold.

# Questions
- [ ] How a node is able to know the address space of a remote node to send a RDMA operation? (When they register it to the infiniband?)
- [ ] Besides the RDMA operations, the design/logical operations of the ring buffer are the same for MPI P2P comms? Or is it different?
- [ ] How to choose a buffer size
- [ ] "For large messages, the basic scheme leads to two extra memory copies. The first one is from user buffer to the preregistered buffer at the sender side" - this means that small messages the copying is not relevant to account the time? Is this what they mean by this? (Page 6, 1st paragraph)
- [ ] Where would you read about how MPI 1-sided comm should be implemented? (Somewhere with some details)
- [ ] I also have some questions about the source code, I can show you in our next meeting

