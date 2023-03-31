# ML_Pyrite

## Overview
This repository contains data source and codes used in the paper entitled "Machine learning analysis of trace element data distinguishes sedimentary and hydrothermal pyrite" by J. Kang et al. We trained two supervised machine learning algorithms on a large LA-ICP-MS pyrite trace element database to distinguish pyrite of different origins. The analysis validated several trace elements (Co, Ni, Cu, Zn, As, Mo, Ag, Sb, Te, Au, Tl, and Pb) as excellent predictors of pyrite origins. Further statistical analysis suggests four trace element clusters behaving differently among sedimentary (syngenetic and early diagenetic), synsedimentary hydrothermal (syngenetic hydrothermal), and post-sedimentary hydrothermal (epigenetic hydrothermal) pyrite, which is probably driven by chemical and physical properties of source fluids, interactions between elements, competition among coprecipitating minerals, and pyrite growth rate. Armed with this initial success, we then demonstrated the efficacy of this approach in identifying the origins of the isotopically superheavy pyrite in the Cryogenian Tiesi’ao and Datangpo formations and the pyritic rims associated with fossiliferous chert nodules in the Ediacaran Doushantuo Formation of South China. We compiled 1 data source and 4 codes to generate the diagrams in Fig. 2-Fig. 4 and supplementary figures. Here is the list of data and code files.

## Data files
In all data files, sedimentary, synsedimentary hydrothermal, and post-sedimentary hydrothermal pyrite are labeled as 0, 1, 2, respectively.
  - [Training.csv](data/Training.csv) includes 3207 analyses for training (720 analyses) and initial testing (2487 analyses). 
  - [Blind_Test.csv](data/Blind_Test.csv) includes 425 analyses from deposits/units not seen in the training and initial testing datasets were used for blind testing.
  - [Xiao_Cui.csv](data/Xiao_Cui.csv) includes LA-ICP-MS trace element analyses of samples from Cui et al. and Xiao et al. projects.
  - [TE_Data.csv](data/TE_Data.csv) includes all analyses (3632) used for supervised machine learning model training and testing (including blind testing). This data file was used to conduct HCA and PCA analyses.

## Code files
Update the path of data files in every code file before running
  - [RF_XG.ipynb](code/RF_XG.ipynb): Distinguishing sedimentary and hydrothermal pyrite using Random Forests and XGBoost with LA-ICP-MS pyrite trace element database. 240 pyrite analyses from each label (sedimentary, synsedimentary hydrothermal, and post-sedimentary hydrothermal) were randomly selected from [Training.csv](data/Training.csv) to form a balanced training dataset.
  - [Ternary.ipynb](code/Ternary.ipynb): Ploting the model predictions on Cui et al. and Xiao et al. samples as ternary plots. Must run RF_XG.ipynb first.
  - [Cluster.ipynb](code/Cluster.ipynb): Conducting hierarchical cluster analysis on power transformend trace element database.
  - [PCA.ipynb](code/PCA.ipynb): Conducting principla component analysis on power transformed trace element database.

## Software Requirements
The codes used in this paper were compiled on Python 3.10.4. All codes were written using Jupyter Notebook. To run the codes, install [Jupyter Noterbook/JupyterLab](https://jupyter.org/install) first.
The versions of other packages are, specifically:
```
numpy==1.22.3
pandas==1.4.3
plotly==5.9.0
matplotlib==3.5.1
sklearn==1.1.1
xgboost==1.6.1
seaborn==0.11.2
scipy==1.7.3
```
