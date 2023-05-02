Download Link: https://assignmentchef.com/product/solved-comp472-assignment-3-covid-19-fact-checking
<br>
<h1>Covid-19 Fact Checking</h1>

In this project, you will build a Naive Bayes bag-of-Word (NB-BOW) approach to determine if a tweet contains a verifiable factual claim. Then, you will compare the output of the NB model to a Word2Vec LSTM approach given to you (see Section 3).

<h1>1           The Dataset</h1>

Download the Assignment 3 dataset available on Moodle. This dataset, created by [Alam et al., 2020], contains a collection of tweets related to Covid-19 collected from March 9–10, 2020 and March 20–25, 2020. These tweets have been labeled for 7 different questions, such as:

Q1       Does the tweet contain a verifiable factual claim?

Q2       To what extent does the tweet appear to contain false information?

…

Q6       Is the tweet harmful for society and why?

For example, an instance of the dataset contains:

<table width="725">

 <tbody>

  <tr>

   <td width="131">tweet id</td>

   <td width="131">text</td>

   <td width="55">q1 label</td>

   <td width="55">q2 label</td>

   <td width="55">q3 label</td>

   <td width="55">q4 label</td>

   <td width="55">q5 label</td>

   <td width="91">q6 label</td>

   <td width="96">q7 label</td>

  </tr>

  <tr>

   <td width="131">1240716889162018816</td>

   <td width="131">Can y’all please just follow the government’s instructions so we can knock this COVID-19 out and be done?! I feel like a kindergartner that keeps losing more recess time because one or two kids can’t follow directions.</td>

   <td width="55">no</td>

   <td width="55">NA</td>

   <td width="55">NA</td>

   <td width="55">NA</td>

   <td width="55">NA</td>

   <td width="91">no not harmful</td>

   <td width="96">no not interesting</td>

  </tr>

 </tbody>

</table>

In this assignment, we will only use the classification of the 1st question (q1 label) whose labels are binary (yes/no):

<ol>

 <li>yes – the tweet contains a verifiable factual claim</li>

 <li>no – the tweet does not contain a verifiable factual claim</li>

</ol>

The dataset is already split into a training set of 400 instances and a test set of 55 instances.

<h1>2           The Naive Bayes Classifier (NB-BOW)</h1>

You will code a Multinomial Naive Bayes classifier yourself.

<h2>2.1         Parameters</h2>

Your Naive Bayes Classifier should use the following parameters:

<strong>Vocabulary: </strong>First fold the training set in lower case, then build a list of all words appearing in the training set. This list will constitute your vocabulary V which will be used as features. To identify the words, tokenise the tweets based on spaces only, use the words as features, and word frequencies as feature values.

Experiment with 2 versions of the model:

<strong>Original Vocabulary </strong>: one model where all words appearing in the training set are used as features. Let’s call this model NB-BOW-OV.

<strong>Filtered Vocabulary </strong>: a second model where you filter out the words that appear only once in the training set, so V contains only the words that appear at least 2 times in the training set. Let’s call this model NB-BOW-FV.

<strong>Smoothing: </strong>to smooth, use additive smoothing (add-<em>δ</em>) with <em>δ </em>= 0<em>.</em>01.

<strong>Log: </strong>To avoid arithmetic underflow, work in <em>log</em><sub>10 </sub>space.

<h2>2.2         Output</h2>

For both your models (NB-BOW-OV &amp; NB-BOW-FV), your program should create 2 output files: a trace file (see Section 2.2.1) and one overall evaluation file (see Section 2.2.2).

<h3>2.2.1         Trace Files</h3>

Given a test set, your program should create trace files called trace NB-BOW-OV.txt and trace NB-BOW-FV.txt,

The trace file should contain:

<ol>

 <li>the tweet ID as indicated in the test file, followed by 2 spaces</li>

 <li>the most likely class as determined by your model (i.e. the label yes, no), followed by 2 spaces</li>

 <li>the score of the most likely class (in scientific notation), followed by 2 spaces</li>

 <li>the correct class as indicated in the test file, followed by 2 spaces</li>

 <li>the label correct or wrong (depending on the case), followed by a carriage return.</li>

</ol>

For example the file trace NB-BOW-O.txt could contain:

<table width="366">

 <tbody>

  <tr>

   <td width="366">1235714668833828864 yes -1.23E-7 no wrong1235545254347984897 no -3.21E-7 no correct</td>

  </tr>

 </tbody>

</table>

<h3>2.2.2         Overall Evaluation Files</h3>

In addition to the trace file, create text files called eval NB-BOW-OV.txt and eval NB-BOW-FV.txt summarising the performance of the model with the initial test set given on Moodle. The file should indicate the model’s:

<ol>

 <li>accuracy (Acc), carriage return</li>

 <li>per-class precision (yes-P, no-P) separated by 2 spaces, then a carriage return</li>

 <li>per-class recall (yes-R, no-R) separated by 2 spaces, then a carriage return,</li>

 <li>per-class F1-measure (yes-F, no-F) separated by 2 spaces, then a carriage return, For example the file eval NB-BOW-OV.txt could contain:</li>

</ol>

