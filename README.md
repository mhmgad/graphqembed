## NetQuery: Learning to Query Complex Networks

#### A fork from William L. Hamilton repositry

Code for making predictions about logical queries using network embeddings and for 
reproducing the results of the paper "Querying Complex Networks in Vector Space."

### Setup and requirements

Run `pip install -r requirements.txt` to obtain the necessary requirements.
The primary requirements is pytorch with version >=3.0.
You may want to use a [virtualenv](https://virtualenv.pypa.io/en/stable/) or [Docker](https://www.docker.com/).

The biological interaction network data used in the paper can be downloaded [here](https://snap.stanford.edu/nqe/bio_data.zip).
Unzip the data in your working directory.

### Running the code

To train a model on the Bio data, run `python -m netquery.bio.train`.
See that file for a list of possible arguments, and note that by default it assumes that the data is in a subdirectory of your working directory (i.e., "./bio_data).
By default the model will log its output and store a version of the model after training.
The train, test, and validation performance will be recorded in the log file. 
If you are training with a GPU be sure to add the cuda flag, i.e., `python -m netquery.bio.train --cuda`. 
The default parameters correspond to the best performing variant from the paper. 

### Using the model for predictions

We added a script `predict.py` to allow using the model to make canonical prediction using a pre-trained model:
run  `python -m netquery.bio.predict --saved-model <model_file>` and it will read the test queries from the data folder. 


NB: Currently the training files are not-portable pickle files. 
We hope to release a more portable version of the data soon.

NB: Only the bio data is currently publicly available. 
