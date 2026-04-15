**Iris Recognition System using Deep Transfer Learning**

  This project implements an end-to-end deep learning solution for biometric iris recognition. It transitions from classical methods like the Hough Transform to a modern CNN-based architecture utilizing Transfer Learning to identify individuals based on iris patterns.

**📊Dataset Information**

   Name: CASIA-Iris-Interval (a subset of CASIA-IrisV4)
   Source: Provided via Kaggle
    Details: Contains 2,639 high-resolution grayscale images (320x280) from 249 subjects
    
  **🛠️ Technical Implementation**
  
  **1. Kaggle API Integration**
  
    To follow industry standards for data handling, the dataset is pulled directly into the Google Colab environment using the Kaggle API:
    
      * Created a kaggle.json credential file from Kaggle account settings
      * Authenticated the session using a unique API Token
      * Used !kaggle datasets download to fetch the data without manual uploads.
      
  **2. Handling File Duplicates**
    
    During the development process, repeated unzipping caused "File Already Exists" prompts.
    
      * Solution: Implemented the !unzip -o -q command.
      * The -o flag (Overwrite) was used to automatically replace existing files, ensuring a seamless, non-interactive code execution.
      
  **3. Code Workflow**
    
      i.   Environment Setup: Loading TensorFlow, Keras, and authenticating Kaggle.
      ii.  Data Preprocessing: * Normalizing pixel values to $[0, 1]$.
              Applying Data Augmentation (Rotation, Zoom, Horizontal Flip) to prevent overfitting.
              Splitting data into 80% Training and 20% Validation sets.
      iii. Model Architecture: * Base: MobileNetV2 (Pre-trained on ImageNet).
              Top: Global Average Pooling, a Dense layer (512 units), and a Dropout layer (0.5) for optimization.
              Output: Softmax layer corresponding to the number of subjects.
      iv.  Training: Compiled with the Adam optimizer and trained for 10 epochs.
      v.   Evaluation: Visualizing results through Accuracy and Loss curves.
      
**📈 Performance Results**

      Validation Accuracy: ~57%
      Validation Precision: ~97% (High reliability for biometric security).
      Observation: The validation accuracy outperformed training accuracy, demonstrating the effectiveness of the Dropout and Augmentation strategies.
