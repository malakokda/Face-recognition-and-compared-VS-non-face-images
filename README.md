# Face-recognition-and-compared-VS-non-face-images
This project explores dimensionality reduction and classification for face recognition using the **ORL (AT&T) Database of Faces**. It compares the effectiveness of **Principal Component Analysis (PCA)** and **Linear Discriminant Analysis (LDA)** for identifying subject IDs.

## The code:
1. **Loads and prepares the dataset**: Processes 400 grayscale images (92x112) into 10,304-dimensional vectors.
2. **Generates Data Matrix**: Constructs a single matrix  representing all subjects and a label vector  with IDs from 1 to 40.
3. **Splits the data**: Implements a specific partitioning where odd-indexed rows are used for training and even-indexed rows for testing.
4. **Applies Custom Dimensionality Reduction**: 
PCA: Projects data onto a reduced basis while maintaining a specific variance threshold ().
LDA: Uses class-specific scatter matrices to maximize separability between different subjects.
5. **Evaluates and Tunes**: Uses a K-Nearest Neighbor (K-NN) classifier and analyzes performance across different  values and  thresholds.
6. **Bonus - Face vs. Non-Face**: Extends the classification to distinguish between human faces and non-face imagery.

## Models used: 
**Principal Component Analysis (PCA)**: Retains dimensions based on variance levels .
**Linear Discriminant Analysis (LDA)**: Implements multiclass LDA using 39 dominant eigenvectors.
* 
**K-Nearest Neighbor (K-NN)**: The primary classifier used for final ID determination, tested with .

## Dataset:
**Source**: ORL dataset (40 subjects, 10 images each). 
**Features**: 10,304 numerical pixel values per image.
**Non-Face Data**: 100 images of random patterns, gradients, and textures for binary classification.

## Target class:
**Subject Recognition**: IDs 1 through 40.
**Binary Task**: Face (1) vs. Non-Face (0).

## How the code works:
1. 
**Partitioning**:
Creates a 50/50 split (5 instances per person for training/testing) by separating odd and even rows.

3. **PCA Implementation**:
* Computes the mean and centers the data.
* Solves for eigenvalues and eigenvectors of the covariance matrix.
* Selects  dimensions to satisfy the variance requirement .

3. **LDA Implementation**:
* Calculates the within-class scatter matrix  and between-class scatter matrix .
* Projects the training and test sets into a 39-dimensional space
* 
4. **Evaluation Metrics**: Reports **Accuracy** for every  value and compares PCA and LDA results directly.

## Results (Test Set):
**Best Model**: **LDA** consistently outperformed PCA, achieving an accuracy of **96.00%** compared to PCA's **94.00%** (at ).
**K-NN Tuning**: As  increased from 1 to 7, accuracy generally decreased for both models, though LDA maintained a significant lead over PCA as  grew.
**Bonus Task**: The binary "Face vs. Non-Face" classifier achieved **95.24%** accuracy, significantly outperforming the baseline "always non-face" prediction of 71.43%.

Would you like me to help you generate a **Visualization Script** to plot the accuracy curves for your report?
