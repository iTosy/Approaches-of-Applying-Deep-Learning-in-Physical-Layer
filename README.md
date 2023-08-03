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
  The python version (pyitpp) doesn't have Reed Solomon encoding, so to be able to use Reed solomon you should add these files in pyitpp/src/comm:
#### reedsolomon.h
#include <pybind11/pybind11.h>
#include <pybind11/operators.h>


#include <itpp/comm/reedsolomon.h>


namespace py = pybind11;





void generate_pybind_wrapper_for_itpp_reedsolomon_class( py::module &m, const char * name ) {


  py::class_<itpp::Reed_Solomon>( m, "Reed_Solomon" )
    .def( py::init<short, short,const bool,const short>() )


    .def("encode", static_cast<void (itpp::Reed_Solomon::*)(const itpp::bvec &, itpp::bvec &)>(&itpp::Reed_Solomon::encode))
    .def("encode", static_cast<itpp::bvec (itpp::Reed_Solomon::*)(const itpp::bvec &)>(&itpp::Reed_Solomon::encode))



    .def("decode", static_cast<void (itpp::Reed_Solomon::*)(const itpp::bvec &, itpp::bvec &)>(&itpp::Reed_Solomon::decode))
    .def("decode", static_cast<itpp::bvec (itpp::Reed_Solomon::*)(const itpp::bvec &)>(&itpp::Reed_Solomon::decode))


    .def("get_rate", &itpp::Reed_Solomon::get_rate)
    
  ;
}

#### reedsolomon.cpp

#include "reedsolomon.h"

PYBIND11_MODULE(reedsolomon, m)
{
  generate_pybind_wrapper_for_itpp_reedsolomon_class( m, "Reed_Solomon" );
}

#### (add this line in the end in [__init__.py])

from .reedsolomon import *

* for more info about installing pyitpp check this repo https://github.com/vidits-kth/py-itpp
