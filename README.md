# Epicasting: An Ensemble Wavelet Neural Network (EWNet) for Forecasting Epidemics

In this study, we propose a novel MODWT-based auto-regressive neural network model with predefined architecture specially designed for forecasting epidemic dynamics (we refer as "epicasting"). Our study considers publicly available real-world infectious disease datatsets namely - influenza[1], dengue[1-5], hepatitis B[6], and malaria[1] from different regions to analyse the epicasting abiility of our proposed model.

Usage of the repository for the paper "Epicasting: An Ensemble Wavelet Neural Network (EWNet) for Forecasting Epidemics [13]".

* The training phase of the proposed EWNet model initially decomposes an univariate time series into its corresponding *details* and *smooth* coefficients by utlizing a MODWT-based additive decomposition as shown below for Colombia dengue dataset. 
![MODWT_DEC](https://user-images.githubusercontent.com/78313840/174397497-552ff314-e630-45ed-8d45-3c075470563c.png)

Followed by the decomposition, each of the details and smooth series are modelled using an auto-regressive neural network architecture having pre-defined lagged inputs and a single hidden layer to generate one-step ahead forecast. In the subsequent step, the neural network generates multi-step ahead forecasts iteratively and aggregates the corresponding forecasts to generate the final output. Graphical representation of the proposed EWNet model is provided below:
![Model_Img_mod](https://user-images.githubusercontent.com/78313840/174395719-4c5be830-8e78-431e-b90f-4dcd2ec2df35.jpg)


* In this repository, we present application of the proposed EWNet model with 15 epidemic datasets. These datasets are collected from varied open-source platforms and published manuscripts. The ".xlsx" files of these datasets available in [Source](https://github.com/mad-stat/Epicasting/tree/main/Datasets) contains disease incidence data reported on a monthly or weekly basis in different regions. The below map corresonds to the regions and the infectious disease consideered in our study. The map has been generated using this [link](https://www.mapchart.net/).
![Map_Disease](https://user-images.githubusercontent.com/78313840/174397613-f52e8828-764f-4ca3-851e-e21b1007b4b8.png)
  
  
* The [EWNet](https://github.com/mad-stat/Epicasting/blob/main/Models/EWNet.R) file contains the source code and the implemntation of the proposed EWNet model. The proposed framework comprises of two hyper-parameters $(p,k)$, where $p$ denotes the number of lagged input observations and $k$ indicates the number of nodes in the hidden layer of the proposed EWNet model. The hyper-parameter $p$ is tuned by minimising the mean scaled absolue error (MASE) metric on the validation set. The suggested values of this hyper-parameter for different epidemic datasets are made available in the file [EWNet_Parameters](https://github.com/mad-stat/Epicasting/blob/main/Models/Suggested%20hyper-parameter%20values%20of%20EWNet%20model.xlsx). The choice of the hyper-parameter $k$ is made as $k = \frac{(p+1)}{2}$ using valid theoretical justification provided in the manuscript "Epicasting: An Ensemble Wavelet Neural Network (EWNet) for Forecasting Epidemics".  

* The application of different statistical and machine learning forecasting frameworks are available in [Forecasting_Models](https://github.com/mad-stat/Epicasting/blob/main/Models/Forecasting_Model_Implementation.R)[7-11]. Furthermore, deep learning forecasters are implemented using **darts**[12] library in Python, the [Deep Learning Forecast](https://github.com/mad-stat/Epicasting/blob/main/Models/Deep_Learning_Models.py) file contains the required implementations. These state-of-the-art forecasters were used to compare the efficacy of our proposed EWNet model.

* The forecasts generated by the three best performing models in the experimentation: proposed EWNet, ETS, and Hybrid ARIMA-ANN models for the epidemic datasets considered in the study is digramatically represented as follows
![WARNN](https://user-images.githubusercontent.com/78313840/174397904-c16e9dc1-d979-44b5-8492-33d54f441ba7.png)

* Reults obtained in the paper for all these epidemic datasets can directly be computed along with the graphs and figures using the implementation files and datasets given in this repository for replicability and sake of reproducibility of our paper. 

## Citing Our Work
Panja, Madhurima; Chakraborty, Tanujit; Kumar, Uttam and Liu, Nan. "Epicasting: An Ensemble Wavelet Neural Network (EWNet) for Forecasting Epidemics." arXiv preprint cs/2206.10696 (2022+).

@article{panja2022epicasting,\
  title={Epicasting: An Ensemble Wavelet Neural Network (EWNet) for Forecasting Epidemics},\
  author={Panja, Madhurima; Chakraborty, Tanujit; Kumar, Uttam and Liu, Nan},\
  journal={arXiv preprint cs/2206.10696},\
  year={2022+}\
}

## References
* <a id="1">[1]</a> [Disease_outbreak_data](https://github.com/JohannHM/Disease-Outbreaks-Data)
* <a id="2">[2]</a> Enduri, Murali Krishna, and Shivakumar Jolad. "Estimation of reproduction number and non stationary spectral analysis of dengue epidemic." Mathematical Biosciences 288 (2017): 140-148.
* <a id="3">[3]</a> [Hong Kong disease data](https://data.gov.hk/en-data/dataset/hk-dh-chpsebcdde-dengue-fever-cases)
* <a id="4">[4]</a> Polwiang, Sittisede. "The time series seasonal patterns of dengue fever and associated weather variables in Bangkok (2003-2017)." BMC infectious diseases 20.1 (2020): 1-10.
* <a id="5">[5]</a> Chakraborty, Tanujit, Swarup Chattopadhyay, and Indrajit Ghosh. "Forecasting dengue epidemics using a hybrid methodology." Physica A: Statistical Mechanics and its Applications 527 (2019): 121266.
* <a id="6">[6]</a>  Wang, Ya-wen, Zhong-zhou Shen, and Yu Jiang. "Comparison of ARIMA and GM (1, 1) models for prediction of hepatitis B in China." PloS one 13.9 (2018): e0201987.
* <a id="7">[7]</a> Hyndman, Rob J., and Yeasmin Khandakar. "Automatic time series forecasting: the forecast package for R." Journal of statistical software 27 (2008): 1-22.
* <a id="8">[8]</a> Di Narzo, A. F., Aznarte, J. L., & Stigler, M. (2022). Package ‘tsDyn’.
* <a id="9">[9]</a> Kourentzes N. nnfor: Time Series Forecasting with Neural Networks. R package version 0.9. 6.
* <a id="10">[10]</a> Paul, Ranjit Kumar, et al. "Package ‘waveletarima’." Seed 500 (2017): 1-5.
* <a id="11">[11]</a> Scott, Steven L., et al. "Package ‘bsts’." (2022).
* <a id="12">[12]</a> Herzen, Julien, et al. "Darts: User-friendly modern machine learning for time series." Journal of Machine Learning Research 23.124 (2022): 1-6.
* <a id="13">[13]</a> [Epicasting: An Ensemble Wavelet Neural Network (EWNet) for Forecasting Epidemics](https://arxiv.org/pdf/2206.10696.pdf)
