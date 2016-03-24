---
title: MS Azure Machine Learning
layout: post
---

Table of contents:

* [Sign Up](#sign-up)
* [Add a Dataset](#add-a-dataset)
* [Add a Script](#add-a-script)
* [Create a Notebook](#create-a-notebook)

## 1. Sign Up

Go to [https://studio.azureml.net](https://studio.azureml.net), create a new user or simply sign up with your good old Microsoft account. If you manage to do this, you'll get an e-mail like this:

> Hello awesome@email.com!
> Your sign-up for the Free tier of Azure Machine Learning is complete. You can start building advanced analytic solutions using Azure Machine Learning Studio.

So far, so good!

## 2. Add a Dataset

After you sign in or sign up, go to the [Azure Studio](https://studio.azureml.net/Home/) and add a dataset from samples.

You see, a number of sample data sets are included by default. Many of these sample data sets are included as examples of various types of data typically used in machine learning. They are listed under **Saved Datasets** in the module palette to the left of the experiment canvas. You can use any of these data sets in your own experiment by dragging it to your experiment canvas.

<p class="centered-img"><img src="/assets/sample-datasets.png"></p>

Some of these datasets may be familiar to you – for example, the **Iris Two Class Data** database, which is used in every other tutorial. Let's pick something more interesting... for example, **IMDB Movie Titles**:

> The dataset contains information about movies that were rated in Twitter tweets: [IMDB](http://www.imdb.com) movie ID, movie name and genre, production year. There are 17K movies in the dataset. The dataset was introduced in the paper "S. Dooms, T. De Pessemier and L. Martens. MovieTweetings: a Movie Rating Dataset Collected From Twitter. Workshop on Crowdsourcing and Human Computation for Recommender Systems, CrowdRec at RecSys 2013."

## 3. Add a Script

There are Python and R **Language Modules** in the module palette to the left of the experiment canvas. Add any **Script** item to the canvas:

<p class="centered-img"><img src="/assets/add-script.png"></p>

Now, how to make Azure execute the given Python script:

```python
# The script MUST contain a function named azureml_main
# which is the entry point for this module.
#
# The entry point function can contain up to two input arguments:
#   Param<dataframe1>: a pandas.DataFrame
#   Param<dataframe2>: a pandas.DataFrame
def azureml_main(dataframe1 = None, dataframe2 = None):

    # Execution logic goes here
    print('Input pandas.DataFrame #1:\r\n\r\n{0}'.format(dataframe1))

    # If a zip file is connected to the third input port is connected,
    # it is unzipped under ".\Script Bundle". This directory is added
    # to sys.path. Therefore, if your zip file contains a Python file
    # mymodule.py you can import it using:
    # import mymodule
    
    # Return value must be of a sequence of pandas.DataFrame
    return dataframe1,
```

or an R script:

```r
# Map 1-based optional input ports to variables
dataset1 <- maml.mapInputPort(1) # class: data.frame
dataset2 <- maml.mapInputPort(2) # class: data.frame

# Contents of optional Zip port are in ./src/
# source("src/yourfile.R");
# load("src/yourData.rdata");

# Sample operation
data.set = rbind(dataset1, dataset2);

# You'll see this output in the R Device port.
# It'll have your stdout, stderr and PNG graphics device(s).
plot(data.set);

# Select data.frame to be sent to the output Dataset port
maml.mapOutputPort("data.set");
```

## 4. Create a Notebook

Nevermind, just create an IPython or an R Notebook using this awesome feature:

<p class="centered-img"><img src="/assets/create-notebook.png"></p>

## 5. Enjoy

<p class="centered-img"><img src="/assets/its-alive.jpg"></p>
