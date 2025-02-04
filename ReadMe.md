# Categorising Buildings in Lausanne Based on Facade Material

## Project Description

Our project, in collaboration with HERUS (Laboratory for Human-Environment Relations in Urban Systems) aims to classify buildings in Lausanne into five categories based on the construction materials of their facades : brick, concrete, mixture, other and stone. Our main mission is to provide essential data that will guide future development and transformation projects of the built environment of Lausanne, with a view to meeting the needs of the city by 2050.

## Prerequisites

Before you begin, make sure you have the following installed :
- Python (version 3.10.0 or more).
- The following Python libraries : NumPy, Pandas, Scikit-learn, Matplotlib, PyTorch, Requests, PyProj.
- Jupyter Notebook (optional, but recommended for data mining).

With these prerequisites, you'll be well-equipped to begin your project with confidence.

## Data Sources

The data proposed by HERUS as part of this project are :
- **Swiss Real Estate Database** : This resource provides detailed information on buildings in Switzerland, extracted from the official directory of building addresses, published by the Federal Office of Topography (swisstopo).
- **Google Street View via the Google Maps API** : To download images of building facades at specific geographic locations in Lausanne.

These data sources form the foundation of our project, providing us with rich information to achieve our objective.

## File List

In this GitHub repository, you will find the following files :
- **ReadMe** : This document provides essential project details, guidelines, and instructions to help you navigate through the repository.
- **notebook** : Here, you'll find the main Jupyter Notebook containing the project's code.
- **pure_adr** : csv file containing data extracted from the Swiss Real Estate Database, bringing together detailed information on real estate in Switzerland, such as building addresses.
- **images_bat** : This directory stores images specifically related to Lausanne building facades, sourced from Google Street View via the Google Maps API.
- **dataset** : The dataset directory contains the collected building images utilized in the project's analysis.
- **materials** : File containing additional image resources of materials corresponding to the five classes.
- **images_test** : It includes supplementary images used for final testing, serving as illustrative examples.
- **illustrations** : Visual image file to illustrate the explanations and concepts presented in the notebook.
- **report** : Detailed document that describes the conclusions, hypotheses, assertions, findings and explains the thought process behind the implementation of the project, without including code.

The previously mentioned files, which are not present in this GitHub repository, are available via the following link : https://drive.google.com/drive/folders/1OPpM4h81X0BbYWkzu7kgAEGEfEu6Gj3M?usp=drive_link.

## Data Collection

In this project, we implement a multi-step data collection process :
1. **Extracting coordinates** : Initially, we extract coordinates of buildings located in Switzerland from the pure_adr.csv file. To effectively manipulate this this data stored in a dataframe, we use the Python library Pandas to filter only the coordinates of Lausanne buildings.

2. **Coordinate transformation** : The obtained coordinates are initially in the Swiss coordinate system. To ensure compatibility, we convert them to the global coordinate system using the Python library PyProj. This step allows us to work with consistent coordinate data suitable for Google Maps API usage.

3. **Google Street View data retrieval** : With coordinates transformed into the global coordinate system, we utilize the requests library to fetch building images from Google Street View via the Google Maps API. These images of Lausanne buildings are stored in the images_bat directory.

4. **Additional image collection** : Since the obtained images are not sufficiently balanced across different classes and may have quality limitations due to sharpness and obstructed facades, we independently collect additional images for each class. This approach ensures a more balanced representation of each category and better quality control. These images are placed in the dataset directory and will serve as the foundation for our analysis.

This structured process ensures that we have the necessary data to achieve the objectives of our project.

## Data Preprocessing

In this phase, we undertake several essential steps to prepare our dataset for effective model training :
1. **Train-Test split** : We initially divide our dataset, using the Scikit-Learn library, into two distinct sets, the train set and the test set. The train set, comprising 70% of the images, serves as the primary data source for training our machine learning model. On the other hand, the test set, representing the remaining 30% of the images, functions as an independent dataset used to evaluate the model's performance and generalization.

