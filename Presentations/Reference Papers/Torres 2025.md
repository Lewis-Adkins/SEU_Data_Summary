**Title:** A Machine Learning Approach to Predicting SEP Proton Intensity and Events Using Time Series of Relativistic Electron Measurements
**Authors:** Jesse Torres, Phillip K. Chan, Lulu Zhao, Ming Zhang
**Publisher**: AGU
**DOI:**  [10.1029/2024SW003921](https://doi.org/10.1029/2024SW003921)

# Abstract

SEP can cause damage to space equipment. physics based models to forecast SEP events and intensity is default with lack of understanding certain processes. We attempt to apply neural networks to forecast intensity of SEP events with time series with electron/proton flux in 5 min intervals to predict proton flux 30 min or 1 hr ahead. also used is RNN. both single models and ensemble of models trained on data re tested. Single RNN model forecasts proton flux of each event with less error as well as predicting proton flux. only downside is time lag larger than the matrix method proposed by (Posner 2007).
# 1. Introduction

Solar Energetic Particles are high energy particles from the sun that can cause harm to sensitive equipment in space. The intensity of events is measured in proton flux. SEP contains many species: protons, alpha particles, heavier nucleon, and electrons with high energy protons the biggest concern as they are the most abundant and difficult to shield. Electrons travel faster because of lesser scattering than protons. electrons with energies kEV to a few MeV are almost in every event with high energy SEP protons are observed according to (Posner 2007) and precedes that of protons by 10s of minutes, therefore measuring of relativistic electrons can become an advanced signal for the arrival of more lethal protons.

**Goal of work is measure relativistic near relativistic SEP electron to predict 10 MeV SEP proton intensity **

Predicted intensity is proton flux measured continuously over time. time series data for features which precede the eent in order to predict a time series of proton flux is used. fixed window of time containing past and current values of proton and electorn flux in measurement cadence intervals are used for input to predict proton flux .5 to an 1 hour into future.

# 2. Related Work

Read Section in paper for all references with specific methods but there are 3  general methods to predicting SEPs
## Solar Flares
* Uses post eruptive observations of solar flared to forecast or nowcast SEP
* Solar flared from the suns magnetic field measurement forecasting SEPs
* Perform a spectral analysis of hard x-ray bursts and uses the, to determine whether an SEP will occur based on the hardening of the spectral index.
	* Preduct the magnitude of the event by applying an empirical function using the max temeprature and max X-ray flux
* Proton Prediction System (PPS) uses peak X-ray flux and the X-ray flare rise time in order to forecast peak proton flux
	* If predicted proton flux exceeds 10 proton flux unit (pfu) then an SEP event has occurred.
	* Location of solar flare us used by the PPS to predict the onset and peak times of SEP
* Nunex 2011 two models, the first time derivatives of X-Ray and proton fluxes are found to be correlated
	* One for magnetically well connected events
		* use the correlation and the associated solar flare to predict SEP proton event
	* One for magnetically poorly connected events
		* ensemble of model trees is used to predict future proton flux
## CMEs
* CMEs require image processing and recognition from observations in application to real time SEP prediction so less popular
	* Forecasting SEP using near real time temporal candence (15 s)  of K-cor observations
		*  Mauna Loa Solar Observatory (MLSO) was first to issue warning compared to all other predicted techniques
	* Formula uses speed and connection angles of CMEs to predict the peak intensity of 14-24 MeV protons
		* overpredicts
		* Used to forecast SEP by threshold of proton flux $10^{-4}$ MeV/s/ cm^2/sr
# Relativistic Electrons as an Advanced Signal 
(Posner 2007)
the topic of this research

# 3. Approach

Electron faster than protons from low scattering. use time series of past and current electron and proton intensity measurements and their time derivatives to forecast proton intensity ahead of time. Process similar to Posner 2007 but this time with machine learning.

## 3.1 Input and Output for Forecasting Proton Intensity

* Times series of particles measurements to predit future >10 MeV Proton intensity.
* time window of the past 2 hr up to the current time is used to predict output proton flux at 30 min or 1 hr from current time. 
* candance of input data is 5 min.
* Times $t$
	* $t$ =  current time
	* $t+1$ =  5 min after current time
	* $t-1$ = 5 min before curent time
	* input time window = $[t-24, t]$ 
	* output $t+6$ or $t+12$ 
*  Electron intensities from >.25 and >.67 MeV channels 
	* Channels can contribute +/- to overall integral flux
* Proton intensities form the >10 MeV channel obtained by the EPHIN instrument on SOHO at L1 
	* Proton intensity calucalted from differential fluxes throuhgh integration over energy
* Define three phases  for SEP Event identified with separate program
	* Rising - between onset and peak
	* Falling - between peak and end
	* Background any time outside duration of SEP event

## 3.2 Basic Approach With One Model
Refered to as M1 (One mode for intensity prediction) compared to multilayer perceptron algrotihm (NN - neural network) to recurrent NN (RNN) RNN designed for time series data

Keras implmenation in python to create models with Gated Recurrent Units (GRU) layer

## 3.3 Multiple Models

Substantial imbalance between background flux and SEP events so M1 could miss most rare SEP events. Multiple models are used instead to fix using the same archtect in [[#Basic Approach With One Model]] 

Two stages training:
* First training stage is model selection
* Proton flux prediciton traiing stage

New approach M3 (Three models for intensity prediction)
# 4. Experimental Evaluation
Two forcasting tasks:
1. Forcast proton intenisty 30-60 min ahead
2. Forecast occurrence of SEP events 30-60 min ahead
## 4.1 Evaluation of SEP Time - Intensity Profile Prediction

### 4.1.1 Evaluation Criteria

Intensit models evaulted using mean absoulte error (MAE), the difference between the actuala and predict value at each timesamp. Calculate MAE only for the events found within test set then average over all events from rising portion.

mesaure lag for on time or too late. shift prediction between onset and peak of each event in test set aligning with targets. Shift with lowest MAE is considered lag

### 4.1.2 Learning and Evaluation Procedures

first 80% of data for training while remaining 20% for testing. 
21 SEP events in training and 18 in test

#### 4.1.2.1 Phase - Selection Model Procedures

RNN tested with class weights was determined to be the best at distinguishing background from rising
All tests compared with and without nn weights
3x3 confusion matrix for three classes of background, rising, and falling
Model selector by Torres 2020

#### 4.1.2.2 Baseline Methods Used for Comparison 

Compared to persistent model, a simple baseline method in which the predicted proton flux value is the current proton flux value, which is equivalent to nowcasr

Also compared to matrix method to posner.

In this implementation mainted same number of matrix cels and clip the input parameter values such that all cells have at least one instance, and therefore can predict a proton intensity using any cell.

### 4.1.3 Results of Predicting SEP Time - Intensity Profile

Compared all all models with NN or RNN with and w/o phases, M1 or M3 at both $t+6$ and $t+12$

#### 4.1.3.1 Sample Prediction Plots

Some statments on overpredicting and and mapping the rising, peak, and falling on plots based off models

#### 4.1.3.2 Analysis of Results

Prediction of proton intensity vs actual proton intensity lines up well so predicitons are good.

## 4.2 Evaluation of SEP Event Forecasting

### 4.2.1 Evaluation Criteria

Setting up a warning system to put onboard satellite to tell wheterh a  predicted proton flux evetn will happen or not

# 5. Conclusion

single RNN midek oerfirns better for proton flux prediciton, less MSE in predcitng proton flux but larger lag!


# Data Availability Statement
* Muller - Mellin et al (1995)
* NOAA National Center for Enviromental Inoomation
* SOHO/EPHIN Porject
* Data code available here