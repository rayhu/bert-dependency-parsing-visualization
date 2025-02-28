# Papers

## Group Tokens
[Multi-Token Joint Speculative Decoding for Accelerating Large Language Model Inference, Qin et al., 2024](https://arxiv.org/abs/2407.09722v1)

This paper has an innovative point of joint perplexity with multi-token considered together. We shall similarly group tokens.
It is key to understanding the semantic structural embedding.

## What did BERT Heads learn
[What Does BERT Look At? An Analysis of BERT's Attention, Clark et al., 2019](https://arxiv.org/abs/1906.04341)

It is about what different heads in different layers learned during training.

## Why BERT heads learn
[Identifying Semantic Induction Heads to Understand In-Context Learning, Ren et al., 2024](https://arxiv.org/pdf/2402.13055)

It is about how BERT heads was able to capture syntactical and semantical embeddings.

## Implicit Vocabulary which is critical for Semantic Representation
[Token Erasure as a Footprint of Implicit Vocabulary Items in LLMs, Feucht et al., 2024](https://arxiv.org/abs/2406.20086)

It talks about finding implicit vocabulary from tokenization, and semantic representation. 

## Structural Probe for Finding Syntax
[A Structural Probe for Finding Syntax in Word Representations. Hewitt et al., 2019](https://aclanthology.org/N19-1419/)
The structure probe found that all syntax trees are implicitly represented in ELMo and BERT but not in traditional word embeddings!
The hierarchical structure of syntax trees is reflected geometrically in the transformed space.

## Recall with attention edge
[Dissecting Recall of Factual Associations in Auto-Regressive Language Models. Geva et al., 2023](https://arxiv.org/abs/2304.14767)

Attention heads encode subject-attribute mappings and play a crucial role in attribute extraction.
The last-subject position is enriched with multiple related attributes, facilitating flexible and contextualized retrieval.

## Jing Huang's Repo
[Demystifying Verbatim Memorization in Large Language Models., 2025](https://github.com/explanare/verbatim-memorization)

Study verbatim memorization. What about making a loss function to punish the verbatim memorization?


## Semantic Entities as Tensors

[Tensor Decomposition for Signal Processing and Machine Learning. Sidiropoulos et al., 2016](https://arxiv.org/abs/1607.01668)

Basically, we are trying to figure out the hidden latent variable by observing the distribution. Think about Bayesian generative model or HMM. But structured in a high-dimensional space. Why? Because the semantic entities are embedded in high-dimensional space instead of sequential signals.

If we are looking at a paper, we can observe the tokens, of course, and then we can orgnize them structurely, by finding the important clusting of the tokens, for example, the title and the abstract shall receive more attention than the content or citations.

In a hidden latent variable model, the High Order Moment captures the high-dimentional relavance between the observed data. When we have 3 variables, we need the third order moment which is a three dimensional covariance tensors. For 4 variables, we need four-dimensions covariance tensor.

Then, we use CPD to decompose it to find the conditional distribution of each observations.

## CPD for tensors
[Understanding the CANDECOMP/PARAFAC Tensor Decomposition](https://www.alexejgossmann.com/tensor_decomposition_CP/)

## Higher-Order Singular Value Decomposition (HOSVD)
Generalize SVD to high-dimensional space.



