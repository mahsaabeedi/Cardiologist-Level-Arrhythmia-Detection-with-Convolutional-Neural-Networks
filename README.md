## Introduction

Develop a model which can diagnose irregular heart
rhythms, also known as arrhythmias, from single-lead ECG
signals better than a cardiologist. Key to exceeding expert performance is a deep convolutional network which
can map a sequence of ECG samples to a sequence of arrhythmia annotations along with a novel dataset two orders
of magnitude larger than previous datasets of its kind.



## Install 

Clone the repository

```
git clone git@github.com:awni/ecg.git
```

If you don't have `virtualenv`, install it with

```
pip install virtualenv
```

Make and activate a new Python 2.7 environment

```
virtualenv -p python2.7 ecg_env
source ecg_env/bin/activate
```

Install the requirements (this may take a few minutes).

For CPU only support run
```
./setup.sh
```

To install with GPU support run
```
env TF=gpu ./setup.sh
```

## Training

In the repo root direcotry (`ecg`) make a new directory called `saved`.

```
mkdir saved
```

To train a model use the following command, replacing `path_to_config.json`
with an actual config:

```
python ecg/train.py path_to_config.json
```

Note that after each epoch the model is saved in
`ecg/saved/<experiment_id>/<timestamp>/<model_id>.hdf5`.


## Testing

After training the model for a few epochs, make predictions with:

```
python ecg/predict.py <dataset>.json <model>.hdf5
```

replacing `<dataset>` with an actual path to the dataset and `<model>` with the
path to the model.