<table width="102">

 <tbody>

  <tr>

   <td width="102">.6666.77770.5555.77770.5555.77770.5555</td>

  </tr>

 </tbody>

</table>

<strong>2.3      Programming Environment</strong>

You must use Python 3.8. In addition, you must use GitHub (make sure your project is private while developing).

<h1>3           The LSTM Classifier (LSTM-W2V)</h1>

Your wonderful TAs have implemented a classifier for the same task using an LSTM and Word2Vec embeddings (LSTM-W2V). This code generates the output files (see Section 4.1) for you, so it can be used to compare the performance of your NB-BOW approach.

<ol>

 <li>Download the embedding #6 from the http://vectors.nlpl.eu/repository. Note that the download is 606MB.</li>

 <li>Download the code available at <a href="https://gitlab.com/Feasinde/lstm-for-covid-disinformation">https://gitlab.com/Feasinde/lstm-for-covid-disinformation</a><a href="https://gitlab.com/Feasinde/lstm-for-covid-disinformation">.</a></li>

 <li>Place both downloads in the same folder.</li>

 <li>Run the code and generate the corresponding output files. Note that the code may take a good 5 to 10 minutes to run.</li>

</ol>

<h1>4           Deliverables</h1>

The submission of the assignment will consist of 3 deliverables:

<ol>

 <li>The code &amp; output files</li>

 <li>The demo (8 min presentation &amp; Q/A)</li>

</ol>

<h2>4.1         The Code &amp; Output files</h2>

Submit all files necessary to run your code in addition to a readme.md which will contain specific and complete instructions on how to run your experiments. You do not need to submit the datasets. If the instructions in your readme file do not work, are incomplete or a file is missing, you will not be given the benefit of the doubt. Generate one output file for each model as indicated in Section 4.1.

<h2>4.2         The Demos</h2>

You will have to demo your assignment for ≈ 12 minutes. Regardless of the demo time, you will demo the program that was uploaded as the official submission. The schedule of the demos will be posted on Moodle. The demos will consist in 2 parts: a presentation ≈ 8 minutes and a Q/A part (≈ 4 minutes). Note that the demos will be recorded.

<h3>4.2.1         The Presentation</h3>

Prepare an 8-minute presentation to analyse and compare the performance of your models. The intended audience of your presentation is your TAs. Hence there is no need to explain the theory behind the models. Your presentation should focus on <strong>your </strong>work and the comparison of the performance of 3 models.

Your presentation should contain at least the following:

An analysis of the initial dataset given on Moodle. If there is anything particular about these datasets that might have an impact on the performance of some models, explain it.  An analysis of the difference between the vocabulary of the NB-BOW-OV and NB-BOW-FV models. What is the size of V in each model? did the reduction in V lead to a significant difference in performance? Explain.

An analysis of the results of all 3 models. In particular, compare and contrast the performance of each model with one another.

In the case of team work, a description of the responsibilities and contributions of each team member.

Please note that your presentation must be analytical. This means that in addition to stating the facts (e.g. the F1 has this value), you should also analyse them i.e. explain why some metric seems more appropriate than another, or why your model did not do as well as expected. Tables, graphs and contingency tables to back up your claims would be very welcome here.

Any material used for the presentation (slides, …) must be uploaded on EAS before the due date.

<h3>4.2.2         Q/A</h3>

After your presentation, your TA will proceed with a ≈ 4 minute question period. Each student will be asked questions on the code/assignment, and he/she will be required to answer the TA satisfactorily. In particular, each member should know what each parameter that you experimented with represent and their effect on the performance. Hence every member of team is expected to attend the demo.

In addition, your TA may give you a new dataset and ask you to train or run your models on this dataset. The output files generated by your program will have to be uploaded on EAS during your demo.

<h1>5           Evaluation Scheme</h1>

Students in teams can be assigned different grades based on their individual contribution to project. Individual grades will be based on:

<ol>

 <li>a peer-evaluation done after the submission.</li>

 <li>the contribution of each student as indicated on GitHub.</li>

 <li>the Q/A of each student during the demo.</li>

</ol>

<table width="613">

 <tbody>

  <tr>

   <td width="195">Code</td>

   <td width="400">functionality, proper use of the datasets, design, programming style, …</td>

   <td width="19">11</td>

  </tr>

  <tr>

   <td width="195">Output with initial datasets</td>

   <td width="400">correctness and format</td>

   <td width="19">1.5</td>

  </tr>

  <tr>

   <td width="195">Demo – Presentation</td>

   <td width="400">depth of the analysis, clarity and conciseness, presentation, time-management, …</td>

   <td width="19">4</td>

  </tr>

  <tr>

   <td width="195">Demo – QA</td>

   <td width="400">correct and clear answers to questions, knowledge of the program, …</td>

   <td width="19">2</td>

  </tr>

  <tr>

   <td width="195">Output with demo-dataset</td>

   <td width="400">correctness and format</td>

   <td width="19">1.5</td>

  </tr>

  <tr>

   <td width="195">Total</td>

   <td width="400"> </td>

   <td width="19">20</td>

  </tr>

 </tbody>

</table>

The team grade will be based on: