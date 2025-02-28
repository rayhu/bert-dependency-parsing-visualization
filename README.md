# BERT Attention Visualization

This project visualizes BERT's attention weights using network graphs. It helps us understand how different layers and attention heads in the BERT process relate to different tokens in a sentence.

There are multiple layers of linguistic dependencies in BERT attentions. For example, word-level relations are captured as lexical dependencies at low layers, phrase strcuture as syntactical dependencies in higher layers, semantical dependencies as constituency parsing, and discourse graphs at even higher layers. Structure information must be passed from low-layer heads to high-layer heads.

How is the structure information represented? How does it pass from low-layer heads to high-layer heads?

One specific target is **discovering how the dependencies get more abstract across layers**.

Let's define several types of cross-layer head connections. 
1. Aggregational connection: The lower head tells the higher head that the data is an aggregation of stuff. Such as "the data I am passing to you is an aggregation of tokens to form a phrase or partial phrase " or " the data I am passing to you is an aggregation of phrases to form a semantical entity."
This corresponds to compositionality in language, that words form phrases, phrases form clauses, and clauses form sentences.

2. Hierarchical Connection: The lower head tells the higher head that the lower layer job is done. For example: "The data I am passing to you shows the syntactical parsing is done. Now do the semantical parsing". This closely relates to linguistic processing stages, from the structure of syntax to the meaning of semantics.

3. Causal Influence Connection: The lower head tells the higher head that the semantical entities have certain causal relationships. This maps well to discourse-level meaning and pragmatic reasoning—how different ideas interact causally. This aspect is critical for tasks like reasoning and dialogue modeling.


To visualize it, we can connect the output of heads across layers so that the head output is the head input of the next layer. This will be a graph data structure that represents the heads as nodes and their connections as edges. Then, we shall label this edge using the three types above.

Then, we can make a verifiable prediction: If the edge labeling is aligned with human labeling, the model will perform better in the evaluation methods.

To validate the hypothesis, we can test whether correct edge labeling is related to improved model performance.
Step 1: Analyze BERT to extract attention connections across layers.
Step 2: Manually or algorithmically label these connections based on linguistic principles.
Step 3: Evaluate performance such as SuperGLUE or SQuAD about its relations of correctly labeled edges.


## Environment Setup

1. Create a new conda environment:
   ```bash
    conda env create -f environment.yml
   ```

2. Activate the environment:
   ```bash
    conda activate bert_env
   ```
3. Run Jupyter Notebook:
   ```bash
    jupyter notebook
   ```
4. Run the cells in the notebook.
## Why Visualize BERT Attention Weights?

Visualizing BERT's attention weights through dependency parsing is crucial for understanding and interpreting how this powerful language model processes text. By examining attention patterns, researchers and practitioners can gain insights into how BERT captures linguistic relationships, identifies important contextual connections, and builds semantic representations. These visualizations serve as a valuable diagnostic tool for model interpretability, helping to demystify the "black box" nature of transformer models. They can reveal whether BERT is learning meaningful grammatical structures, focusing on relevant tokens, or potentially developing problematic biases. This understanding is essential for improving model performance, debugging issues, and ensuring responsible deployment of BERT-based applications in real-world scenarios.

From the BERT attention weights, we can probably derive many information, such as grammatical structure, semantical structure, and even world-knowledge.


