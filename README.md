README: MNIST Digit Classification with Convolutional Neural Network (CNN)
This repository contains a comprehensive implementation of a Convolutional Neural Network (CNN) to classify handwritten digits from the MNIST dataset. Below is a detailed explanation of the steps and processes involved in the code, as demonstrated in the provided images.
•  Importing Packages and Loading the MNIST Dataset
	•  The process begins by importing essential Python libraries, including torch, torchvision, and matplotlib, to handle neural network operations, data transformations, and visualization.
	•  The MNIST dataset is loaded using torchvision.datasets.MNIST, with the dataset stored in the current directory (./).
	•  Data transformations are applied using transforms.ToTensor() to convert MNIST images into tensors.
	•  The dataset is split into training, validation, and test sets:
		•  Training set: First 10,000 images.
		•  Validation set: Next 10,000 images.
		•  Test set: Remaining images.
	•  DataLoaders are created with a batch size of 64, enabling shuffled data loading for training and validation.
•  Creating the CNN Model with nn.Sequential
	•  A CNN model is constructed using nn.Sequential, a sequential container for stacking layers.
	•  The architecture includes:
		•  First convolutional layer (Conv2d) with 1 input channel, 32 output channels, a 5x5 kernel, and padding of 2.
		•  ReLU activation function for non-linearity.
		•  Max pooling layer (MaxPool2d) with a 2x2 kernel to reduce spatial dimensions.
		•  Second convolutional layer with 32 input channels, 64 output channels, a 5x5 kernel, and padding of 2.
		•  Another ReLU and MaxPool2d layer.
		•  A flatten layer to transition from convolutional to fully connected layers.
		•  Two fully connected layers (Linear): first with 3136 input features and 1024 output features, followed by ReLU and dropout (p=0.5); second with 1024 input features and 10 output features (for 10 digit classes).
	•  The model processes a sample input to verify the output shape, resulting in a tensor of shape (4, 64, 7, 7) after convolutions and pooling, and (4, 3136) after flattening.
•  Defining Loss Function and Optimizer
	•  The cross-entropy loss function (nn.CrossEntropyLoss) is used to measure the difference between predicted and actual digit labels.
	•  The Adam optimizer is initialized with a learning rate of 0.001 to update the model parameters during training.
•  Training the Model with Training and Validation Sets
	•  A train function is defined to train the model over a specified number of epochs (set to 20).
	•  The training loop includes:
		•  Setting the model to training mode.
		•  Iterating over batches in the training DataLoader, computing predictions, loss, and backpropagation.
		•  Updating model parameters using the optimizer.
		•  Calculating and storing training loss and accuracy for each epoch.
	•  Validation is performed after each training epoch:
		•  Setting the model to evaluation mode.
		•  Iterating over validation batches, computing predictions and loss without gradient computation.
		•  Storing validation loss and accuracy.
	•  Accuracy is computed by comparing the argmax of predictions with true labels, averaged over the dataset size.
•  Viewing Training and Validation Accuracy and Loss
	•  The training and validation loss and accuracy histories are visualized using matplotlib.
	•  Two subplots are created:
		•  The first plot displays training loss (blue) and validation loss (orange) over epochs, showing a decreasing trend.
		•  The second plot shows training accuracy (blue) and validation accuracy (orange), indicating an increasing trend toward high accuracy (around 0.99).
	•  The plots are labeled with appropriate legends and axis titles for clarity.
•  Viewing Test Accuracy
	•  The trained model is evaluated on the test dataset.
	•  Predictions are made, and test accuracy is calculated as the mean of correct predictions (where argmax of predictions matches true labels), achieving approximately 0.9915.
•  Viewing Elements with Maximum Probability
	•  The code visualizes a subset of test images with their predicted labels.
	•  A 2x6 grid of images is created, displaying the first 12 test images.
	•  Each image is shown in grayscale, with the predicted digit label overlaid in blue text at the top center.
	•  The model correctly identifies most digits, with examples including 7, 2, 1, 0, 4, 1, 4, 9, 5, 9, 0, and 6.
This implementation demonstrates a complete workflow for building, training, and evaluating a CNN on the MNIST dataset, with visualizations to assess model performance. The code is structured for reproducibility and can be extended for further experimentation.

<img width="1507" height="835" alt="Screenshot 2025-09-20 185846" src="https://github.com/user-attachments/assets/643e6844-0499-4e6f-8f3f-635e209d94eb" />
<img width="1512" height="755" alt="Screenshot 2025-09-20 185929" src="https://github.com/user-attachments/assets/835d416b-4093-489d-ace9-5550a6161cce" />
<img width="1505" height="577" alt="Screenshot 2025-09-20 190007" src="https://github.com/user-attachments/assets/a554d1c9-e4c9-4870-abba-591195be67d7" />
<img width="1514" height="852" alt="Screenshot 2025-09-20 190037" src="https://github.com/user-attachments/assets/6d3d2e0d-fc31-4abb-99ff-bcbe9da797c4" />
<img width="1502" height="720" alt="Screenshot 2025-09-20 190106" src="https://github.com/user-attachments/assets/4b9978b7-5188-4a15-a7ff-9efc8ed672c2" />
<img width="1509" height="847" alt="Screenshot 2025-09-20 190144" src="https://github.com/user-attachments/assets/82120a4d-01cf-4ac3-9a98-e2f03a67deb3" />
<img width="1509" height="792" alt="Screenshot 2025-09-20 190210" src="https://github.com/user-attachments/assets/749e939e-3657-461d-aa8f-5e531f107a49" />
<img width="1508" height="802" alt="Screenshot 2025-09-20 190235" src="https://github.com/user-attachments/assets/c351d1cd-3db6-441c-8898-7e008f645ed9" />

