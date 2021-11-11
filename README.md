# WaveNet for Nuclear Reactor Accident Prediction
<p style='text-align: justify;'> 
This repository demonstrates the implementation of WaveNet model to predict accidents in a pressurized water reactor. The WaveNet is developed with stacked dilated convolution network. The outputs of all layers are combined and extended back to the original number of channels by a series of postprocessing layers, followed by a softmax function. WaveNet has been found to produce state of the art performances in tasks such as audio, text and image generation. However, its predictive capability for multivariate tabular dataset has not been properly verified. </p>

<p style='text-align: justify;'> 
Here, the WaveNet architecture is used to predict accidents in a nuclear power reactor, using multivariate dataset obtained from a desktop simulator. The network implementation, and its performance evaluation for nuclear plant accident prediction can be found in <a href="WaveNet_for_PWR_Accident_Prediction.ipynb">this notebook.</a>  

## Dataset
<p style='text-align: justify;'> 
The dataset is obtained from simulating six different operation conditions of a generic two-loop pressurized water reactor (PWR). The PWR normal operating state and postulated accidents simulated are: Normal operation; Loss of Coolant Accident (LOCA); steam generator tube rupture (SGTR); steam line break inside containment (SLBIC); and loss of AC power (LACP). The features selected to train the model are taken from the sensors that record the average temperature of the reactor coolant system (TAVG, °C), temperatures of the hot leg A (THA,°C), hot leg B (THB,°C), cold leg A & B (TCA and TCB), the steam generator pressure  (PSGA, PSGB) and level (LSGA & LSGB) sensors, the pressurizer level (LVPZ), and the reactor coolant system volume sensor (VOL). The data is cleaned, preprocessed, standardized and splitted to train and test the model.  

## Model
<p style='text-align: justify;'> 
The WaveNet model utilized is inspired by the architecture presented  <a href="https://github.com/ibab/tensorflow-wavenet">here</a>. However, the convolution network uses three dilated layers (i.e. dilation_rate = [1,2,3]), and it is non-causal. The dilated convolution is separated by LeakyRelu and BatchNormalization layers. A flatten layer is added before the output layer to reduce the three-dimensional convolution output to 2D output. Two dense layers are placed at the top to output the model prediction. The final model is as depicted below:

![alt text](Wavenet.png)

   <a href="Wavenet.png">The WaveNet graph</a>   



# Links
[1] WAVENET: [A generative model for raw audio](https://arxiv.org/pdf/1609.03499.pdf)

[2] WaveNet model for accident prediction in a generic pressurized water reactor (under review)
