Currently, this is just a self-maintained repository for keeping up with the lateset advancement in Privacy-Preserving AI field. It consists of two main parts, the first being the academic papers, the other being the concrete engineering libraries.

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

### Wolverine [link](https://eprint.iacr.org/2020/925.pdf)
> Weng, Chenkai, et al. Wolverine: Fast, Scalable, and Communication-Efficient Zero-Knowledge Proofs for Boolean and Arithmetic Circuits. Cryptology ePrint Archive, Report 2020/925, 2020. https://eprint. iacr. org/2020/925.

This is a latest ZKP system, and it is rather efficient and seems practically usable. The basic idea is just the so-called e “MPC-in-the-head” approach, so it is similar to MPC.

### CryptFlow [link](https://www.microsoft.com/en-us/research/uploads/prod/2019/09/CrypTFlow.pdf)
> Kumar, Nishant, et al. "Cryptflow: Secure tensorflow inference." 2020 IEEE Symposium on Security and Privacy (SP). IEEE, 2020

This is an end-to-end system for tranforming native TensorFlow program to MPC-backed program, done by Microsoft teams. The aim is the same as [LatticeX/Rosetta](https://github.com/LatticeX-Foundation/Rosetta).

### DELPHI [link](https://www.usenix.org/system/files/sec20spring_mishra_prepub.pdf)
> Mishra, Pratyush, et al. "DELPHI: A cryptographic inference service for neural networks." 29th {USENIX} Security Symposium ({USENIX} Security 20). 2020.

Keywords: hybrid approach based on HE (SEAL), GC and OT for outsourcing **Prediction** tasks.


## 2017

### SecureML [link](http://www.ieee-security.org/TC/SP2017/papers/466.pdf)
> Mohassel, Payman, and Yupeng Zhang. "Secureml: A system for scalable privacy-preserving machine learning." 2017 IEEE Symposium on Security and Privacy (SP). IEEE, 2017.

I think this is an important paper in this direction for its concrete implementation based on the share of fixed-point integer. This idea is adopted in many later construction. It also detailed how to use the schema of Offline-Online to speedup. This paper is solid. But, you may pay attention to the truncation algorithm and its analysis in Theorem within this paper, becasue the so-called negeligible error probability is likely to occur when you build a general MPC system.
