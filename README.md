# SVD Application & Machine Learning Pipeline (R)

*A hybrid of SVD, graph analytics, and machine learning models for yield prediction.*

---

## 📌 Overview

This repository contains three R scripts implementing a workflow for:

- Preprocessing hybrid crop yield data  
- Encoding cluster information for **INBRED** and **TESTER** lines  
- Visualizing yield in 3D with regression plane fitting  
- Building classical and neural ML models  
- Performing graph-based analysis using **SVD**  
- Prototyping CNN / DNN structures

The focus is on exploring how **matrix factorization + graph structure + ML models** can be combined for yield prediction and heterotic pattern discovery.

---

## 📂 Repository Structure

```text
SVD_application_ML-master/
│
├── SVD_application      # Main end-to-end pipeline (preprocessing, ML, SVD, graph)
├── SVD_finalfile        # Clean summary of SVD + graph reconstruction
└── cnn_on_progress      # Concept / prototype for CNN-style models in R/TensorFlow


🔧 Dependencies

Below is a clean, GitHub-friendly dependencies block.

R Version

Tested on:

R ≥ 4.0

Required CRAN Packages

Install them in one step:

install.packages(c(
  "scatterplot3d",
  "neuralnet",
  "igraph",
  "ggplot2"
))


These packages support:

scatterplot3d → 3D visualization

neuralnet → feed-forward ANN models

igraph → graph + adjacency matrix operations

ggplot2 → additional plotting (optional)

TensorFlow + TFDatasets + TFEestimators

Install backend packages:

install.packages(c("tensorflow", "tfdatasets", "tfestimators"))


Then install TensorFlow itself:

tensorflow::install_tensorflow()


TensorFlow is needed for:

DNN classifier

CNN experiment prototypes

Feature column APIs for structured data

Optional (Recommended)
install.packages("plotrix")   # for visual distributions
install.packages("reshape2")  # for matrix reshaping
install.packages("dplyr")     # for data manipulation

🧠 Script Breakdown
1️⃣ SVD_application — Main Pipeline

This script runs everything:

Data cleaning

Year & cluster encoding

3D scatterplot + regression plane

GLM modeling

Neural networks (several variants)

TensorFlow DNN

Graph construction

SVD decomposition + reconstruction

Edge list extraction

Key operations include:

s3d <- scatterplot3d(...)
my.lm <- lm(YIELD ~ INBRED_CLUSTER + TESTER_CLUSTER)
s3d$plane3d(my.lm)


Encoding:

levels(train$INBRED_CLUSTER)[levels(train$INBRED_CLUSTER)=="Cluster1"] <- "1"
...


Neural network:

nn <- neuralnet(
  YIELD ~ .,
  train,
  hidden = 20,
  linear.output = TRUE,
  act.fct = "ReLu"
)


Graph & SVD:

df.g <- graph.data.frame(train_extract, directed = TRUE)
X     <- as_adjacency_matrix(df.g)
s     <- svd(X)

2️⃣ SVD_finalfile — Clean SVD Workflow Only

Contains only:

adjacency → SVD

filtering singular values

reconstructing low-rank matrix

rebuilding graph

producing long-format edge table

Perfect for experiments with graph embeddings.

3️⃣ cnn_on_progress — Prototype CNN Work

Contains:

Feature column definitions

Sketch of TensorFlow classifier structures

Notes for future image/tabular CNN models

Not a final model — conceptual only.

📊 Typical Outputs

You will obtain:

trainset_encoded1.csv (encoded dataset)

3D cluster plot with regression plane

GLM summary

Neural net predictions

Accuracy table

Singular value spectrum plot

Low-rank reconstructed adjacency matrix

Graph edge lists (raw & reconstructed)

▶️ How to Run

Clone this repo

Set working directory in R:

setwd("path/to/SVD_application_ML-master")


Run the full pipeline:

source("SVD_application")


Run only SVD:

source("SVD_finalfile")


Inspect CNN prototype:

file.edit("cnn_on_progress")

💡 Use Cases

Yield prediction benchmarking

Studying INBRED–TESTER compatibility

Heterotic group analysis

Graph-based feature extraction

Low-rank structure discovery

Neural vs classical ML comparisons

TensorFlow model experimentation

📬 Contact

Sayane Shome
📧 sayaneshome1@gmail.com

🔗 https://www.linkedin.com/in/sayaneshome

🌐 https://www.sayaneshome1.com
