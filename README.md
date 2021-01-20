Currently, this is mainly a personal repository for keeping up with the lateset advancement in Privacy-Preserving AI field. It consists of two main parts, the first being the academic papers, the other being the concrete engineering libraries.

> Some comments on these work are just personal, and maybe incorrect. All the selected work here still have my highest appreciation.

> **Acronyms Notes**
>
> OT: Oblivious Transfer
>
> GC: Garbled Circuit
>
> HE: Homomorphic Encryption
>
> MPC: Multi-Party Compuation
>
> SS: Secret-sharing
>
> ZKP: Zero Knowledge Proof


# Academic Papers

## 2020

### CrypTFlow2 [link](https://eprint.iacr.org/2020/1002.pdf)
> Rathee, Deevashwer, Mayank Rathee, Nishant Kumar, Nishanth Chandran, Divya Gupta, Aseem Rastogi, and Rahul Sharma. "CrypTFlow2: Practical 2-party secure inference." In Proceedings of the 2020 ACM SIGSAC Conference on Computer and Communications Security, pp. 325-342. 2020.

A updated version of CrypTFlow.

### EdaBits [link](https://eprint.iacr.org/2020/338.pdf)
> Escudero, Daniel, Satrajit Ghosh, Marcel Keller, Rahul Rachuri, and Peter Scholl. "Improved Primitives for MPC over Mixed Arithmetic-Binary Circuits." IACR Cryptol. ePrint Arch. 2020 (2020): 338.

A new efficient conversion between arithmatic and boolean number representation is proposed, and it seems very generic and efficient.

### ABY2.0 [link](https://eprint.iacr.org/2020/1225.pdf)
> Patra, Arpita, et al. "ABY2. 0: Improved mixed-protocol secure two-party computation." USENIX Security. Vol. 21. 2020.

This is similar to their prior work BLAZE and ASTRA.

### Wolverine [link](https://eprint.iacr.org/2020/925.pdf)
> Weng, Chenkai, et al. Wolverine: Fast, Scalable, and Communication-Efficient Zero-Knowledge Proofs for Boolean and Arithmetic Circuits. Cryptology ePrint Archive, Report 2020/925, 2020. https://eprint. iacr. org/2020/925.

This is a latest ZKP system, and it is rather efficient and seems practically usable. The basic idea is just the so-called e “MPC-in-the-head” approach, so it is similar to MPC.

### CrypTFlow [link](https://www.microsoft.com/en-us/research/uploads/prod/2019/09/CrypTFlow.pdf)
> Kumar, Nishant, et al. "Cryptflow: Secure tensorflow inference." 2020 IEEE Symposium on Security and Privacy (SP). IEEE, 2020

This is an end-to-end system for tranforming native TensorFlow program to MPC-backed program, done by Microsoft teams. The aim is the same as [LatticeX/Rosetta](https://github.com/LatticeX-Foundation/Rosetta).

### DELPHI [link](https://www.usenix.org/system/files/sec20spring_mishra_prepub.pdf)
> Mishra, Pratyush, et al. "DELPHI: A cryptographic inference service for neural networks." 29th {USENIX} Security Symposium ({USENIX} Security 20). 2020.

Keywords: hybrid approach based on HE (SEAL), GC and OT for outsourcing **Prediction** tasks.

## 2019 

## QUOTIENT [link](https://arxiv.org/pdf/1907.03372.pdf)
> Agrawal, Nitin, Ali Shahin Shamsabadi, Matt J. Kusner, and Adrià Gascón. "QUOTIENT: two-party secure neural network training and prediction." In Proceedings of the 2019 ACM SIGSAC Conference on Computer and Communications Security, pp. 1231-1247. 2019.


## 2017

### SecureML [link](http://www.ieee-security.org/TC/SP2017/papers/466.pdf)
> Mohassel, Payman, and Yupeng Zhang. "Secureml: A system for scalable privacy-preserving machine learning." 2017 IEEE Symposium on Security and Privacy (SP). IEEE, 2017.

I think this is an important paper in this direction for its concrete implementation based on the share of fixed-point integer. This idea is adopted in many later construction. It also detailed how to use the schema of Offline-Online to speedup. This paper is solid. But, you may pay attention to the truncation algorithm and its analysis in Theorem within this paper, becasue the so-called negeligible error probability is likely to occur when you build a general MPC system.

### EzPC [link](https://eprint.iacr.org/2017/1109.pdf)
> Chandran, Nishanth, Divya Gupta, Aseem Rastogi, Rahul Sharma, and Shardul Tripathi. "EzPC: programmable, efficient, and scalable secure two-party computation for machine learning." ePrint Report 1109 (2017).

The main contribution is to present a new C-dialect language and its compiler to convert the source code to MPC-enabled backend runable executable file. In my opinion, this is a good try at the direction of providing easy-to-use interface for developer using MPC. This is an open source [project](https://github.com/mpc-msri/EzPC), and the team has made some following research, such as Cryptflow. "In summary, EzPC raises the level of abstraction for the programmer, and generates efficient 2PC protocols automatically, while its metatheory provides strong correctness and security guarantees."
> * Automatic chose whether to use arithmatic circuit or boolean circuit. 
> * ABY backend is used only for now.
> * The major part, section 4, is about the compiler design to ensure both correctness and security.



