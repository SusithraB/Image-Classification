## AIM

To Develop a convolutional deep neural network for image classification and to verify the response for new images.

## Problem Statement and Dataset

Include the Problem Statement and Dataset.

## Neural Network Model
![image](https://github.com/user-attachments/assets/d58b246e-4f4a-4958-bbc9-d9d86281cf73)


## DESIGN STEPS

### STEP 1:
Define the objective of classifying handwritten digits (0-9) using a Convolutional Neural Network (CNN).

### STEP 2:
Use the MNIST dataset, which contains 60,000 training images and 10,000 test images of handwritten digits.
### STEP 3:
Convert images to tensors, normalize pixel values, and create DataLoaders for batch processing.
### STEP 4:
Design a CNN with convolutional layers, activation functions, pooling layers, and fully connected layers.
### STEP 5:
Train the model using a suitable loss function (CrossEntropyLoss) and optimizer (Adam) for multiple epochs.
### STEP 6:
Test the model on unseen data, compute accuracy, and analyze results using a confusion matrix and classification report.
### STEP 7:
Save the trained model, visualize predictions, and integrate it into an application if needed.
## PROGRAM

### Name:SUSITHRA.B
### Register Number:212223220113
```class CNNClassifier(nn.Module):
    def __init__(self):
        super(CNNClassifier, self).__init__()
        self.conv1 = nn.Conv2d(in_channels=1,out_channels=32,kernel_size=3,padding=1)
        self.conv2 = nn.Conv2d(in_channels=32,out_channels=64,kernel_size=3,padding=1)
        self.conv3 = nn.Conv2d(in_channels=64,out_channels=128,kernel_size=3,padding=1)
        self.pool = nn.MaxPool2d(kernel_size=2,stride=2)
        self.fc1 = nn.Linear(128*3*3,128)
        self.fc2 = nn.Linear(128,64)
        self.fc3 = nn.Linear(64,10)






    def forward(self, x):
        x = self.pool(torch.relu(self.conv1(x)))
        x = self.pool(torch.relu(self.conv2(x)))
        x = self.pool(torch.relu(self.conv3(x)))
        x=x.view(x.size(0), -1)
        x =torch.relu(self.fc1(x))
        x =torch.relu(self.fc2(x))
        return x


```

```
# Initialize the Model, Loss Function, and Optimizer

model = CNNClassifier()
criterion =nn.CrossEntropyLoss()
optimizer =optim.Adam(model.parameters(),lr=0.01)

```

```python
## Step 3: Train the Model
def train_model(model, train_loader, num_epochs=3):
  for epoch in range(num_epochs):
      model.train()
      running_loss = 0.0
      for images,labels in train_loader:
        optimizer.zero_grad()
        outputs = model(images)
        loss = criterion(outputs,labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()


        print('Name:Susithra.B')
        print('Register Number:212223220113')
        print(f'Epoch [{epoch+1}/{num_epochs}], Loss: {running_loss/len(train_loader):.4f}')
```

## OUTPUT
### Training Loss per Epoch
![image](https://github.com/user-attachments/assets/4bd19783-58b1-4ab7-ba3f-79e3c1fd8d26)

### Confusion Matrix
![image](https://github.com/user-attachments/assets/110d95ff-c351-4cda-ba1b-1a2ec30b56bb)

### Classification Report
![image](https://github.com/user-attachments/assets/e4d23cdf-5a76-42fb-9457-2f5407799d56)


### New Sample Data Prediction
![image](https://github.com/user-attachments/assets/dfab90ca-fc81-47cb-ac52-46edd759e197)

## RESULT
Thus, We have developed a convolutional deep neural network for image classification to verify the response for new images.
