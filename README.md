# Lyrics Generator

This is a small experiment in generating lyrics with a recurrent neural network.

## Train the model

### Install dependencies

`pip install -r requirements.txt`

the requirement file has been reduced in size so if any of the scripts fail,
just install the missing packages :-)

### Get the data

- Download the [songdata dataset](https://www.kaggle.com/mousehead/songlyrics).
  - Save the `songdata.csv` file in a `data` sub-directory.
- Download the [Glove embeddings](http://nlp.stanford.edu/data/glove.6B.zip)
  - Save the `glove.6B.50d.txt` file in a `data` sub-directory.

### Run the training

`python train.py`

This command takes care of all the training. Warning: it takes a very long
time on a normal CPU!

## Create new lyrics

`python cli.py lyrics model.h5 tokenizer.pickle`

Try `python cli.py lyrics -h` to find out more

## Export to Tensorflow JS (used for the app)

`python cli.py export model.h5 tokenizer.pickle`

This creates a sub-directory `export` with the relevant files (can be used for the app)

## Single-page "app" for creating lyrics

The `lyrics-tfjs` sub-directory has a simple web-page that can be used to
create lyrics in the browser. The code expects data to be found in a `data/`
sub-directory. This includes the `words.json` file, `model.json` and any extra
files generated by the Tensorflow export.