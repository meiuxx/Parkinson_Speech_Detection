# Branch A: Machine Learning models:

we will train a couple of machine learning (ML) models on our data, tuning for hyperparameters, comparing performance and keeping track to see which model performs best on out audio-extracted features.

We will compare performance of different classical ML models:
*   Logistic Regression
*   Support Vector Machines
*   Random Forest
*   XGBoost
* K-Nearest Neighbours

The different feature selection methods will be explored in different notebooks in the following order:
- **Principal Component Analysis (PCA)**
- Filter-Based Feature Selection (SelectKBest)
- Recursive Feature Elimination (RFE)
- Minimum Redundancy Maximum Relevance (mRMR)

```
with_age="/content/drive/MyDrive/openSMILE_GeMAPSv01b.csv"

with_age="/content/drive/MyDrive/Colab Notebooks/Parkinsons/openSMILE_GeMAPSv01b.csv"

```

when importing data drop sex and ID columns

````
X = df.drop(columns=['ID','Sex', 'label'], axis=1)
````

if needed drop age as well same method

### Scaling:

For tree models (e.g. Random Forests and XGBoost), we must refrain from scaling our data as it might harm the output and the inherent structural workings of tree algorithms. However, for all other non-tree models, we will scale our features using `StandardScaler`.

### Dimentionality reduction.
With a sample space of 81, and a feature space of 63, our data is high-dimensional and risky (overfitting, non-unique solutions...). We apply FS methods after having suicidal thoughts.

### The models set:
We define a dictionary of dictionaries to store the hyperparameter grids for each model. These grids contain various plausible values that will be used later for hyperparameter tuning with `GridSearchCV`.

When using a pipeline (which we would), we need to prefix each parameter for tuning with its equivalent pipeline step name.

PCA params => pca__*

SelectKBest params => select__*

RFE params => rfe__*

mRMR params => mrmr__*

model params => model__*

### Training and Validation
We'll use repeated stratified 5-fold cross-validation on our train data, repeated 13 times. Looping through the different models, we'll define the appropriate pipeline steps (`Pipeline`) depending on the model of our current iteration.

We run `GridSearchCV` through our `param_grid` dictionary to find the best parameters for each of our models, train it through all combinations of parameters, then save the best params, best model and best metrics.

