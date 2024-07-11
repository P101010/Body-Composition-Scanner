
# Body Composition Analysis

This project aims to analyse body composition using ML models on subject images to predict waist, hip, and neck circumference. This information is then used to calculate various body composition metrics.

## Project Structure

The main components of the project are as follows:

1. **Image Processing**: Taking front and side images of the subject.
2. **Silhouette Creation**: Using a pretrained ResNet model to create silhouettes from the images.
3. **Feature Extraction**: Extracting features from the silhouettes.
4. **Circumference Prediction**: Training a regression model to predict waist, hip, and neck circumference.
5. **Body Composition Calculation**: Applying formulas to calculate various body composition metrics.

![picture alt](project.png)

## Dataset

### BodyM Dataset

The BodyM Dataset was accessed on 07/02/2024 from [BodyM Dataset](https://registry.opendata.aws/bodym). This is the first large public body measurement dataset, including 8978 frontal and lateral silhouettes for 2505 real subjects, paired with height, weight, and 14 body measurements. 

#### Description

The following artifacts are made available for each subject:

- **Subject Height**
- **Subject Weight**
- **Subject Gender**
- **Silhouette Images**: Two black-and-white silhouette images of the subject standing in frontal and side poses with the full body in view.
- **Body Measurements**: 14 body measurements in cm - ankle girth, arm-length, bicep girth, calf girth, chest girth, forearm girth, height, hip girth, leg-length, shoulder-breadth, shoulder-to-crotch length, thigh girth, waist girth, wrist girth.

The data is split into three sets:
- **Training Set**
- **Test Set A**
- **Test Set B**

For the training and Test-A sets, subjects are photographed and 3D-scanned in a lab by technicians. For the Test-B set, subjects are scanned in the lab but photographed in a less-controlled environment with diverse camera orientations and lighting conditions to simulate in-the-wild image capture. Some subjects have been photographed more than once with different clothing to test the robustness of the dataset.

## Setup and Dependencies

To install the required dependencies, run the following command:

\`\`\`bash
pip install -r requirements.txt
\`\`\`

## Data Preparation

The project uses two main data files:

1. **Measurements File**: Contains the measurements of subjects.
2. **Metadata File**: Contains metadata for the subjects.

## Key Components

### Image Processing

The body composition app first takes the front and side images of the subject.

### Silhouette Creation

A silhouette is created using a pretrained ResNet model. This model is efficient and provides accurate segmentation of the human body.

### Feature Extraction

From the silhouettes, the following features are extracted:

- Area
- Perimeter
- Aspect Ratio
- Solidity
- Area (left)
- Perimeter (left)
- Aspect Ratio (left)
- Solidity (left)

### Circumference Prediction

A regression model is trained to predict the waist, hip, and neck circumference using the extracted features. These models are saved in the `models` directory for ease of use.

### Body Composition Calculation

The following formulas are applied to calculate various body composition metrics:

- **Body Mass Index (BMI)**: \( BMI = rac{weight\_kg}{height^2} \)
- **Fat Mass Index (FMI)**: \( FMI = rac{fat\_mass}{height^2} \)
- **Lean Mass Index (LMI)**: \( LMI = rac{lean\_mass}{height^2} \)

For detailed information, refer to the [paper](https://www.math.csi.cuny.edu/~verzani/Classes/Old/S2005/MTH113/ComputerProjects/HumanBodyII.pdf).

## Running the Project

To run the project, follow these steps:

1. Ensure all dependencies are installed by running `pip install -r requirements.txt`.
2. Run the Jupyter notebook to process the data and make predictions.

---
