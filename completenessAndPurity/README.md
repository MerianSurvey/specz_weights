# Completeness and Purity

By treating the weighted specz subset obtained in the notebook located at `notebook/weights_frankenz_NN.ipnb` as representative, we can examine the color/magnitude space of Merian data and compare it to that of the weighted specz dataset. Differences between the two datasets can be used to determine the completeness and purity of the Merian data. 

The notebooks located in this folder simulate completeness and purity on a "Merian cut" of the COSMOS catalog. Specifically, we take a subset of COSMOS that fits the Merian mass and redshift parameters -- log mass between 8 and 9, and redshift between 0.058 and 0.1. In order to simulate completeness, we randomly remove galaxies from the Merian cut, and in order to simulate purity, we randonly add in galaxies from outside the Merian range into the Merian cut. 

After simulating the Merian cut, we can produce the following figure

![Completeness and purity](https://github.com/MerianSurvey/specz_weights/blob/main/completenessAndPurity/figures/CompPur.jpg)

We were able to make the above figure because in artificially creating a Merian cut we knew how many galaxies were added/lost. With actual Merian data, we will not have that luxury, so being able to determine the completeness and purity based by comparing the representative weighted specz set to Merian data will be useful. 

## Linear Regression

The artificial Merian cut is split into ten mass bins, each with its own completeness/purity label. By generating several artificial Merian cuts, we end up with a collection of data points and labels, which can be used to create a linear regression model. 

The figure below illustrates each data point

![lr data](https://github.com/MerianSurvey/specz_weights/blob/main/completenessAndPurity/figures/compare_mc_specz.jpg)

Each panel of the figure represents a different color band, _g,r,i,z,y_ from left to right. The orange bars represent the magnitude space of the representative dataset for each band, and the blue bars represent the magnitude space of the generated Merian cut. To create data for training a linear regression model to capture purity, we divide each specz bar by its corresponding Merian cut bar. The following figure depicts the results of the model. 

![model output](https://github.com/MerianSurvey/specz_weights/blob/main/completenessAndPurity/figures/purityLR.jpg)

As can be seen from the figure, the model captures the purity of the Merian cut fairly well. It is important to note that completeness & purity selections in the data were made randomly, whereas those depicted in the first figure were made as a function of mass. 

*** 

## Notebooks in This Directory 

* `compPur_LRdata.ipynb` - This notebook creates the data to train and test linear regression models. The basic process is to read in the COSMOS catalog, then make the artificial merian completeness and purity cuts repeatedly. 
* `PurityLR.ipynb` - Runs linear regression on the data created using the above notebook. 