2. **Data transformation** : One crucial aspect of data preparation is ensuring uniformity in image size, as our images originate from various sources and may differ in dimensions. We accomplish this by resizing all images to a consistent size. Additionally, we perform normalization on the images using the PyTorch (torch) library. This process helps enhance training stability and reduces biases introduced by variations in pixel value scales.

3. **Data augmentation** : To enrich the diversity of the training set and simulate various scenarios, we employ data augmentation techniques using the PyTorch (torchvision) library. These include random flips, random translations, zooms, crops, the addition of Gaussian blur, brightness adjustments, and more. By doing so, we expand the range of images provided to our model, improving its ability to learn and generalize effectively.

Please note that the train and test sets are not added to the GitHub repository, as their creation is executed by the code during runtime.

## Building the Model

In this phase, we explore various approaches to classify the images of buildings within our dataset. 

1. **Models** : We assess the performance of three distinct methods :
    - **Pretrained VGG-16 model** : It is a deep convolutional neural network (CNN) model known for its simplicity and linear architecture, consisting of 13 convolutional layers and 3 fully connected layers, making it suitable for initial image classification tasks.
    - **Pretrained ResNet-50 model** : Variant of the ResNet model, characterized by its 48 convolutional layers, along with pooling layers. It is a more advanced and complex architecture than VGG-16, and it excels in training deep networks without suffering from gradient vanishing problems, making it a robust choice for precise image classification tasks.
    - **Our SimpleCNN model** : It is a CNN model specially designed by us, for our construction materials classification task. We build SimpleCNN from scratch and it consists of five convolutional layers followed by ReLU activation functions and max pooling operations, culminating in a fully connected layer responsible for carrying out the classification task. It also includes a dropout layer for regularization during training.


2. **Evaluations and comparison** : We assess the models' performance using evaluation metrics such as accuracy (calculated using the NumPy library), the F1 score, or the ROC curve (via the Scikit-Learn library). Additionally, we will plot training loss and test loss curves to gain insights into our models' behavior, helping us identify potential issues like overfitting or underfitting.

3. **Regularization techniques** : To enhance the robustness and generalization of our models, we implement regularization techniques, such as weight decay. These techniques help prevent overfitting and improve model performance on unseen data.

4. **Hyperparameter tuning** : To fine-tune the performance of our models, we explore hyperparameter optimization techniques. This process involves systematically varying model hyperparameters and plotting curves to determine optimal parameter settings. We utilize the Matplotlib library to visualize these curves and identify the best hyperparameters.

This comprehensive analysis enables us to select the most suitable model and parameter settings for our specific building material classification task.

## Summary

In this section, our main goal is to evaluate, as an example, the performance of the best model using a set of test images from the test_images dataset. The goal is to evaluate the model's ability to accurately classify these test images into their respective classes. Through this evaluation process, we aim to provide examples of image evaluations performed by the model, helping us determine whether they correctly classify images into the appropriate categories or not.

## Instructions

For the smooth running of the project, please follow these simple instructions. First, make sure you have installed the necessary libraries and run the first import cell in the notebook. Then you can run the code in sequence, ideally from the bottom up, to follow the chronological flow of the project. However, you have the option to skip the "Data Collection" section because images collected from the Google Street View API are not used due to their lack of relevance (please note that our API key for Google Street View is hidden for security reasons, meaning you will not be able to download images of Lausanne buildings from the Google Street View API using the appropriate cell in the notebook). You can start execution from the "Data Preprocessing" section. Be sure to set up the necessary items before you begin, which includes downloading the nine files mentioned previously and placing them in a single folder. For a more detailed understanding of the project, view the report.

## Authors

This work was carried out by Youssef Belghmi and Hamza Morchid, Master Data Science students at EPFL, as part of the semester project in the Machine Learning subject (CS-433).

## Thanks

We express our gratitude to HERUS, in particular to Francisco Xavier Felix Martin Del Campo, our scientific collaborator within HERUS, for his valuable collaboration, his trust, his constant support, and his wise advice throughout the realization of this project.

## Contact
If you have any inquiries, require additional information, or encounter any issues, please feel free to contact the authors via the following email addresses : youssef.belghmi@epfl.ch and hamza.morchid@epfl.ch

We hope that you find our project informative and insightful !
