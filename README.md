# NLP-Midterm-Bigram-LSTM-Transformer
Bigram vs. LSTM vs. small transformer for next-character prediction using the Tiny Shakespeare dataset.
## Task
Given previous characters, predict what the next character will be.

## Dataset
Tiny Shakespeare contains around 1.1 million characters with 65 unique characters
https://raw.githubusercontent.com/karpathy/char-rnn/master/data/tinyshakespeare/input.txt
90/10 training-to-validation split.

## Models Examined
1. Bigram: A lookup table that predicts the next character using the current one.
  - Uses only the current character and ignores everything before it.
  - It can't know the word or the sentence it's in; its text has text pairing but not a lot of real
    English words.
2. LSTM: Can read one character at a time and can carry memory through vectors. Gates are used to control what is remembered and what is forgotten.
  - All predictions use many earlier characters, so it can learn word shapes. Also worth noting that   it is well labeled.
  - Its memory can also fade out over a long piece of text, so it has to read one character at a       time instead of all at once.
3. Small transformer: Each character turns into a number to tell where it is and what it is. Four blocks of attention and feedforward layers allow it to look back at what it is. (128 dimensions
  - All characters can look at each other in the 128-character window and tell how
    relevant it is. A mask is used to block future characters.
## Results
