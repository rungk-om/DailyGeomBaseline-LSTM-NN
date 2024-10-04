# DailyGeomBaseline-LSTM-NN

## Brief Description
This is a repository for the Python codes for training the neural networks to predict the daily component of the geomagnetic baseline 1 hour in advance for the ground geomagnetic measurements made at Chambon-la-Forêt (48.025N, 2.260E), France, Europe. It is a part of the manuscript "A novel neural network-based approach to derive a geomagnetic baseline for robust characterization of geomagnetic indices at mid-latitude" by Kieokaew et al., submitted to Space Weather, accessible [HERE](http://arxiv.org/abs/2410.02311). 

The neural networks consist of multiple-layers and several nodes of LSTM (Long Short-Term Memory) neural networks with a dropout layer. They are built with Tensorflow with Keras-API. We utilise the geomagnetic measurements available from [INTERMAGNET](https://intermagnet.org/), then processed through the filtering technique as described by [Haberle et al. 2022](http://doi.org10.1029/2022JA030407). We train the neural networks using the daily filter data (the sum of 24h, 12h, 8h, and 6h harmonics) at 1 hour cadence as the target, at 1 hour cadence produced using the decimation. The independent or input variables (hourly cadence) consist of the local time, solar zenith angle, the Sun-Earth distance, and the solar radio flux F10.7. The neural networks take 12 hour sequence of the inputs to produce 1 hour forecast of the quiet daily variation. 

There are two Jupyter Notebooks: 
1. DailyQuietVariation_LSTM_Initial.ipynb <- This is to create an initial model of the quiet daily variation.
2. DailyQuietVariation_LSTM_WalkForward.ipynb <- This is to update the initial model using the Walk Forward validation. 

Suggestions for setting up the Python environments (conda, tensorflow, keras) can be found in 'instruction.txt'. 

Data can be found under Data/. There is a single CSV file with columns:
LT: Local Time in hour (0 to 23)
SZA: Solar Zenith Angle (in degrees, 0 to 359)
DistSE: Distance between the Sun and Earth (in Astronomical Units) 
F10.7: Solar radio flux corrected to L1 downloaded from OMNI database (see https://cdaweb.gsfc.nasa.gov/)

The codes may be adapted to use with other ground magnetic observatories. Our codes are under MIT license; you may adapt ours and acknowledge us with the following DOI: 
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.13881560.svg)](https://doi.org/10.5281/zenodo.13881560). 

