| Model | Params | Train Loss | Val Loss | Training Time | Generated Text Quality | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| Bigram | 4225 | 2.4554 | 2.4862 | 9.9s | Low | Uses 1 previous character only | 10s | Low | Uses 1 previous character only |
| LSTM | 946625 | 1.1876 | 1.4878 | 72.2s | Medium | Memory carried step by step; val loss flattened at 2500 | 72s | Medium | Memory carried step by step; val loss flattened at 2500 |
| Transformer | 824897 | 1.3707 | 1.5847 | 105.7s | Medium | Attention over 128-character context; val loss continued to fall at 3000  | 106s | Medium | Attention over 128-character context; val loss continued to fall at 3000  |
