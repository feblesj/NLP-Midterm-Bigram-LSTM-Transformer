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

## Analysis of Results
LSTM performed the best for this task. It had the lowest validation loss (1.488), followed by the transformer (1.585), and the bigram came in last with (2.486). The bigram's text was mostly nonsense words. The LSTM and transformer both read like a real Shakespeare play and were able to realize the labels were speakers, but they both had examples of words that didn't make sense from line to line. I do think that LSTM read slightly better than the transformer. While comparing to the bigram, the transformer lowered the validation loss from 2.486 to 1.585 and wrote real words and lines that read like a play. Although compared to LSTM, it didn't lower the loss, its training and validation losses were also closer together (0.21 vs. 0.30), and the validation loss was still continuing to fall at 3000 while LSTM's flattened. Attention allows all characters to look straight at any earlier character and choose the ones that are still relevant, which was important when compared to bigram. In this test, it didn't beat LSTM. My prediction is that the training of 3000 steps was too small. It also probably could've benefited from tuning, and I didn't look into that. I don't think that the extra complexity was worth it in this context. The transformer took way longer, was much more difficult to code, and didn't even beat the LSTM for all of the effort that I went through. It would probably be better with more data and more training. The biggest thing that I learned about attention is that it allows all characters to have a view of the earlier text, so instead of just passing it along one character at a time, it had a much larger picture to look at, which was also very beneficial. It helped a lot over the bigram, though in my test it didn't beat the LSTM.

## AI-Use Disclosure
I used Claude to plan exactly what I was going to do for this project. I also typed the code myself and ran all three models. When I got errors, I would ask Claude what went wrong and ask for an explanation, and then I would go back and make the changes myself. I truly believe that I understand what I did in this project and could explain exactly what the code does after going back and forth with Claude throughout this project.
