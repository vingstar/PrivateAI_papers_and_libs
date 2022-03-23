Currently, this is mainly a personal repository for keeping up with the lateset advancement in Privacy-Preserving AI field. It consists of two main parts, the first being the academic papers, the other being the concrete engineering libraries.

> I **ONLY** list here the papers I have read, so this is far from being complete.
> 
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
> 
> FL: Federated Learning


# Academic Papers

## 2021

### Cheetah [link](- https://eprint.iacr.org/2022/207.pdf)
> Huang, Zhicong, Wen-jie Lu, Cheng Hong, and Jiansheng Ding. "Cheetah: Lean and Fast Secure Two-Party Deep Neural Network Inference." Cryptology ePrint Archive (2022).

This paper follows the same story line of CrypTFlow2, and improve on two main aspects. First, An encoding-decoding scheme is proposed to map the matrix and vector values to HE polynomials, this can greatly reduce the HE operations cost. On the other hand, it replaces the random OT primitives with the latest one, VOLE-style silent OT, and it also use a simple version of truncation that is precise enough for CNN from the practical aspect.

We can see that it can indeed improve the total secure inference performance if we can combine both MPC and HE in a clever and careful way. But these tricks are still hard to be applied to secure training process, since some assumptions are not met, such as the parameters' gradients can not be only handled by one party during training.

### Secrecy [link](https://arxiv.org/pdf/2102.01048.pdf)
> Liagouris, John, Vasiliki Kalavri, Muhammad Faisal, and Mayank Varia. "Secrecy: Secure collaborative analytics on secret-shared data." arXiv preprint arXiv:2102.01048 (2021).

