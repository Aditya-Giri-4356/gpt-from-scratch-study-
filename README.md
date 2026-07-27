# gpt-from-scratch-study-

A small GPT-style language model built from scratch in PyTorch, based on the learning approach from Andrej Karpathy's GPT implementation. The main goal of this project was to understand how a GPT-style Transformer actually works internally by building the components step by step instead of using a pre-built Transformer model.

The original character-level tokenizer approach was also modified to use SentencePiece BPE tokenization.

The final model contains:

-SentencePiece BPE tokenizer
-Token embeddings
-Positional embeddings
-Query, Key and Value projections
-Causal self-attention
-Multi-head attention
-Feed-forward networks
-Layer normalization
-Residual connections
-Transformer blocks
-Cross-entropy loss
-AdamW optimizer
-Autoregressive text generation

##Dataset

The model uses the Tiny Shakespeare dataset used in Karpathy's original educational implementation.

##SentencePiece BPE

Instead of keeping the original 65-character vocabulary, I trained a SentencePiece BPE tokenizer with a vocabulary size of 5000.

Tokenizer: SentencePiece
Model type: BPE
Vocabulary size: 5000
Maximum token ID: 4998

##Final Model Configuration 

+----------------------+--------------------------+
| Parameter            | Value                    |
+----------------------+--------------------------+
| Model                | Decoder-only Transformer |
| Dataset              | Tiny Shakespeare         |
| Tokenizer            | SentencePiece BPE        |
| Vocabulary Size      | 5,000                    |
| Total Tokens         | 295,231                  |
| Context Length       | 128                      |
| Embedding Dimension  | 128                      |
| Attention Heads      | 4                        |
| Transformer Layers   | 4                        |
| Feed Forward Size    | 512                      |
| Batch Size           | 32                       |
| Dropout              | 0.0                      |
| Optimizer            | AdamW                    |
| Learning Rate        | 3e-4                     |
| Training Iterations  | 5,000                    |
| Parameters           | 2,093,192 (~2.09M)       |
| Device               | CUDA (Google Colab T4)   |
+----------------------+--------------------------+


Final Training Loss: 1.2681
Training Progress: 8.4974 → 1.2681 (5,000 iterations)


##Output

After training, the model was able to generate Shakespeare-like text.

PRINCE: Come, cousin, women he may shed for you;
and we will choose; but pity reconcile...

SICINIUS: This know you: We cannot speak...

BRUTUS: With pates!

VOLUMNIA: O, flowers, that, that would have rather I had...

BUCKINGHAM: My Lord' party, my lord.

DUKE VINCENTIO: My men!

The output is not grammatically perfect and contains malformed words, but the model learned recognizable patterns from the dataset including:

-Shakespearean vocabulary
-Character names
-Dialogue formatting
-Punctuation
-Sentence structure
-Word combinations
-Shakespeare-style text patterns


##Bigram vs Transformer

The Bigram model was useful as a baseline but showed much weaker learning.

Example:

Iteration 0: Loss = 8.9726
Iteration 500: Loss = 8.8299
Iteration 1000: Loss = 8.5877

The final Transformer reached:

Iteration 0: Loss = 8.4974
Iteration 500: Loss = 5.0480
Iteration 1000: Loss = 4.4311
...
Iteration 4999: Loss = 1.2681

The main difference is that the Bigram model has very limited context, while the Transformer can use self-attention across the 128-token context window.

##References

This project was heavily inspired by Andrej Karpathy's educational material on building GPT-style language models from scratch.

The original character-level approach was extended with SentencePiece BPE tokenization and the model was developed incrementally to understand the individual components of a Transformer.

Link to the video: https://www.youtube.com/watch?v=kCc8FmEb1nY
