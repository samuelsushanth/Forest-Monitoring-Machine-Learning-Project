"# Forest-Monitoring-Machine-Learning-Project---Assignment" 

In this report, we analyze the forest cover in the Niokolokoba region. Through various geospatial data techniques, we're able to predict forest cover, calculate carbon emissions from deforestation, and estimate the carbon stock in the region. We use machine learning models and satellite imagery to make our predictions.

add Codeadd Markdown
Methodology
The methodology involves several steps:

Data Collection: Satellite imagery is collected for the Niokolokoba region.
Forest Prediction: Machine learning models are used to predict forest cover for subsequent years.
Carbon Calculations: Using the predicted forest cover, we calculate potential carbon emissions and carbon stock.
Visualization: The data is visualized on a map, providing an interactive tool to monitor forests.
add Codeadd Markdown
Objective
Analyze the dynamics of the Niokolokoba forest in terms of deforestation, reforestation, carbon emissions and carbon stock using satellite images and machine learning predictions.

1. Data Collection
Satellite images of the Niokolokoba forest from 2013 to 2020.
Forest cover predictions stored in '.tif' files for each year.
2. Preliminary Analysis
Visualization of images with rasterio and matplotlib.
3. Calculation of Carbon Emissions
Identification of deforested areas each year.
Emissions calculated using average carbon density.
4. Calculation of Carbon Stock
Estimation of carbon stored in existing forest cover.
5. View on Map
Interactive map created with Folium showing predictions and calculations.
6. Analysis of Deforestation and Reforestation
Areas of deforestation and reforestation identified and visualized.
7. User Interface
Layer controls, captions, tooltips and popups added for interactivity.
8. Challenges and Solutions
Alignment of images and correct representation of carbon stock among the challenges addressed.
9. Conclusion
Valuable information on the health of the Niokolokoba forest was obtained, with an interactive map for stakeholders.

This report summarizes the work carried out. Adjustments may be made based on additional needs or analyses.



## Calculation and visualization of NDVI

We first determine vegetation health using NDVI (Normalized Difference Vegetation Index). This index uses satellite imagery, particularly the NIR (near infrared) and Red bands, to provide a measure of vegetation health.

By calculating the NDVI, we obtain a visual representation where healthy vegetation appears green and areas with little or no vegetation appear shades of red.

Once the NDVI is obtained, we further segment the imagery into vegetation (shown in white) and non-vegetation (shown in black) areas to clearly identify vegetation regions.

---
## Merging raster images

To get a complete view of an area, it is sometimes necessary to merge or stitch together multiple satellite images. Here we combine two images from the year 2013 to demonstrate this process.

The side-by-side view shows the two original images and the resulting merged image.

---

Forest cover modeling using deep learning
1. Data preprocessing:
We define the paths to the mosaic files which contain the satellite images.
The first 6 years of data are used for training and the last 2 for evaluation.
2. Data Labeling:
From NDVI (Normalized Difference Vegetation Index) images, we label areas as forest or non-forest.
Regions with a high NDVI value are considered forest, while those with a low NDVI value are considered non-forest.
3. Extracting patches:
We extract patches or segments from the image.
Patches with a high NDVI value are classified as forest, while those with a low NDVI value are classified as non-forest.
These patches serve as training data for our model.
4. Data Augmentation:
To increase the amount of training data and make the model more robust, we use data augmentation techniques, such as rotating and flipping images.
5. Model Definition:
We use a convolutional neural network (CNN) model with the following architecture: ```

### Forest cover modeling using deep learning

#### 1. **Data preprocessing**:
- We define the paths to the mosaic files which contain the satellite images.
- The first 6 years of data are used for training and the last 2 for evaluation.

#### 2. **Data Labeling**:
- From NDVI (Normalized Difference Vegetation Index) images, we label areas as forest or non-forest.
- Regions with a high NDVI value are considered forest, while those with a low NDVI value are considered non-forest.

#### 3. **Extracting patches**:
- We extract patches or segments from the image.
- Patches with a high NDVI value are classified as forest, while those with a low NDVI value are classified as non-forest.
- These patches serve as training data for our model.

#### 4. **Data Augmentation**:
- To increase the amount of training data and make the model more robust, we use data augmentation techniques, such as rotating and flipping images.

#### 5. **Model Definition**:
We use a convolutional neural network (CNN) model with the following architecture:
\```
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
Conv2D (Conv2D)              (None, 48, 48, 32)        320
_________________________________________________________________
MaxPooling2D (MaxPooling2D)  (None, 24, 24, 32)        0
_________________________________________________________________
Conv2D (Conv2D)              (None, 22, 22, 64)        18496
_________________________________________________________________
MaxPooling2D (MaxPooling2D)  (None, 11, 11, 64)        0
_________________________________________________________________
Flatten (Flatten)            (None, 7744)              0
_________________________________________________________________
Dense (Dense)                (None, 64)                495680
_________________________________________________________________
Dense (Dense)                (None, 1)                 65
=================================================================
\```


#### 6. **Model training**:
- We compile the model using the 'adam' optimizer and the 'binary_crossentropy' loss function.
- The model is trained on the training data for 10 epochs.
- We also validate the model using the evaluation data.

#### 7. **Model evaluation**:
- After training, we evaluate the model's performance on the evaluation data.
- We calculate several metrics such as precision, recall, F1 score and correctness.

#### 8. **Saving model**:
- Finally, we save the trained model for later use.

---

Note that the description above is a high-level simplification of the code to help end users understand the steps without going into technical details.


## Loading and viewing the predicted forest cover

After calculating the NDVI and merging the images, we use a set of predicted forest cover images. These predictions give us insight into how forest cover has changed over the years.

For each predicted year, we visualize:
- The NDVI, indicating the health of the vegetation.
- The NIR band, a component of the satellite image useful for vegetation analysis.
- Predicted forest cover, showing forest areas in green.

---

## Forest cover prediction using our model

We use a pre-trained model to predict forest cover from satellite images. Predictions are based on color bands from satellite imagery as well as other relevant features. The model generates a binary map where regions predicted to be forest are marked white, while other regions are black.

Once these predictions are generated, we combine them with NDVI data and other metrics to get a complete picture of forest health and cover."# Forest-Monitoring-Machine-Learning-Project---Assignment" 
