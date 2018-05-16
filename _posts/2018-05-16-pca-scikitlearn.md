---
layout: post
title: Principle Component Analysis with scikit-learn
author: Tim
---

*This post is based on the PCA tutorial by plotly:*

*<a href="https://plot.ly/ipython-notebooks/principal-component-analysis/" target="_blank">https://plot.ly/ipython-notebooks/principal-component-analysis/</a>*



## Loading the Dataset

The iris dataset contains measurements for 150 iris flowers from three different species.

The three classes in the Iris dataset are:

> Iris-setosa (n=50)  
> Iris-versicolor (n=50)  
> Iris-virginica (n=50)  

And the four features of in Iris dataset are:

> sepal length in cm  
> sepal width in cm  
> petal length in cm  
> petal width in cm  

Let's import the dataset using pandas:


```python
import pandas as pd
import numpy as np

df = pd.read_csv(
    filepath_or_buffer='https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data', 
    header=None, 
    sep=',')

df.columns=['sepal_len', 'sepal_wid', 'petal_len', 'petal_wid', 'class']
df.dropna(how="all", inplace=True) # drops the empty line at file-end
```


```python
# split data table into data X and class labels y

X = df.iloc[:,0:4].values
y = df.iloc[:,4].values
```

## Standardizing

Whether to standardize the data prior to a PCA on the covariance matrix depends on the measurement scales of the original features. Since PCA yields a feature subspace that maximizes the variance along the axes, it makes sense to standardize the data, especially, if it was measured on different scales. Although, all features in the Iris dataset were measured in centimeters, let us continue with the transformation of the data onto unit scale (mean=0 and variance=1), which is a requirement for the optimal performance of many machine learning algorithms.

```python
from sklearn.preprocessing import StandardScaler
X_std = StandardScaler().fit_transform(X)
```

## PCA in scikit-learn


```python
from sklearn.decomposition import PCA as sklearnPCA
sklearn_pca = sklearnPCA(n_components=2)
Y_sklearn = sklearn_pca.fit_transform(X_std)
```

## Prepare the PCA plot

### Matplotlib &amp; Seaborn


```python
import seaborn as sns
import matplotlib.pyplot as plt
from matplotlib import rcParams

## Set basic figure style
sns.set_context("talk")
sns.set_style("ticks")
rcParams['font.sans-serif'] = "FreeSans"

## Prepare the figure
for name in ('Iris-setosa', 'Iris-versicolor', 'Iris-virginica'):     
    x = Y_sklearn[y==name, 0]  # Select PC1 data for each species
    y2 = Y_sklearn[y==name, 1]  # Select PC2 data for each species    
    plt.plot(x, y2, "o", alpha=0.6, label=name)

## Style the figure
plt.xlim(-3,4)
plt.ylim(-3,3)
sns.despine(offset=10, trim=True)
plt.title("PCA plot")
plt.xlabel("PC1")
plt.ylabel("PC2")
plt.legend(loc=1, bbox_to_anchor=(1.4, 1))
plt.tight_layout()

## Plot the figure
plt.show()
```


![png]({{ "assets/img/output_19_0.png" | absolute_url }})

