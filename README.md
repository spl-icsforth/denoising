# Denoise-Galaxy-Spectra
### **Code for Denoising of Spectroscopic Data**


# Table of contents
1. [Introduction](#introduction)
2. [Dependencies](#paragraph1)
3. [Execution](#paragraph2)

## Introduction <a name="introduction"></a>
This repository contains MATLAB codes and scripts designed for the denoising of spectroscopic data.
The proposed approach synthesizes a denoised spectral profile from its corresponding noisy acquired 
version by capitalizing on the Sparse Representations (SR) learning framework. According to the SR framework,
various spectral profiles can be represented as sparse linear combinations of elements from learned over-complete dictionaries.

## Dependencies <a name="paragraph1"></a>

**Dataset** 

* The dataset contains simulated cosmological data modeled after the upcoming Euclid satellite galaxy survey. 

* Specifically, the dataset contains 13709 examples of full spectral energy distribution (SED) of galaxies, 
  each one encoding the spectral profile over 3750 wavelengths 1.1 \- 2.0 micrometers. 

* We utilized 7000 examples for training the coupled dictionaries and evaluate the performance of the proposed 
  method on the remaining examples. 

**Noise Conditions**

* **High SNR**: the peak of an Ha line at Euclid's flux limit has 3.5 sigma.

* **Medium SNR**: the integrated Ha flux at Euclid's flux limit has 3.5 sigma. This is the
  official survey specification.

* **Low SNR**: the integrated Ha flux at Euclid's flux limit is at noise level (sigma = 1).

In this example, we experiment with medium SNR noise conditions.

**Dictionaries**

* Regarding the dictionary training phase, we designed coupled dictionaries that model both the clean 
  and the noisy feature spaces, based on a ADMM Sparse Coupled Dictionary Learning scheme.

* We trained 5000 representative dictionary atoms from 7000 couples 
  of training spectral templates.

**In order to run the code, both the data and the dictionaries must be downloaded:** 

* This link provides the sample data:
[link](https://www.dropbox.com/sh/bh7mhnstk393q7g/AADx6rPJt1hX_0lhMJB3AmoCa?dl=0)

* This link contains the coupled dictionaries, that are utilized for the sparse decomposition.
[link](https://www.dropbox.com/sh/fkvxjfor14k4hwu/AAB20Iz0LI84NBxCoK6V9cQca?dl=0)

**Both the data and the dictionaries should be placed in the same folder**

## Execution <a name="paragraph2"></a>

The primary function is **Sc-Denoising.m** which is designed to take a sequence of observed, degraded spectral profiles,
the coupled dictionaries, and a sparsity regularization parameter , and attemp to reconstruct the high-resolution spectral profiles.

**Input Arguments**

* **Mid\_SNR\_Noisy\_region\_of\_interest**: Input noisy testing spectral profiles

* **D_clean** : Clean, high resolution dictionary

* **D_noisy** : Noisy, low resolution dictioanary

* **lambda**  : sparsity regularization parameter

**Output Arguments**

* **reconstructed\_signal\_from\_Mid_SNR** : Output, denoised spectral profiles

The primary script that loads the data, the dictionaries and provides visual results of the reconstructed spectral profiles 
is **demo.m**

In the **demo.m**, we reconstruct the denoised spectral profiles from Medium SNR noise conditions. 



