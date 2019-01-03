# Quickdraw doodle recognition


Let's use the Quickdraw project dataset, made available by Google (see https://quickdraw.withgoogle.com/data) to correct images. In the Quickdraw project, about 15 million users, from parts of the world, iterated with a game without which there were six images related to about 345 topics. Each one must be done in, no minimum, three. Once the drawing was updated, the game tried to recognize it. The design of the project was conceived as a representation of concepts pictorially abstract concepts.

In these works, in particular, we will use the Quickdraw dataset to create models that distinguish designs of swans, flamingos and ducks. For each image that saved the use, an image bitmap (28 x 28 pixels) was collected in its class ('duck', 'flamingo' or 'swan') at the same time, it is compatible with the sequence of strokes (traces) an image.

The database was made available together with this file and responded to the `ammd2tp2018.pkl` file. This file contains a list of 57000 drawings. Each drawing is a field label, bitmap and strokes. The label field can assume the values ​​'duck', 'flamingo' or 'swan'. The `bitmap` field is a numpy vector with 784 numbers from 0 to 255, corresponding to the 28x28 pixels of the image corresponding to the drawing. The `strokes` field is a numpy vector with 80 rows. Each row is three columns, _X_, _Y_, and _S_. _S_ indicates a stroke order of zero or, in the case of an invalid stroke. The pair (_X_, _Y_) corresponds to the points that define the stroke. All drawings were chosen instead with Quickdraw (ie, a right class for a neural network with an advantage above a minimum). The following code reads the dataset we are going to use.

## Example drawing

![Example](https://raw.githubusercontent.com/thiagomarquesrocha/quickdraw-doodle-recognition/master/imagens/bitmap.png)

Note that the drawing is made by several strokes (up to 15 at most) and one touch is made by several stitches (up to 80 at the most).

## Neural Networks

* __Bitmap and Strokes__
    * CNN = convolution network that has as input the bitmaps of 28x28 pixels;
    * CNN-D = sequential network (CNN Dilated) that uses as input the strokes;
    * LSTM/GRU = sequential network (LSTM or GRU) that uses as input the strokes;
    
* __Combined__
    * MLP-Bit-Strokes-coders = An MLP that uses 30-dimension _embeddings_ entries created by its CNN and its best model, between CNN-D and LSTM / GRU; 
    * MLP-Bit-Strokes-multi = An MLP that combines its CNN and its best model, between CNN-D and LSTM / GRU; 

![Example](https://raw.githubusercontent.com/thiagomarquesrocha/quickdraw-doodle-recognition/master/imagens/modelos_ammd2.png)

### Install

This project requires **Python 2.7** and the following Python libraries installed:

- [NumPy](http://www.numpy.org/)
- [Pandas](http://pandas.pydata.org/)
- [matplotlib](http://matplotlib.org/)
- [scikit-learn](http://scikit-learn.org/stable/)
- [keras](https://keras.io/#installation)


You will also need to have software installed to run and execute a [Jupyter Notebook](http://ipython.org/notebook.html)

If you do not have Python installed yet, it is highly recommended that you install the [Anaconda](http://continuum.io/downloads) distribution of Python, which already has the above packages and more included. Make sure that you select the Python 2.7 installer and not the Python 3.x installer.

### Run

In a terminal or command window, run one of the following commands:

```bash
ipython notebook quickdraw-doodle-recognition.ipynb
```  
or
```bash
jupyter notebook quickdraw-doodle-recognition.ipynb
```

This will open the Jupyter Notebook software and project file in your browser.

## Data

- 57.000 drawings

### Features

- `bitmap` field is a numpy vector with 784 numbers from 0 to 255, corresponding to the 28x28 pixels of the image corresponding to the drawing
- `strokes` field is a numpy vector with 80 rows. Each row is three columns, _X_, _Y_, and _S_. _S_ indicates a stroke order of zero or, in the case of an invalid stroke. The pair (_X_, _Y_) corresponds to the points that define the stroke

### Target
- `label`: duck-0, flamingo-1, swan-2


