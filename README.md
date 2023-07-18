# Approaches of Applying Deep Learning in Physical Layer

## Introduction

In this project I try some algorithm used for the communication process in physical layer, construct a neural network autoencoder to replace the algorithmic processes, and finally construct a residual binarized neural network software for the model.

## Content

* Modulation constellation points and noise effect
* Modulation with and without encoding and Block Error Ratio for different SNR
* A comparison between Autoencoder and Reed Solomon encoding algorithm
* The residual Binarized Neurak Network Autoencoder

## Libraries

* Tensorflow
* Keras
* Pyitpp
* Numpy
* Matplotlib

## Usage

* Importing pyitpp <br/>
  pyitpp is a pybind library of the itpp library for C++. <br/>
  The python version (pyitpp) doesn't have Reed Solomon encoding, so to be able to use Reed solomon you should follow the instructions after running the first two cells in (autoenco VS RS.ipynb) and use them for (autoenco VS RS.ipynb),(uncoding&coding.ipynb)
* for more info about installing pyitpp check this repo https://github.com/vidits-kth/py-itpp
