Currently, this is just a self-maintained repository for keeping up with the lateset advancement in Privacy-Preserving AI field. It consists of two main parts, the first being the academic papers, the other being the concrete engineering libraries.

> Some comments on these work are just personal, and maybe incorrect. All the selected work here still have my highest appreciation.

> * Acronyms Notes
OT: Oblivious Transfer
GC: Garbled Circuit
MPC: Multi-Party Compuation
SS: Secret-sharing



## Academic Papers

### CryptFlow [link](https://www.microsoft.com/en-us/research/uploads/prod/2019/09/CrypTFlow.pdf)
> Kumar, Nishant, et al. "Cryptflow: Secure tensorflow inference." 2020 IEEE Symposium on Security and Privacy (SP). IEEE, 2020

This is an end-to-end system for tranforming native TensorFlow program to MPC-backed program, done by Microsoft teams. The aim is the same as [LatticeX/Rosetta](https://github.com/LatticeX-Foundation/Rosetta).

### DELPHI [link](https://www.usenix.org/system/files/sec20spring_mishra_prepub.pdf)
> Mishra, Pratyush, et al. "DELPHI: A cryptographic inference service for neural networks." 29th {USENIX} Security Symposium ({USENIX} Security 20). 2020.

Keywords: based on homomorphic encryption (SEAL), Garbled circuit and OT for outsourcing **Prediction** tasks.
