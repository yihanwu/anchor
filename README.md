## What is `anchor`?

Anchor is a python package to find unimodal, bimodal, and multimodal features in any data that is normalized between 0 and 1, for example alternative splicing or other percent-based units.

* Free software: BSD license
* Documentation: https://YeoLab.github.io/anchor

## Installation

```
git clone https://github.com/yihanwu/anchor.git
cd anchor
pip install -r requirements.txt
```

## Usage

`anchor` was structured like `scikit-learn`, where if you want the "final
answer" of your estimator, you use `fit_transform()`, but if you want to see the
intermediates, you use `fit()`.

If you want the modality assignments for your data, first make sure that you
have a `pandas.DataFrame`, here it is called `data`, in the format (samples,
features). This uses a log2 Bayes Factor cutoff of 5, and the default Beta
distribution parameterizations (shown [here]())

```python
import anchor

bm = anchor.BayesianModalities()
modalities = bm.fit_predict(data)
```

If you want to see all the intermediate Bayes factors, then you can do:

```python
import anchor

bm = anchor.BayesianModalities()
bayes_factors = bm.fit(data)
```


## History

### Modifications to be made on this fork

- change readme based on pull request [here](https://github.com/YeoLab/anchor/pull/1)
- integrate new (version > 0.7) seaborn palette changes from [pull request](https://github.com/YeoLab/anchor/pull/2)
- change minor import differences
- copy package requirements into requirements.txt (see [this commit](https://github.com/YeoLab/anchor/blob/8d0505bba9a8695070fa3bc4c8c033f55b08cb16/environment.yml) for original package requirements)
- change cross_validation.Bootstrap to KFold (n_splits=2, train_size = 0.5)

### 1.1.1 (2017-06-29)

- In `infotheory.binify`, round the decimal numbers before they are written as strings

### 1.0.1 (2017-06-28)

- Documentation and build fixes

### 1.0.0 (2017-06-28)

* Updated to Python 3.5, 3.6

### 0.1.0 (2015-07-08)

* First release on PyPI.
