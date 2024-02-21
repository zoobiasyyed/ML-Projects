title: "Final Project"
author: "Lauren Szlosek and Zoobia Syyed"
format: pdf
---
# Introduction
For this project, our goal was to be able to build a model that is able to predict the genre of a movie based on the script that is provided. In order for the model to be successful, it is important that it accurately predicts the genre of the movie. The dataset used consists of information about actors and the movie scripts of their movies. The data is organized into eight columns; actors, characters they played, movie title, genre, year released, and the script of the movie. There are a total of 3922 entries. We only utilized the genre and script columns for efficiency. Deep learning is an important component in this project due to its unique ability to automatically extract and represent complex patterns and relationships within unstructured text data, such as movie scripts. Deep learning methods offer several distinct advantages. Firstly, deep neural networks, including LSTM and CNN architectures, can capture intricate patterns and dependencies in textual data, which is essential for understanding the nuances of movie scripts across different genres. Moreover, deep learning is particularly adept at feature learning, automatically discovering relevant features and representations from raw text data, which can be crucial when dealing with the rich and diverse content found in movie scripts.
The scalability and flexibility of deep learning models, combined with their ability to generalize well on diverse data, make them a compelling choice for this project. Therefore, deep learning is needed for achieving high-quality genre classification by effectively leveraging the inherent complexities of movie scripts and delivering robust, context-aware results.


# Analysis
Upon exploring the dataset consisting of 2,200 rows and 2 columns, our initial focus was on understanding the distribution of genres. We observed the varying counts of each genre, providing insights into the dataset's composition. Further, we delved into the distribution of script lengths, uncovering the range of words per script. The tokenization process revealed 95,375 unique tokens after processing the movie scripts.
Exploring the training process reveals interesting patterns in the model's learning journey. The accuracy on the training set steadily increases from an initial 8.95% to 82.67% after 50 epochs, indicating a significant learning progression. However, the validation accuracy, starting at 8.24%, shows a less pronounced improvement, reaching 36.93% by the end of training. This discrepancy suggests potential overfitting or a need for further model refinement.




# Methods


Our model, constructed as a sequential neural network, features an embedding layer for vectorizing words, a 1D convolutional layer for feature extraction, max-pooling to reduce dimensions, an LSTM layer for capturing sequential dependencies, and dense layers for classification. Training involved tokenization of movie scripts, padding sequences for uniform length, label encoding for genres, and splitting the data into training and testing sets (80-20 split). The model was compiled with categorical cross-entropy loss and Adam optimizer, training for 50 epochs with early stopping. Our original model involved multiple models combined, but we simplified it to make it run more efficiently.
When we first started training the model, we originally trained on just 100 scripts and only on 1 epoch, just because the code was taking a very long time to run. There was an attempt to run the code on Google Colab, but it was very unsuccessful, so we decided to run it on the server. The issue we kept running into was that the epochs would run, but only on 1000 rows of the data, rather than the whole data set. After running it on 50 epochs, our accuracy was unchanged, and stayed at a stagnant   0.3007 for the entire run. To combat this, we decided to increase our batch size from 64 to 128. After back and forth adjustments to the code, we still were getting very poor results, and were struggling to understand why.
It was discovered that there was something wrong with the dataset itself; every time there was a comma in the script, it would split and create a whole new genre. We could not identify this before, because these splits would not happen until line 400.
However, even after these changes, our model still overfit, and struggled to get an acceptable accuracy. As we trained the model, it would stop at 47/50 epochs, making it difficult for us to fully train.
Ultimately, our loss ended with 0.380, with the accuracy at 82.67 %, and our val_loss was 3.439, with the val_accuracy being 36%
![My Caption Here](/Users/cparlett/Desktop/corgi.jpg){width=300}
# Results
The model's performance metrics revealed training accuracy of approximately 9.6% and validation accuracy around 8.2%. The initial predictions on specific movie scripts showcased both correct and incorrect genre assignments. For instance, the model correctly identified "Elf" as a comedy but erroneously classified "Pet Sematary" as comedy instead of horror.


# Reflection
The training process sheds light on the complexities of the model and potential overfitting issues. The accuracy improvement on the training set does not necessarily translate to better generalization, emphasizing the need for careful model selection and hyperparameter tuning. Future iterations could explore different architectures, regularization techniques, and increased data size to enhance model robustness.


In conclusion, while the model shows promise in certain predictions, addressing overfitting and refining the architecture are critical for achieving better accuracy on unseen data. The results demonstrate the iterative nature of model development and the continuous learning process in the field of machine learning.
