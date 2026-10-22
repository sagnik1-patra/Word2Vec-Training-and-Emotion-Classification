# Technical Report: Word2Vec and GloVe Emotion Classification

## Dataset and preprocessing
207805 GoEmotions comments retained; 28 labels. Lowercasing, URL removal, tokenization and filtering were used.

## Word2Vec training
{'source': 'GoEmotions fallback (not independent domain corpus)', 'documents': 207805, 'tokens': 2783484, 'meets_10000_docs': True, 'meets_1m_tokens': True}
Skip-gram and CBOW hyperparameters were compared. Probe similarity is NOT downstream accuracy.

## GloVe and architectures
GloVe 6B 100d; coverage: {'GloVe': 96.65805483790317, 'Word2Vec': 99.75831319276607}. Dense, CNN, Word2Vec Dense, and fine-tuned Dense models were trained.

## Results
                   model  accuracy  macro_f1  weighted_f1
             GloVe_Dense  0.156216  0.136136     0.118786
               GloVe_CNN  0.222722  0.227166     0.198496
          Word2Vec_Dense  0.176587  0.167543     0.142604
         GloVe_FineTuned  0.215078  0.225808     0.171881
TFIDF_LogisticRegression  0.290781  0.286380     0.275517
      TFIDF_RandomForest  0.345608  0.048707     0.193392

## Multi-label evaluation
{'threshold': 0.2, 'hamming_loss': 0.0502561905067439, 'micro_f1': 0.4087189787417602, 'macro_f1': 0.2654337280520508, 'weighted_f1': 0.3487037093109677, 'precision_at_1': 0.4333515167236328, 'recall_at_1': 0.3925783336162567, 'precision_at_3': 0.24290737509727478, 'recall_at_3': 0.6353283524513245, 'precision_at_5': 0.1745532900094986, 'recall_at_5': 0.7483066916465759}

## Error analysis
 actual   predicted  count
neutral disapproval    666
neutral realization    535
neutral    approval    510
neutral   curiosity    508
neutral      caring    496
neutral   confusion    454
neutral      desire    331
neutral       anger    331
neutral  excitement    322
neutral    optimism    300

## Limitations
An independent 1-million-token domain corpus is required for full corpus compliance. WordSim-353/SimLex-999 and GloVe 300d are not included. The best-on-test summary is descriptive rather than a valid model-selection protocol. Results vary with random seed and hardware.
