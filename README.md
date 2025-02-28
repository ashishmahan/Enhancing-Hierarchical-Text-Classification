# Enhancing-Hierarchical-Text-Classification

Initially, I attempted to solve the problem using traditional machine learning techniques. The approach involved:

Text Vectorization:

Using 'TfidfVectorizer' from 'sklearn.feature_extraction.text' to convert the text data into numerical form. The max_features parameter was set to 10,000 to limit the dimensionality.

Classification Model:

A LogisticRegression model was trained for each category level using the MultiOutputClassifier to handle the multi-label nature of the problem.

Pipeline Setup:

The text vectorization and logistic regression were combined into a single pipeline for ease of processing.

Results:

Cat1 Accuracy: 0.7545

Cat2 Accuracy: 0.4895

Cat3 Accuracy: 0.32

The traditional approach was straightforward and computationally efficient. However, it struggled with the deeper levels of the hierarchy, particularly Cat2 and Cat3, where the accuracy dropped significantly.

To address the limitations of the initial approach, I switched to a deep learning model, which is better suited for capturing the complex relationships in hierarchical classification tasks.

Deep Learning with LSTM based Approach that I used to solve this task:

1. Preprocessing:

Tokenization and text vectorization.

Encoded target labels using Label Encoder method for the three hierarchical levels. Also padded the sequences to 200 tokens to ensure uniform input length.

An embedding layer was used to convert the input text sequences into dense vectors.

2. Model Design:

A Bidirectional LSTM model with 256 LSTM units (e.g., using a shared base model with multiple output layers corresponding to each category level). I applied class weights to give more importance to less frequent categories. I also used Dropout Regularization and Early Stopping during training to prevent overfitting.

Separate dense layers were used to output predictions for each category level (Cat1, Cat2, and Cat3), respecting the hierarchy.

3. Training and Evaluation:

Categorical cross-entropy loss was used for each output.

Trained the model on the dataset, ensuring hierarchical consistency.

Evaluated accuracy at each level of the category hierarchy.

Also I predicted the model on a sample text "This product is fantastic and works great for my dog!"
