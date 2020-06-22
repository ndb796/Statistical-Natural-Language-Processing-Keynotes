### Neural Machine Translation (NMT)

* Neural Machine Translation (NMT) is a way to do Machine Translation with a single neural network.
* The neural network architecture is called sequence-to-sequence (aka seq2seq) and it involves two RNNs.

### Sequence-to-sequence is versatile!

* Sequence-to-sequence is useful for more than just MT
* Many NLP tasks can be phrased as sequence-to-sequence:
    * Summarization (long text → short text)
    * Dialogue (previous utterances → next utterance)
    * Parsing (input text → output parse as a sequence)
    * Code generation (natural language → Python code)

### Neural Machine Translation

* The sequence-to-sequence model is an example of a Conditional Language Model.
    * Language Model: the decoder is predicting the next word of the target sentence y
    * Conditional: Its predictions are also conditioned on the source sentence x
* NMT directly calculates P(y|x):
    * P(y|x) = P(y1|x)P(y2|y1,x)P(y3|y1,y2,x)...P(yT|y1,...,yT-1,x)
* Question: How to train a NMT system?
* Answer: Get a big parallel corpus
* Seq2seq is optimized as a single system.
    * Backpropagation operates "end-to-end".

### Greedy decoding

* We saw how to generate (or "decode") the target sentence by taking argmax on each step of the decoder.
* This is greedy decoding (take the most probable word on each step)
* Problems with this method?
    * Greedy decoding has no way to undo decisions!

### Beam search decoding

* Core idea: On each step of decoder, keep track of the k most probable partial translations.
    * k is the beam size (in practice around 5 to 10).
* Beam search is not guaranteed to find the optimal solution.
* But much more efficient than exhaustive search!
    * Exhaustive search decoding is far too expensive.

### Beam search decoding: stopping criterion

* In greedy decoding, usually we decode until the model produces a <END> token.
    * For example: <START> he hit me with a pie <END>
* In beam search decoding, different hypotheses may produce <END> tokens on different timesteps.
    * When a hypothesis produces <END>, that hypothesis is complete.
    * Place it aside and continue exploring other hypotheses via beam search.

### Advantages of NMT? (Compared to SMT)

* Better performance
    * More fluent
    * Better use of context
    * Better use of phrase similarities
* A single neural network to be optimized end-to-end
    * No subcomponents to be individually optimized
* Requires much less human engineering effort
    * No feature engineering
    * Same method for all language pairs

### Disadvantages of NMT? (Compared to SMT)

* NMT is less interpretable
    * Hard to debug
* NMT is difficult to control
    * For example, can't easily specify rules or guidelines for translation
    * Safety concerns!

### NMT: the biggest success story of NLP Deep Learning

* Neural Machine Translation went from a fringe research activity in 2014 to the leading standard method in 2016
    * 2014: First seq2seq paper published
    * 2016: Google Translate switches from SMT to NMT

### So is Machine Translation solved?

* Nope!
* Many difficulties remain:
    * Out-of-vocabulary words
    * Domain mismatch between train and test data
    * Maintaining context over longer text
    * Low-resource language pairs

### Sequence-to-sequence: the bottleneck problem

* 인코더는 고정된 크기의 컨텍스트 벡터를 반환해야 하므로, 정보 손실이 발생할 수 있음
* 입력 문장이 길면 번역 품질이 떨어지는 문제가 발생

### Attention

* Attention provides a solution to the bottleneck problem.
* Core idea: on each step of the decoder, use a direct connection to the encoder to focus on a particular part of the source.

### Attention is great

* Attention significantly improves NMT performance
    * It's very useful to allow the decoder to focus on certain parts of the source.
* Attention solves the bottleneck problem
    * Attention allows the decoder to look directly at source; bypass bottleneck.
* Attention helps with vanishing gradient problem
    * Provides a shortcut to faraway states
* Attention provides some interpretability
    * By inspecting attention distribution, we can see what the decoder was focusing on.
    * We get (soft) alignment for free!
    * This is cool because we never explicitly trained an alignment system.
    * The network just learned alignment by itself.
