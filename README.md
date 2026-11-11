# CSCI323 TweetEval Sentiment Analysis

This group project compares Multinomial Naive Bayes, logistic regression, and a linear support vector machine for classifying tweets as negative, neutral, or positive.

[Open the Python notebook](TweetEval_GroupABC_revised%20%282%29.ipynb)

## Run in Google Colab

1. Open the notebook in Google Colab with a CPU runtime. Run the first code cell to install the pinned packages. Restart the runtime if Colab prompts you.
2. Run **Group A** with `USE_GOOGLE_DRIVE = True` and authorize Google Drive when prompted. This saves the prepared data and fitted vectorisers in `MyDrive/CSCI323/TweetEval_Prepared/`.
3. Run **Group B** from B1 through B24. This trains the candidate models, selects one configuration per method, and saves `TweetEval_GroupB_ThreeMethods_Handoff.zip` in `MyDrive/CSCI323/`.
4. Run **Group C** from **Setup and Locate the Handoff Files** through **Final Integrity Check and Results Package**. This loads the three selected models, evaluates them on the test split, and saves the tables, plots, and error analyses in `MyDrive/CSCI323/TweetEval_GroupC_Evaluation_Results.zip`.

## Dataset and evaluation

The notebook uses the `sentiment` subset of `cardiffnlp/tweet_eval` at revision `b3a375baf0f409c77e6bc7aa35102b7b3534f8be`. It retains the original splits of 45,615 training, 2,000 validation, and 12,284 test tweets. [TweetEval dataset](https://huggingface.co/datasets/cardiffnlp/tweet_eval)

The comparison uses four feature sets combining counts or TF-IDF with unigrams or unigrams plus bigrams. Each vectoriser is fitted on the training split only. The notebook selects configurations by validation macro recall, using macro F1 to break ties, and evaluates the selected models on the held-out test split.

## Saved results

| Model | Validation macro recall | Test macro recall | Test macro F1 | Test accuracy |
| --- | ---: | ---: | ---: | ---: |
| Multinomial Naive Bayes | 0.6371 | 0.6072 | 0.5966 | 0.5988 |
| Logistic regression | 0.6461 | 0.5684 | 0.5699 | 0.6062 |
| Linear SVM | 0.6421 | 0.5747 | 0.5730 | 0.5959 |
| Training-majority baseline (always neutral) | 0.3333 | 0.3333 | 0.2172 | 0.4833 |

## References

- Barbieri et al. (2020) introduced TweetEval and its sentiment evaluation metric. [TweetEval paper](https://aclanthology.org/2020.findings-emnlp.148/)
- Pang et al. (2002) compared Naive Bayes, maximum entropy, and support vector machines for sentiment classification. [Sentiment classification paper](https://aclanthology.org/W02-1011/)
