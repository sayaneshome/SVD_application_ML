SVD Application & Machine Learning Pipeline (R)

This repository contains three self-contained R scripts that collectively implement a workflow for:

Preprocessing hybrid crop yield data

Cluster encoding for INBRED and TESTER lines

Visualization using 3D scatter-plots and regression plane fitting

Classical ML models (GLM, linear regression)

Neural networks using neuralnet

TensorFlow DNN classifiers in R

Graph-based analysis using igraph

Matrix factorization (SVD) and low-rank reconstruction

Early CNN experimentation

The workflow demonstrates multiple ML + graph-analytic approaches for yield prediction and heterotic pattern understanding.

📂 Repository Structure
SVD_application_ML-master/
│
├── SVD_application         # Main script: preprocessing, encoding, NN, GLM, TF, graph SVD
├── SVD_finalfile           # Cleaned summary version of SVD workflow
└── cnn_on_progress         # Early prototype: CNN model development


All files are plain-text R scripts without extensions.

📌 Script Descriptions
1. SVD_application — Full Pipeline (Primary Script)

This is the main and most comprehensive script.
It includes the following:

a. Visualization

Installs & loads scatterplot3d

Plots 3D scatter of
INBRED_CLUSTER × TESTER_CLUSTER × YIELD

Fits regression plane using lm() and overlays it.

b. Data Preparation

Reads dataset: CC2020_train_final.csv

Encodes YEAR values as 0/1/2

Converts cluster categories:
Cluster1 → 1, …, Cluster17 → 17

Writes encoded dataset as:
trainset_encoded1.csv

c. TensorFlow DNN Classifier

Uses:

tfestimators
tfdatasets
tensorflow


Feature columns:

YEAR

LOCATION

INBRED

INBRED_CLUSTER

TESTER

TESTER_CLUSTER

Builds a DNN classifier with hidden layers:
80 → 40 → 30

d. Classical ML Models

Linear regression

GLM (YIELD ~ .)

Train/test split

Neural network using neuralnet

Computes MSE, predictions, accuracy

Visualization using plotdist() and base R plots

e. Graph + SVD Analysis

Creates directed graph from
(LOCATION, INBRED, TESTER)

Converts graph to adjacency matrix

Performs SVD

Zeroes out near-zero singular values

Reconstructs matrix using truncated components

Builds reconstructed graph

Converts graph into long-data format with edge listings

This section demonstrates how SVD can reveal latent structure in hybrid relationships.

2. SVD_finalfile — Clean Summary Script

This file is a simplified, cleaner version of the SVD workflow.

It contains:

SVD decomposition

Filtering of small singular values

Low-rank reconstruction

Graph reconstruction

Use this script when you only want the SVD + graph component without ML or encoding steps.

3. cnn_on_progress — CNN Prototype (Work in Progress)

A short conceptual outline for:

Feature columns

DNN / CNN definitions

TensorFlow classifier structure

This file is not a complete model but contains early experimentation ideas and reference function signatures.

🔧 Dependencies
CRAN Packages
scatterplot3d
neuralnet
igraph
tensorflow
tfestimators
tfdatasets


Install TensorFlow for R:

install.packages("tensorflow")
tensorflow::install_tensorflow()

🚀 How to Run
1. Run the full pipeline
source("SVD_application")


This will:

Preprocess the dataset

Fit regression & NN models

Train TensorFlow classifier

Perform graph + SVD analysis

2. Run only SVD + graph reconstruction
source("SVD_finalfile")

3. View CNN prototype
file.edit("cnn_on_progress")

📊 Outputs

Depending on which parts of the script are executed, you will obtain:

Encoded dataset: trainset_encoded1.csv

3D scatterplots + regression plane

Neural network prediction table:

predictions | realvalues | accuracy


Plots of feature distributions

Singular value spectrum plot

Long-format graph edges from adjacency matrix

✨ Purpose of the Project

The repository demonstrates a hybrid analytical approach combining:

Yield prediction

Cluster feature engineering

Deep learning in R

Graph structural analysis

Low-rank matrix approximation

Such workflows are useful for:

Hybrid performance modeling

Heterotic pattern detection

Latent feature extraction

Low-rank graph embeddings

Experimental comparison of ML methods

📬 Contact

For questions, improvements, or collaboration:

Sayane Shome
📧 sayaneshome1@gmail.com

🔗 https://www.linkedin.com/in/sayaneshome

🌐 https://www.sayaneshome1.com
