# Gated-training to enhance performance and robustness in computational models of word recognition

EARSHOT: exploring Gated-training to enhance performance and robustness in computational models of word recognition
This is my Master thesis project. The full document can be found here: [EARSHOT exploring Gated-training.pdf](https://github.com/peppievt/Gated-training/files/8418969/EARSHOT.exploring.Gated-training.pdf)

When using this repository, please cite this thesis.

This codebase can be used to apply gated training to audio data. The specifics can be found within the code files. I have splitted the code in 3 logical steps to seperate data preperation, training and testing of the model. In the prepare_data file, features are derived using MFSC extraction. Also the labels of the audio are transformed to semantic vectors. One can choose in this stage in what kind of vectors (one-hot, 300-10 vectors) and one could potentially use semantic vectors from an algorithm like Word2Vec.
In the training file, we setup everything to train the LSTM model. First we created the Gated-training samples, aka we construct data by partially extracting a [0, t] per sample of the dataset and adjust the label of the word accordingly using the Entropy calculation used in the paper. 
Further more one can specify the dataset, the split of train/validation and test set for training the model. Because we use a variable sample length, we use a batch generator with 1 sample per batch.
The test-file is used to conduct the experiments for my thesis. Divergent experiments are conducted here. We can visualize the training and validation curves of the training stage. Furthermore one can setup complete gated samples and predict word competition by either choosing several words (and visualize their competition) or just show the 5th best performing words during the audio stimulus. In this case we can also view the certainty of the word prediction by visualizing the activation of the semantic labels during word recognition. 
For a detailed analysis of the Gated-training method vs the Full-gated training model, the entropy and recognition of all training/validation and test samples is computed and compared. In this analysis, the Gated-training model appeared superior on all relevant criteria (recognition speed, certainty and dealing with noisy samples).

![afbeelding](https://user-images.githubusercontent.com/47629010/161780178-b1e0be8e-afff-405e-8643-57a47e988933.png)

![afbeelding](https://user-images.githubusercontent.com/47629010/161780268-6a6c28fc-e443-4086-b352-25bcb52e3506.png)
