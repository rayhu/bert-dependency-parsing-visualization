# Analyzing BERT's Attention Weights and Dependency Trees

## Background

I visualize graph of BERT's multi-head attention weights per head per layer, where edges were created from attention weights exceeding the average value. 
However, the resulting structure did not form a proper dependency tree. 

This highlights the following challenges:

1. BERT's attention mechanism not only capture syntactic structure but also captures many more contextual and semantic relations.
2. High attention weights do not necessarily correspond to syntactic dependencies.
3. Different attention heads learn different patterns and serve various functions.


## Problem Analysis

1. Multi-head Attention in BERT


BERT uses multi-head attention to learn contextual representations.
Each head learns different types of information, including semantic relations, co-occurrence patterns, lexical similarity, partial syntactic structures, and more.
Not all heads are focused on learning syntactic dependencies.


2. Edges with Attention Weights > Average Do Not Necessarily Represent Dependency

High attention weights could indicate co-occurrence, referential relations, or contextual closeness, but not necessarily dependency relations.
Low attention weights might encode key syntactic functions because certain dependencies do not require high attention weights.


## Experiment Design
### 1. Multi-head Attention Function Analysis

**Objective:**
Identify which attention heads are more likely to learn dependency relations.
Rationale: Not every head learns syntactic structures, so identifying specific heads is crucial.

**Method:**

1. Select the right heads. As BERT has 12 layers and 12 heads in each layer. We have 144 possible heads to investigate. Lower layers first.

2. Analyze each attention head in each layer separately.

3. Calculate the matching score between each head's attention graph and the Gold Dependency Tree.

**Matching Metrics:**

UAS (Unlabeled Attachment Score): Checks if the dependency relations are correct without considering the labels.

LAS (Labeled Attachment Score): Considers both dependency relations and labels.

Select the heads with the highest matching scores.

**Steps:**

1. Collect a Gold Dependency Tree dataset, such as Universal Dependencies (UD) Treebanks.

2. Iterate through each layer and each head, generating the attention graph.

3. Calculate UAS and LAS for each head.

4. Select the heads with the highest UAS and LAS scores.

**Expected Outcome:**

Some attention heads will show high UAS and LAS, indicating they are more likely to learn dependency relations.

Most attention heads will learn other types of information, such as semantic relations.

### 2. Layer-wise Accumulated Attention Analysis

**Objective:**

Analyze layer-wise accumulated attention to investigate how BERT gradually constructs syntactic relations across layers.

Rationale: Single-layer attention may not reveal dependency relations, but accumulated attention across layers might reveal gradually built syntactic structures.

**Method:**
Accumulated Attention Graph:

Accumulate attention weights across layers and normalize them.

Construct an Accumulated Attention Graph to see if syntactic structures gradually emerge.

**Steps:**

1. Collect attention weights from each layer.

2. Accumulate attention weights:

3. Use either weighted accumulation (emphasizing higher layers) or average accumulation (more balanced).

4. Construct Accumulated Attention Graph.

5. Perform dependency parsing on the accumulated attention graph to observe if a valid dependency tree forms.

**Expected Outcome:**

Higher-layer accumulated attention graphs are more likely to reveal dependency structures.

Lower-layer accumulated attention graphs may show local co-occurrences or lexical similarity.


### 3. Attention Re-training with Supervision

**Objective:**
Enhance BERT's learning of dependency relations through supervised learning.

Rationale: The original BERT model was not trained with dependency supervision. Adding supervision signals from dependency trees can guide attention heads towards learning syntactic structures.

**Method:**

Loss Function Design:

Convert Gold Dependency Tree into a Dependency Attention Map.

Design a Supervised Loss Function to encourage BERT's attention maps to match the Gold Dependency Attention Map.

**Steps:**

1. Prepare a Gold Dependency Tree dataset.

2. Convert Gold Tree to Dependency Attention Map.

3. Design Supervised Loss Function:

4. Use L2 norm or Cross Entropy to compute the difference between BERT's attention map and Gold Dependency Attention Map.

5. Fine-tune BERT's attention layers with the supervised loss.

6. Observe the changes in attention maps and check if they become closer to dependency trees.

**Expected Outcome:**
After fine-tuning, some of BERT's attention heads will more closely correspond to dependency relations.
UAS and LAS scores will significantly improve, indicating better alignment with syntactic structures.

## Targets:

These experimental designs aim to uncover the underlying patterns of BERT's attention mechanism and its potential relationship with syntactic dependencies. They offer a more detailed perspective than merely analyzing high attention weights, leading to a better understanding of how BERT represents syntactic structures.

These insights could further improve syntactic parsing models and contribute to NLP tasks requiring syntactic awareness, such as semantic role labeling, information extraction, and machine translation.
