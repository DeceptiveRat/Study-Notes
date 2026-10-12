1. change-cipher protocol
- sent using SSL record protocol
- consists of 1 byte
- causes pending state to become current state - [1]
=> acts as a synchronization marker for using the new keys

reference:
- geeks for geeks - SSL: <https://www.geeksforgeeks.org/computer-networks/secure-socket-layer-ssl/>

notes
[1]: as cryptographic parameters are negotiated, they are in the pending state. Only after receiving the ChangeCipherSpec message do they start using the new negotiated parameters in the pending state as it is changed to current state