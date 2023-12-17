[scikit-learn]() is an open source Python module from Google that provides commonly needed ML algorithms. 

##### Downloading the module

```
pip install matplotlib
pip install numpy
pip install -U scikit-learn
```

> If there is an error that says 'module not found', install module using pip, and make sure to have a project interpreter in project settings (if using PyCharm).

##### Digits dataset

It also comes with sample datasets to try out things yourself. One of these datasets is a collection of images of hand-drawn digits. The digits dataset consists of 8x8 pixel images of digits. The `images` attribute of the dataset stores 8x8 arrays of grayscale values for each image. The `target` attribute of the dataset stores the digit each image represents

```
# Train usng svm, then predict, show test jpg

clf = svm.SVC(gamma=0.001, C=100)  # gamma low implies accuracy but time
x, y = digits.data[:-10], digits.target[:-10]
clf.fit(x, y)  # This is where the training is happening based on the passed data
clf.predict([digits.data[-1]])

plt.imshow(digits.images[-1], cmap=plt.cm.gray_r, interpolation="nearest")
plt.show()
```

##### Journal notes - Sentdex course

Sentdex YouTube - Scikit-learn course ([link](https://www.youtube.com/watch?v=EQZaSuK-PHs&list=PLQVvvaa0QuDd0flgGphKCej-9jp-QdzZ3&index=29)) <br>Codebase I tried myself - TestXYZ <br>

Chapter 1 - Says how new algorithms rarely need to be written, most of ML is extracting and structiring data <br>Chapter 2 - Predicts digit: Uses `svm` to train using provided data (i.e. does a 'fitting'), and can then predict on a new input <br>Chapter 3 - Basics of stocks stats, D/E ratio<br>Chapter 4 - Lists files in a folder<br>Chapter 5 - Extracting a feature: Extracts data from local files using plain `split`<br>Chapter 6 - Structuring data: Writes exctraced data from local files into one single csv using `Pandas` <br>Chapter 7 - Adds another feature, i.e. stock price and S&P500 price <br>Chapter 8 - Adds another computed column that tracks percentage change <br>Chapter 9 - Plot graphs using data frames <br>Chapter 10 - Labelling data, i.e. based on some calculation give it a label <br>Chapter 11 - Using SVC to predict based on model trained with normalized labeled data, drawing graph <br>Chapter 12 - Gets lot more data from every stock's local files, i.e. lot more dimensions/features to work with <br>Chapter 13 - Does linear SVC on two features with every datapoint having a label <br>Chapter 14 - Uses all the ~35 features, labeled data, Runs SVC with a traing set, tests with a test set, and checks accuracy <br>Chapter 15 - (Skimmed) Randomizes training and testing set <br>Chapter 16 - (Skimmed) Fetching historical sock prices for one stock using a module that makes API calls <br>Chapter 17 - (Skimmed) Does the above for all stocks <br>

Remaining chapters skimmed too, chapters 27 and 28 are where Unsupervised Llearning is used.
