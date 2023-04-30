Download Link: https://assignmentchef.com/product/solved-hw3-diamond-mining-cs249
<br>
<h1>Assignment Overview</h1>

The goal of this assignment is for you to develop models for the diamonds dataset included in the ggplot2 package.

This is a very simple assignment: you are asked to build four models: LDA or QDA, simple Linear Regression, log-scaled Linear Regression, and Logistic Regression. You then just upload the formulas (R commands) you used to construct these models to CCLE.

<h2>Step 0: build the numeric.diamonds dataset</h2>

This notebook includes commands for buiding a dataset called numeric.diamonds that you are to use for this assignment.

The diamonds dataset has 3 categorical attributes (cut, color, clarity) that are ordered. The numeric.diamonds dataset is a numeric version of the diamonds dataset in which all these categorical attributes are converted to integer codes.

For example, there are 7 colors, with the ordering: J <em>&lt; </em>I <em>&lt; </em>H <em>&lt; </em>G <em>&lt; </em>F <em>&lt; </em>E <em>&lt; </em>D (J is worst, D is best). We implement these by replacing J with the value 1, I with the value 2, …, and D with the value 7. After doing this transformation for cut and clarity also, the result is an entirely numeric dataset called numeric.diamonds.

In addition to this notebook, we’ve provided another called Diamonds.ipynb for gaining intuition about the data by walking through some exploratory graphics. Many aspects of the dataset are displayed. You do not have to use this notebook, it is totally optional, but it is included since visualization can help.

<h2>Step 1: build a training set and test set (as subsets of numeric.diamonds) – using your UID</h2>

First, set the random number generator seed to your UID. Then generate a training set and test set using the following commands:

MY_UID = 123456789 ########## you must enter your UCLA UID here !!! set.seed( MY_UID )

n = nrow( numeric.diamonds ) sample.size = 0.75 * n

training.row.ids = sample( (1:n), sample.size )

my.training.set = numeric.diamonds[ training.row.ids, ]

my.test.set = numeric.diamonds[ -training.row.ids, ]                                         # set complement of training.set.ids

Please use exactly these commands to construct your training set and test set. Also, use the training set to construct each model, and use the test set to compute the accuracy of each model. The grading program will re-compute your model and its accuracy using this method.

<h2>Step 2: Evaluate the accuracy of four Baseline Models about diamonds</h2>

These are the baseline models:

qda( cut ~ .,         data=my.training.set ) lm( price ~ .,             data=my.training.set ) lm( log10(price) ~ ., data=my.training.set )

glm( I(price&gt;1500) ~ ., data=my.training.set, family=binomial )

You are to develop a notebook that computes the accuracy of each of these models on my.test.set.

<h2>Step 4: generate improvements on the Baseline Models</h2>

For the numeric.diamonds dataset you are to develop a notebook that evaluates accuracy of four baseline models in R:

<ol>

 <li>a LDA or QDA classification model that predicts a diamond’s Cut.</li>

 <li>a linear regression model that predicts a diamond’s Price.</li>

 <li>a linear regression model that predicts a diamond’s log10(Price).</li>

 <li>a logistic regression model that predicts whether a diamond’s Price is above $1500.</li>

</ol>

As an example, you might produce these models:

<ol>

 <li>qda( cut ~ price + table + color + clarity, data=my.training.set )</li>

 <li>lm( price ~ carat + x + y + z + clarity, data=my.training.set )</li>

 <li>lm( log10(price) ~ table + log10(carat) + color, data=my.training.set )</li>

 <li>glm( abs(price<em>&gt;</em>1500) ~ carat + table + clarity, data=my.training.set, family = binomial )</li>

</ol>

As these examples show, details matter: you must specify the complete formula for each model in detail, listing all variables included.

Please choose attributes so that your model outperforms the baseline model on my.test.set.

<h2>Step 4: generate a CSV file HW3 output.csv including your 4 models</h2>

If these were your four models, then to complete the assignment you would create a CSV file HW3 output.csv containing eight lines:

33.333, qda( cut ~ .,                                          data=my.training.set )

88.888, lm( price ~ .,                                         data=my.training.set )

77.777, lm( log10(price) ~ ., data=my.training.set )

88.888, glm( I(price&gt;1500) ~ ., data=my.training.set, family=binomial )

44.444, qda( cut ~ price + table + color + clarity, data=my.training.set )

99.999, lm( price ~ carat + x + y + z + clarity, data=my.training.set )

99.999, lm( log10(price) ~ table + log10(carat) + color, data=my.training.set )

99.999, glm( I(price&gt;1500) ~ carat + table + clarity, data=my.training.set, family=binomial )

The first four lines show the four Baseline Models. The next four are your models that improve on the Baseline model.

Each line gives <strong>the accuracy of a model on </strong>my.test.set, as well as <strong>the exact command you used to generate the model</strong>. You must develop procedures for computing accuracy that follow instructions in the notebook.

For each of the baseline models, you will get 18 points for computing accuracy values correctly. You will get 7 points for producing a model with higher accuracy. Thus the maximum possible for this assignment is 100 points.

<h2>Step 5: upload your CSV file and notebook to CCLE</h2>

Finally, go to CCLE and upload:

<ul>

 <li>your output CSV file HW3 output.csv</li>

 <li>your notebook file HW3 Diamond Mining.ipynb</li>

</ul>

We are not planning to run any of the uploaded notebooks. However, your notebook should have the commands you used in developing your models — in order to show your work. As announced, all assignment grading in this course will be automated, and the notebook is needed in order to check results of the grading program.