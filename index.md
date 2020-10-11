<h1> Predicting Hazardous Seismic: Evaluating Machine Learning Models using Scikit Learn.</h1>
<em>A newbie evaluation on trying out Machine Learning Models for Classification and Data Augmentation to Support better results.</em>

## Contents:
1. [Premise](#pre)<br/>
2. [Our Contribution](#our)<br/>
3. [In Conclusion](#con)<br/>
4. [What we have Learn](#learnt)<br/>
5. [Refrences](#ref)<br/>
6. [Contributors](#contributor)<br/>

<br/>
<p>We are immensely grateful to  <a href="https://www.linkedin.com/in/nabanita-roy/">Nabanita Roy</a> for pointing out this very interesting dataset,her previous work formed the base for which we were able to build on, you can have a look at her work here (<a href="https://towardsdatascience.com/predicting-hazardous-seismic-bumps-using-supervised-classification-algorithms-part-i-2c5d21f379bc">Part I</a> and <a href="https://towardsdatascience.com/predicting-hazardous-seismic-bumps-part-ii-training-supervised-classifier-models-and-8b9104b611b0">Part II</a>)!<br/>
 
Based on the data exploration and performance analysis carried out by Nabanita, the performance of the previous models were very low for the <b>recall metric</b> having just a 0.06 score for the best performing model <b>SVM</b>. This behaviour resulted in the conclusion that out of all the Actual Positive (hazardous) shifts, only 6% of the shifts have been predicted as Positive. Our focus was on improving this.</p><br/>

<a name="pre"><h3>__1. Premise__</h3></a>
Predicting Positive here is predicting <em>“ the possibility of hazardous situation occurrence, where an appropriate supervision service can reduce a risk of rockburst (e.g. by distressing shooting) or withdraw workers from the threatened area. Good prediction of increased seismic activity is therefore a matter of great practical importance. “</em><br/>

<b>We wouldn’t want to send miners into a mine with a substandard model!</b>

On the other hand, Precision for the best performing model is only 0.67, which means that out of all the shifts predicted as hazardous, (1 - 0.67) = 23% were actually low risk, which would mean a non insignificant number of shifts where miners may have been told to stay home, and thus a lower productivity.  

Our shared colab notebook can be found <a href="https://colab.research.google.com/drive/1fIvMom1iQUPN7K_ODtnq9Kb41ZfKH_xK#scrollTo=_25QD437NyrA"><em>here!</em></a><br/>

<a name="our"><h3>__2. Our Contribution__</h3></a>
<ul>
 <li><b>Pre-processing the Data Further</b></li>
 <p>As a small improvement, we replaced the One-hot encoder for these Categorical variables with Numerical encoding as the assessment coding being graded from Low to High, coding numerically added meaningful information. To view the full data attributes, see <a href="https://archive.ics.uci.edu/ml/datasets/seismic-bumps">here.</a></p>
 <ul>
  <li><b>Seismic</b>: result of shift seismic hazard assessment in the mine working obtained by the seismic
   method (<b>a - lack of hazard, b - low hazard, c - high hazard, d - danger state</b>);</li>
  <li><b>Seismoacoustic</b>: result of shift seismic hazard assessment in the mine working obtained by the
seismoacoustic method;</li>
  <li><b>Shift</b>: information about type of a shift (W - coal-getting, N -preparation shift);</li>
 </ul>
 <p><ins>The encoding of these attributes was implemented by a simple mapping of the known values as seen in line <b>'put line number showing numerical encoding'</b> of our <a href="https://colab.research.google.com/drive/1fIvMom1iQUPN7K_ODtnq9Kb41ZfKH_xK#scrollTo=_25QD437NyrA"><em>colab notebook</em></a>, this encoding allowed for easier interpretability as we will see later. It was also relevant for the plotting of the correlation matrix as unless attributes are numeric, they are completely ignored.<ins/></p>
 <br/>
 <li><b>Explanatory Data Analysis: Checking the Correlations between Features and the Target</b></li>
 <p> To depict the correlation of final features to the Target (Class), a  heatmap was implemented <em>(shown in Figure 1)</em>:
 <br/>
 <p align="center">
 <img src="https://user-images.githubusercontent.com/69084008/95680839-409dfc80-0bd4-11eb-9dd7-3cf5567a2786.png" alt="image"/>
 <br/>
    <em>Figure 1: Correlation Matrix</em>
 </p>
 <br/>
 <li><b>Augment data using Synthetic Minority Oversampling Technique (SMOTE).</b></li>
 <p>The original data has a lot more Class 0 than Class 1 points which is obvious in the data visualisations and is likely to impact the performance of all models. As suggested by  <a href="https://www.linkedin.com/in/nabanita-roy/">Nabanita Roy</a> , we tried the Synthetic Minority Oversampling Technique (SMOTE) oversampling technique as seen in line <b>'put line number showing numerical encoding'</b> of our <a href="https://colab.research.google.com/drive/1fIvMom1iQUPN7K_ODtnq9Kb41ZfKH_xK#scrollTo=_25QD437NyrA"><em>colab notebook</em></a>.</p>
 <br/>
 <p align="center">
 <img src="https://user-images.githubusercontent.com/69084008/95685532-5caf9700-0bf0-11eb-94d1-933a09980287.png" alt="image"/>
 <br/>
    <em>Figure 2: Original dataset shape Counter({0: 2414, 1: 170})</em>
 </p>
 <br/>
 <p align="center">
 <img src="https://user-images.githubusercontent.com/69084008/95685598-b0ba7b80-0bf0-11eb-857a-7d1858150f8b.png" alt="image"/>
 <br/>
    <em>Figure 3: Resampled dataset shape Counter({0: 1931, 1: 1931})</em>
 </p>
</ul>


<a name="con"><h3>__3. In Conclusion__</h3></a>
<ol>
 <li>Training any model on the augmented dataset (SMOTE) improves the model performance significantly.</li>
 <li>XGBoost wins by a small margin, based on shallow Decision Trees.</li>
 <li>The RandomForestClassifier and Decision Tree Classifier are perform well, although not with the GridSearchCV Optimised version! It seems like optimising against the SMOTE dataset can be counter-productive and choosing values like max_leaf_nodes=10 intuitively adapted to a small dataset works here.</li>
</ol>

<a name="learnt"><h3>__4. What we have Learnt__</h3></a>

<a name="ref"><h3>__5. Refernces__</h3></a>
<ol>
 <li>Introduction to Scikit Learn:<a href="https://scikit-learn.org/stable/supervised_learning.html#supervised-learning">Understanding Classification Models for Supervised Machine Learning</a></li>
 <li><a href="https://medium.com/@MohammedS/performance-metrics-for-classification-problems-in-machine-learning-part-i-b085d432082b">To Understand Model Performance Metrics</a></li>
 <li>To Understand the feature data (data types, missing values, outliers, etc): see-<a href="https://towardsdatascience.com/predicting-hazardous-seismic-bumps-using-supervised-classification-algorithms-part-i-2c5d21f379bc">Data Exploration and Peparation</a></li>
 <li>Visualization (boxplots, scatter plots, correlation matrix, etc)- see<a href="https://towardsdatascience.com/predicting-hazardous-seismic-bumps-using-supervised-classification-algorithms-part-i-2c5d21f379bc"> Data Exploration and Peparation</a></li>
</ol>


<a name="contributor"><h3>__6. Contributors__</h3></a>
<ul>
  <li><a href="https://www.linkedin.com/in/catherine-lalanne-85b5ba/">Catherine Lalanne</a></li>
  <li><a href="https://www.linkedin.com/in/heejin-yoon-429837190/">Heejin Yoon</a></li>
  <li><a href="https://www.linkedin.com/in/i-am-luciana-azubuike/">Luciana Azubuike</a></li>
</ul>
<br/>

