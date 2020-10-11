<h1> Predicting Hazardous Seismic: Evaluating Machine Learning Models using Scikit Learn.</h1>
<em>A newbie evaluation on trying out Machine Learning Models for Classification and Data Augmentation to Support better results.</em>

## Contents:
1. [Premise](#pre)<br/>
1. [Our Contirbution](#our)<br/>
3. [Contributors](#contributor)<br/>

<br/>
<p>We are immensely grateful to  <a href="https://www.linkedin.com/in/nabanita-roy/">Nabanita Roy</a> for pointing out this very interesting dataset,her previous work formed the base for which we were able to build on, you can have a look at her work here (<a href="https://www.linkedin.com/in/nabanita-roy/">Part 1</a> and <a href="https://www.linkedin.com/in/nabanita-roy/">Part 2</a>)!<br/>
 
Based on the data exploration and performance analysis carried out by Nabanita, the performance of the previous models were very low for the <b>recall metric</b> having just a 0.06 score for the best performing model <b>SVM</b>. This behaviour resulted in the conclusion that out of all the Actual Positive (hazardous) shifts, only 6% of the shifts have been predicted as Positive. Our focus was on improving this.
</p>
<br/>

<a name="pre"><h3>__1. Premise__</h3></a>
Predicting Positive here is predicting <em>“ the possibility of hazardous situation occurrence, where an appropriate supervision service can reduce a risk of rockburst (e.g. by distressing shooting) or withdraw workers from the threatened area. Good prediction of increased seismic activity is therefore a matter of great practical importance. “</em><br/>

<b>We wouldn’t want to send miners into a mine with a substandard model!</b>

On the other hand, Precision for the best performing model is only 0.67, which means that out of all the shifts predicted as hazardous, (1 - 0.67) = 23% were actually low risk, which would mean a non insignificant number of shifts where miners may have been told to stay home, and thus a lower productivity.  

Our shared colab notebook can be found <a href="https://colab.research.google.com/drive/1fIvMom1iQUPN7K_ODtnq9Kb41ZfKH_xK#scrollTo=_25QD437NyrA"><em>here!</em></a><br/>

<a name="our"><h3>__2. Our Contirbution__</h3></a>
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
 <li><b>Checking the Correlations between Features and the target</b></li>
 <br/>
 <p align="center">
 <img src="https://user-images.githubusercontent.com/69084008/95680839-409dfc80-0bd4-11eb-9dd7-3cf5567a2786.png" alt="image"/>
 <br/>
    <em>Figure 1: Correlation Matrix</em>
</p>
<br/>
</ul>

<ins>The encoding of these attributes was implemented by a simple mapping of the known values as seen in line <b>'put line number showing numerical encoding'</b>, this encoding allowed for easier interpretability as we will see later.<ins/>


<p align="center">
 <img src="https://user-images.githubusercontent.com/69084008/94839134-80aff300-040e-11eb-9a83-a1e8cb8099f0.png" alt="image"/>
 <br/>
    <em>Figure Number and Title</em>
</p>
<br/>


<a name="contributor"><h3>__3. Contributors__</h3></a>
<ul>
  <li><a href="https://www.linkedin.com/in/catherine-lalanne-85b5ba/">Catherine Lalanne</a></li>
  <li><a href="https://www.linkedin.com/in/heejin-yoon-429837190/">Heejin Yoon</a></li>
  <li><a href="https://www.linkedin.com/in/i-am-luciana-azubuike/">Luciana Azubuike</a></li>
</ul>
<br/>

