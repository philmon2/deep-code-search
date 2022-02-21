# Deep Code Search

This is a fork (with some adjustments) of the official [Deep Code Search](https://github.com/guxd/deep-code-search/tree/master/pytorch) implementation .


## Basic Setup
### Requirements
* Install **Python 3.6**. You may find it beneficial to use a virtual environment. Consider _miniconda_ or _venv_.
* Install dependencies:
 ```
pip install -r requirements.txt
 ```
 
### Retrieve pre-trained model
```
pip install gdown
mkdir -p ./output/JointEmbeder/github/202106140524/models/
cd ./output/JointEmbeder/github/202106140524/models/
gdown --id 1xpUXsSFbULYEAs8low5zQZWK7-wmqTNO
```

### Retrieve raw java dataset 
  The `/data/github` folder provides a small dummy dataset for quick deployment. Let's remove it and replace it with the real dataset:
  ```
  cd data/github
  rm *
  gdown --id 11Iia3ZyNuD-TYeymo8I3hU1YTNweY9_i
  gdown --id 1FYfNZKNUXaYTKuOhwY3POhnUGpnQuZOe
  gdown --id 10FgMDxW5VIO49MxxcYXvH07FYK0kxVqY
  gdown --id 1yQwqzx7hW7qMGnRDOolI_vYZDNN0_SoA
  unrar x use.rawcode.rar 
  ```
  
Note: you can ignore the `/data/example` folder. Since the model only uses the dataset in `/data/github`.

### Evaluate model
   ```
   python repr_code.py -t 202106140524 --reload_from 4000000
   python search.py -t 202106140524 --reload_from 4000000
   ```
 
## Code Structures

 - `models`: neural network models for code/desc representation and similarity measure.
 - `modules.py`: basic modules for model construction.
 - `train.py`: train and validate code/desc representaton models; 
 - `repr_code.py`: encode code into vectors and store them to a file; 
 - `search.py`: perform code search;
 - `configs.py`: configurations for models defined in the `models` folder. 
   Each function defines the hyper-parameters for the corresponding model.
 - `data_loader.py`: A PyTorch dataset loader.
 - `utils.py`: utilities for models and training. 

```
