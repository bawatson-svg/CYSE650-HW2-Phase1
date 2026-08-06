# Assignment 2: Sentiment Classification with Neural Language Models

## Overview

In this assignment, you will build a sentiment classifier for movie reviews. Each review is labeled as either negative or positive:
```t
0 = negative
1 = positive
```

You have learned several modeling approaches in class, including RNNs, Transformers, pretrained embeddings, or even pretrained language models. You may choose any appropriate model or combination of models from the course. Your goal is to achieve strong classification accuracy and clearly explain your design choices.

The training dataset is intentionally **small** and **imbalanced**. This is part of the assignment. You should think carefully about potential issues then design your training pipeline accordingly:
- overfitting,
- class imbalance,
- evaluation tokens not shown in the training data.
  

## Dataset

The data comes from the Pang and Lee movie review polarity corpus, redistributed through NLTK. The original corpus contains 1000 positive and 1000 negative movie reviews.

The released files are:

```text
train.csv
public_test.csv
```

Each CSV file contains:

```text
id, text, label, label_name, source_file
```

The `text` column contains the movie review. The `label` column contains the sentiment label.

### Training Set

Use data in `train.csv` to train your model.

The training set contains 240 reviews:

```text
180 positive reviews
60 negative reviews
```

This training set is intentionally imbalanced.

### Public Test Set

Use `public_test.csv` to evaluate your model locally.

The public test set contains 400 reviews:

```text
200 positive reviews
200 negative reviews
```

You may report your accuracy on this public test set in your writeup. **Do not train your model on the public test set.**

### Hidden Test Set

There is also a hidden test set that will not be released to students at Stage 1. Your final submitted model will be evaluated on both the public test set and the hidden test set. The hidden test set is balanced and contains reviews that do not appear in `train.csv` or `public_test.csv`.

## Task

Build a model that predicts the sentiment label for each movie review.

Your model should take a review as input and output one of the following labels:
```text
0 = negative
1 = positive
```
You may also compare multiple approaches and submit your best-performing model.

## Assignment Stages

This assignment has two stages.

### Stage 1: Model Development and Public Test Submission

By the Stage 1 deadline, submit **a public GitHub repository link** containing your final model development work. **Your repository commit timestamp will be used to verify on-time submission.** 
Any modifications of **stage1_notebook.ipynb** and **model_checkpoint/** the after Stage 1 deadline will be noticed and affect your grading.

Your Stage 1 GitHub repository must include:
```text
stage1_notebook.ipynb
README.md
requirements.txt
model_checkpoint/
public_test_predictions.csv
```

Your `stage1_notebook.ipynb` should contain the following markdown comments:
 
- what is your model structure
- How did you handle the small and imbalanced training set?  
- key training techniques (such as the choice of learning rate, optimizer, batch size)
- evaluation result in total accuracy, and a confusion matrix on the given public test data samples.

Your `model_checkpoint/` folder must contain all files needed to reload your trained model.  
The file `public_test_predictions.csv` must contain exactly:
```text
id,predicted_label
```

where `predicted_label` is either `0` or `1`.

### Stage 2: Hidden Test Evaluation

After the Stage 1 deadline, the instructor will release the hidden test file:

```text
hidden_test.csv
```

The hidden test file will contain movie reviews and labels for Stage 2 self-evaluation. You will load the exact model checkpoint submitted in Stage 1 and use it to generate predictions for the hidden test examples.

For Stage 2, update the same GitHub repository and include:

```text
stage2_notebook.ipynb
hidden_test_predictions.csv 
```

Your `stage2_notebook.ipynb` should clearly show:

- hidden test accuracy
- hidden test confusion matrix 
- a short comparison between your public test result and hidden test result.
- if you had more time or compute, what would you try next?

The file `hidden_test_predictions.csv` must contain exactly:

id,predicted_label

where `predicted_label` is either `0` or `1`.
 


Stage 2 is **inference and evaluation only**. Although the hidden labels are provided for evaluation, you may not retrain, fine-tune,  or otherwise modify your model after the Stage 1 deadline. Your hidden test predictions must be generated from the Stage 1 checkpoint.

Any modifications to **stage1_notebook.ipynb** or **model_checkpoint/** after the Stage 1 deadline will affect your grade. Stage 2 work should be limited to adding **stage2_notebook.ipynb**, **hidden_test_predictions.csv**, and **hidden_test_evaluation.md**.

## Requirements
1. Your code should be runnable on a single Mac or Windows laptop. You may use CPU-only training.
2. Your inference code should be able to load your saved checkpoint and generate predictions without retraining. A strong submission does not need to use the largest model. A clear, well-evaluated approach that runs reliably is better than a complicated model that cannot be reproduced.

## Submission

For Stage 1, submit a **Public GitHub repository link** containing:
```t
stage1_notebook.ipynb
README.md
requirements.txt
model_checkpoint/
public_test_predictions.csv
``` 
Your `README.md` should explain how to run your notebook or prediction script.
 

For Stage 2, **uploaded these two files to the same GitHub repository as in your Step 1**, and **submit the github link** as a dummy submission.
```text
stage2_notebook.ipynb
hidden_test_predictions.csv 
``` 
 


## Rules

- You may use standard Python machine learning libraries, including PyTorch, scikit-learn, Hugging Face Transformers, NLTK, NumPy, and pandas.
- You may use pretrained models or pretrained embeddings.
- You may not manually label, rewrite, or modify the training and testing data  examples.
- You may not train on `public_test.csv`.
- You may not retrain, fine-tune, or modify your model after the Stage 1 deadline.
- Stage 2 hidden test evaluation must use the model checkpoint submitted in Stage 1.
- If you use online references, acknowledge them in your writeup. If you use generative AI tools, specifically include an 'Use of AI' section.
