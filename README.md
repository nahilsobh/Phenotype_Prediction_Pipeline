# KnowEnG's Phenotype Prediction Pipeline
This is the Knowledge Regression for Genomics (KnowEnG), an NIH BD2K Center of Excellence, Phenotype Prediction Pipeline that will be used to **infer** an 'omic'-drug association.

The user will need to do of the following in order for the system to learn how to **predict** the phenotype through regression:
 * User must submit an ‘omic’ spreadsheet with samples as columns and genes as rows. 
 * User will also need to submit a phenotype value for each sample.

This will allow one to:
 * Identify the best drug for a patient.

Given an omic spreadsheet of a collection of genes as well as the supplied phenotype value, the user will need to choose one of these options:

| **Options**                                      | **Method**                           | **Parameters** |
| ------------------------------------------------ | -------------------------------------| -------------- |
| Elastic Net                                      | Elastic                              | elastic_net    |
| Lasso                                            | Lasso                                | Lasso          |

* * *
## How to run this pipeline with our data
* * *

### 1. Clone the Phenotype_Prediction_Pipeline
```
 git clone https://github.com/KnowEnG/Phenotype_Prediction_Pipeline.git
```
 
### 2. Install the following (Ubuntu or Linux)
  ```
 apt-get install -y python3-pip
 apt-get install -y libblas-dev liblapack-dev libatlas-base-dev gfortran
 pip3 install numpy==1.11.1
 pip3 install pandas==0.18.1
 pip3 install scipy==0.18.0
 pip3 install scikit-learn==0.17.1
 apt-get install -y libfreetype6-dev libxft-dev
 pip3 install matplotlib=1.4.2
 pip3 install pyyaml
 pip3 install knpackage
```

### 3. Change directory to Phenotype_Prediction_Pipeline

```
cd Phenotype_Prediction_Pipeline
```

### 4. Change directory to test

```
cd test
```

### 5. Create a local directory "run_dir" and place all the run files in it
```
make env_setup
```

### 6. Select and run a phenotype prediction option:
  
 * Run Elastic Net pipeline</br>
  ```
  make run_elastic_predict
  ```
 
 * Run Lasso pipeline</br>
 ```
 make run_lasso_predict
 ```
 
__***Follow steps 1-3 above then do the following:***__

### * Create your results directory
 
 ```
 mkdir results_directory
 ```
 
### * Create run_parameters file (YAML Format)
 
 Look for examples of run_parameters in:
  ```
  Phenotype_Prediction_Pipeline/data/run_files BENCHMARK_2_ElasticNet.yml
  
  Phenotype_Prediction_Pipeline/data/run_files BENCHMARK_1_PPP_Lasso.yml

  ```
 
### * Run
Using Elastic net
  ```
 python3 ../src/phenotype.prediction.py -run_directory ./run_dir -run_file BENCHMARK_2_ElasticNet.yml
  ```
Using Lasso
 ```
 python3 ../src/phenotype.prediction.py -run_directory ./run_dir -run_file BENCHMARK_1_PPP_Lasso.yml
 ```
 
 * * *
 ## Description of "run_parameters" file
 * * *
 
| **Key**                   | **Value** | **Comments** |
| ------------------------- | --------- | ------------ |
| method                    | Elastic Net  | http://scikit-learn.org/stable/modules/linear_model.html#elastic-net |
| results_directory | directory | Directory to save the output files |

spreadsheet_name = features_train_clean.df</br>
response_name = response_train_clean.df</br>
test_spreadsheet_name = features_test_clean.df

 * * * 
 ## Description of Output files are saved in results directory
 * * * 
 
 | **Gene Name** | **Prediction**|
 | ------------- | ------------- |
 | User Gene 1   | Float         |
 | ...           | ...           |
 | User Gene n   | Float         |
 
  