This paper provides a solution to secure multi-party data analytics. The highlight is that this solution is based on the already secret-shared data rather than the plaintext data held by different party. This means that some optimizations base on preprocessing on plaintext input data, such as these proposed by [Conclave](https://arxiv.org/pdf/1902.06288.pdf), can not be used.



### Cerebro [link](https://www.usenix.org/conference/usenixsecurity21/presentation/zheng) 
> Zheng, Wenting, Ryan Deng, Weikeng Chen, Raluca Ada Popa, Aurojit Panda, and Ion Stoica. "Cerebro: A platform for multi-party cryptographic collaborative learning." In 30th {USENIX} Security Symposium ({USENIX} Security 21). 2021.
> With code: https://github:com/mc2-project/cerebro

This paper provides a end-to-end platform for private AI. It consists of several components for the whole process, a `easy-to-use` DSL that you can use to express your ML task, a compiler whose frontend can generate the logical MPC-backed computation corresponding to the DSL script, and the backend part of it can even further optimize the deployment of some nodes based on network conditions of every nodes. You can also specific when and how the resulting plaintext model result can be exposed to some parties by `compute policies`. At last, after the computation, you can start a audit process to check who had posied the learned model with malicous input data, which can be achived by some cryptographic commitment scheme. With such `cryptographic audit` ability, it can make the participants accountable.

In my opinion, this platform seems a litte too ambitious. Thw key takeaways from what I've learned is some optimization tricks used in compiling from the DSL to the effcient MPC computation, which are also appliable to other generic systems.


### XORBoost [link](https://eprint.iacr.org/2021/432)
> Kevin Deforth and Marc Desgroseilliers and Nicolas Gama and Mariya Georgieva and Dimitar Jetchev and Marius Vuille. XORBoost: Tree Boosting in the Multiparty Computation Setting. https://eprint.iacr.org/2021/432

This paper describe how to train and predict with XGBoost algorothm in a secure way, and its solution is wholly based on MPC. The main idea is to `express` the candidate split feature and its threshold by permutated binary `bucket vector` utilizing the permutaion protcol in their prior work about Manticore protocol. The training instance subset corresponding to each internal node is also presented by binary `instance vector`, and updated by element-wise MUL of this `instance vector` and `selector vector`, which can be derived from permutated `bucket vector`.

The performance seems good for ensemble trees with small depth.

The solution proposed by this paper can handle both Vertical and horizontal partitioned datasets. In pratice, however, the dataset is ofen vertical partitioned. So if we can utilize the chracteristic of VFL, that the WHOLE data vector of a specific FEATURE is held by ONE party, some computation can be optimized further.  


### QuickSilver [link](https://eprint.iacr.org/2021/076.pdf)
> Kang Yang and Pratik Sarkar and Chenkai Weng and Xiao Wang. QuickSilver: Efficient and Affordable Zero-Knowledge Proofs for Circuits and Polynomials over Any Field. https://eprint.iacr.org/2021/076

A more practical ZKP protocol with many concrete improvements based on [Wolverine](https://eprint.iacr.org/2020/925.pdf)

## 2020

### CrypTFlow2 [link](https://eprint.iacr.org/2020/1002.pdf)
> Rathee, Deevashwer, Mayank Rathee, Nishant Kumar, Nishanth Chandran, Divya Gupta, Aseem Rastogi, and Rahul Sharma. "CrypTFlow2: Practical 2-party secure inference." In Proceedings of the 2020 ACM SIGSAC Conference on Computer and Communications Security, pp. 325-342. 2020.

A updated version of CrypTFlow. Mainly, in 2PC semi-honest model, A protocol for comparsion and a protocol for dividion without precision loss are proposed. The two protocols seem quite hand-tuned, but with concrete improvement in communication complexity.

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
But the compiler's output is still vallina C++ program, unlike Rosetta. So this may limit its future extension for more sophisticated computation.

### DELPHI [link](https://www.usenix.org/system/files/sec20spring_mishra_prepub.pdf)
> Mishra, Pratyush, et al. "DELPHI: A cryptographic inference service for neural networks." 29th {USENIX} Security Symposium ({USENIX} Security 20). 2020.

Keywords: hybrid approach based on HE (SEAL), GC and OT for outsourcing **Prediction** tasks.

## 2019 

### QUOTIENT [link](https://arxiv.org/pdf/1907.03372.pdf)
> Agrawal, Nitin, Ali Shahin Shamsabadi, Matt J. Kusner, and Adrià Gascón. "QUOTIENT: two-party secure neural network training and prediction." In Proceedings of the 2019 ACM SIGSAC Conference on Computer and Communications Security, pp. 1231-1247. 2019.

### OTEHRS 

#### <a name="PPDTTPAMS"></a> Privacy-Preserving Decision Tree Training and Prediction against Malicious Server. [link](https://eprint.iacr.org/2019/1282)
> Akavia, Adi, Max Leibovich, Yehezkel S. Resheff, Roey Ron, Moni Shahar, and Margarita Vald. "Privacy-Preserving Decision Tree Training and Prediction against Malicious Server." IACR Cryptol. ePrint Arch. 2019 (2019): 1282. 

This paper propose a HE-based secure decision tree training algorithm.  

#### <a name="SecureBoost"></a>SecureBoost [link](https://arxiv.org/abs/1901.08755)
> Cheng, Kewei, Tao Fan, Yilun Jin, Yang Liu, Tianjian Chen, and Qiang Yang. "Secureboost: A lossless federated learning framework." arXiv preprint arXiv:1901.08755 (2019).

This paper propose a **FL**-based solution to train a gradient boosting decision tree model securely. This solution seems elegent, though some security concerns remains since it is based one the efficient FL approach rather than based on cryptography. 


## 2017

### SecureML [link](http://www.ieee-security.org/TC/SP2017/papers/466.pdf)
> Mohassel, Payman, and Yupeng Zhang. "Secureml: A system for scalable privacy-preserving machine learning." 2017 IEEE Symposium on Security and Privacy (SP). IEEE, 2017.

I think this is an important paper in this direction for its concrete implementation based on the share of fixed-point integer. This idea is adopted in many later construction. It also detailed how to use the schema of Offline-Online to speedup. This paper is solid. But, you may pay attention to the truncation algorithm and its analysis in Theorem within this paper, becasue the so-called negeligible error probability is likely to occur when you build a general MPC system.

### EzPC [link](https://eprint.iacr.org/2017/1109.pdf)
> Chandran, Nishanth, Divya Gupta, Aseem Rastogi, Rahul Sharma, and Shardul Tripathi. "EzPC: programmable, efficient, and scalable secure two-party computation for machine learning." ePrint Report 1109 (2017).

The main contribution is to present a new C-dialect language and its compiler to convert the source code to MPC-enabled backend runable executable file. In my opinion, this is a good try at the direction of providing easy-to-use interface for developer using MPC. This is an open source [project](https://github.com/mpc-msri/EzPC), and the team has made some following research, such as Cryptflow. "In summary, EzPC raises the level of abstraction for the programmer, and generates efficient 2PC protocols automatically, while its metatheory provides strong correctness and security guarantees."
> * Automatic chose whether to use arithmatic circuit or boolean circuit.  But the rules are very simple and heuristic: use arithmatic gates for multiplication operation.
> * ABY backend is used only for now.
> * The major part, section 4, is about the compiler design to ensure both correctness and security.
> * The so-called code partition is also very simple, just by resharing the output with new random inputs from Alice. 


# Special Topics

## Privacy-preserving Tree-based Models

### Outsourcing Computation
> In this scene, clients have ALL the data while cloud server provides computation power ONLY.
> 

* [Privacy-Preserving Decision Tree Training and Prediction against Malicious Server](#PPDTTPAMS) proposed a HE-based solution, the essential idea is to encrypt a 0-1 indicator vector to indicate whether a sample is within a tree node. The tree model is ID3 only.

### Multi-party  over VERTICAL 
* [SecureBoost](#SecureBoost) provides a elegent FL-based solution to train an XGboost model among multiple data-providers. It also use basic HE tools to enable the feature-holder can accumulate its G and H among every possible local split-point. Then the Label-holder can decrypt and  find the best split-point INDEX after aggerating these Gs and Hs from every feature-holder. However, the solution has NO rigorous security proof, and its leaked intermediate information can actually dangerous. In short, IMHO, the global framework of SecureBoost is insightfull, while there still has much work to do to provide more data privacy guarantee.

* **Pivot** [link](https://arxiv.org/pdf/2008.06170.pdf) propose a solution to the same problem, training and prediction tree-based models among multi-party with vertically partioned data, by ulitizing both HE, actually all-threshold HE, and MPC, SPDZ in their implementation, in a rather rigorous way. 
 > Wu, Yuncheng, Shaofeng Cai, Xiaokui Xiao, Gang Chen, and Beng Chin Ooi. "Privacy preserving vertical federated learning for tree-based models." arXiv preprint arXiv:2008.06170 (2020).
 > 


# Libraries and Frameworks

* [Fedlearner](https://github.com/bytedance/fedlearner). A FL framework developed by ByteDance team, and it support tree-based and NN-based models.

