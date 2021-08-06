# Completeness and Purity

By treating the weighted specz subset obtained in the notebook located at `notebook/weights_frankenz_NN.ipnb` as representative, we can examine the color/magnitude space of Merian data and compare it to that of the weighted specz dataset. Differences between the two datasets can be used to determine the completeness and purity of the Merian data. 

The notebooks located in this folder simulate completeness and purity on a "Merian cut" of the COSMOS catalog. Specifically, we take a subset of COSMOS that fits the Merian mass and redshift parameters -- log mass between 8 and 9, and redshift between 0.058 and 0.1. In order to simulate completeness, we randomly remove galaxies from the Merian cut, and in order to simulate purity, we randonly add in galaxies from outside the Merian range into the Merian cut. 

