# Quickdraw doodle recognition


Let's use the Quickdraw project dataset, made available by Google (see https://quickdraw.withgoogle.com/data) to correct images. In the Quickdraw project, about 15 million users, from parts of the world, iterated with a game without which there were six images related to about 345 topics. Each one must be done in, no minimum, three. Once the drawing was updated, the game tried to recognize it. The design of the project was conceived as a representation of concepts pictorially abstract concepts.

In these works, in particular, we will use the Quickdraw dataset to create models that distinguish designs of swans, flamingos and ducks. For each image that saved the use, an image bitmap (28 x 28 pixels) was collected in its class ('duck', 'flamingo' or 'swan') at the same time, it is compatible with the sequence of strokes (traces) an image.

The database was made available together with this file and responded to the ammd2tp2018.pkl file. This file contains a list of 57000 drawings. Each drawing is a field label, bitmap and strokes. The label field can assume the values ​​'duck', 'flamingo' or 'swan'. The bitmap field is a numpy vector with 784 numbers from 0 to 255, corresponding to the 28x28 pixels of the image corresponding to the drawing. The strokes field is a numpy vector with 80 rows. Each row is three columns, _X_, _Y_, and _S_. _S_ indicates a stroke order of zero or, in the case of an invalid stroke. The pair (_X_, _Y_) corresponds to the points that define the stroke. All drawings were chosen instead with Quickdraw (ie, a right class for a neural network with an advantage above a minimum). The following code reads the dataset we are going to use.


