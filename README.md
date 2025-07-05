# 25-2-R-13 - Literature sources analysis using deep impostor approach
Our project describes an unsupervised process for finding stylistic boundaries in long or
composite texts. A challenge that has become increasingly important as texts are 
written, modified, or assembled from multiple sources. Building on the Deep Impostors
framework, which uses deep neural models like CNNs and BERT to create chunk-level
stylistic signals, our main addition is a robust change-point detection technique
that allows for fine-grained segmentation without the need for prior labels.

The proposed method divides each input text into fixed-size batches and represents
them using word embeddings (Word2Vec or BERT). For each pair of unrelated
“impostor” texts, a binary classifier is trained to identify their stylistic patterns, and the
resulting model is applied to the target text to generate a sequence of probabilistic
stylistic scores (signals). To determine candidate boundaries, we employ a rolling
distance calculation that detects local stylistic deviations and highlights abrupt shifts
within the text. Peaks in this distance signal are evaluated as potential stylistic transition
points.

To improve segmentation reliability, findings from numerous impostor pairs will be
combined using a consensus voting process. The complete pipeline will be built in
Python, with comprehensive unit testing and future evaluation against annotated
datasets using standard metrics such as precision, recall, and F1 score.

This methodology seeks to demonstrate that integrating deep impostor signals, rolling
distance analysis, and consensus voting can result in an effective and fully
unsupervised method for stylistic segmentation of complex documents.
