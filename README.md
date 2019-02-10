# Personalized-cancer-diagnosis
__Classify the given genetic variations/mutations based on evidence from text-based clinical literature.__


<h1> Business Problem</h1>
<h2>Description</h2>

<p> Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/ </p>
<p> Data: Memorial Sloan Kettering Cancer Center (MSKCC)</p>
<p> Download training_variants.zip and training_text.zip from Kaggle.</p> 

<h6> Context:</h6>
<p> Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/discussion/35336#198462</p>

<h6> Problem statement : </h6>
<p> Classify the given genetic variations/mutations based on evidence from text-based clinical literature. </p>


<h2> Source/Useful Links</h2>

Some articles and reference blogs about the problem statement
1. https://www.forbes.com/sites/matthewherper/2017/06/03/a-new-cancer-drug-helped-almost-everyone-who-took-it-almost-heres-what-it-teaches-us/#2a44ee2f6b25
2. https://www.youtube.com/watch?v=UwbuW7oK8rk 
3. https://www.youtube.com/watch?v=qxXRKVompI8

<h2>  Real-world/Business objectives and constraints.</h2>
* No low-latency requirement.
* Interpretability is important.
* Errors can be very costly.
* Probability of a data-point belonging to each class is needed.

<h3> Data Overview</h3>

- Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment/data
- We have two data files: one conatins the information about the genetic mutations and the other contains the clinical evidence (text) that  human experts/pathologists use to classify the genetic mutations. 
- Both these data files are have a common column called ID
- <p> 
    Data file's information:
    <ul> 
        <li>
        training_variants (ID , Gene, Variations, Class)
        </li>
        <li>
        training_text (ID, Text)
        </li>
    </ul>
</p>

<h3> Example Data Point</h3>

<h6>training_variants</h6>
<hr>
ID,Gene,Variation,Class<br>
0,FAM58A,Truncating Mutations,1 <br>
1,CBL,W802*,2 <br>
2,CBL,Q249E,2 <br>
...

<h6> training_text</h6>
<hr>
ID,Text <br>
0||Cyclin-dependent kinases (CDKs) regulate a variety of fundamental cellular processes. CDK10 stands out as one of the last orphan CDKs for which no activating cyclin has been identified and no kinase activity revealed. Previous work has shown that CDK10 silencing increases ETS2 (v-ets erythroblastosis virus E26 oncogene homolog 2)-driven activation of the MAPK pathway, which confers tamoxifen resistance to breast cancer cells. The precise mechanisms by which CDK10 modulates ETS2 activity, and more generally the functions of CDK10, remain elusive. Here we demonstrate that CDK10 is a cyclin-dependent kinase by identifying cyclin M as an activating cyclin. Cyclin M, an orphan cyclin, is the product of FAM58A, whose mutations cause STAR syndrome, a human developmental anomaly whose features include toe syndactyly, telecanthus, and anogenital and renal malformations. We show that STAR syndrome-associated cyclin M mutants are unable to interact with CDK10. Cyclin M silencing phenocopies CDK10 silencing in increasing c-Raf and in conferring tamoxifen resistance to breast cancer cells. CDK10/cyclin M phosphorylates ETS2 in vitro, and in cells it positively controls ETS2 degradation by the proteasome. ETS2 protein levels are increased in cells derived from a STAR patient, and this increase is attributable to decreased cyclin M levels. Altogether, our results reveal an additional regulatory mechanism for ETS2, which plays key roles in cancer and development. They also shed light on the molecular mechanisms underlying STAR syndrome.Cyclin-dependent kinases (CDKs) play a pivotal role in the control of a number of fundamental cellular processes (1). The human genome contains 21 genes encoding proteins that can be considered as members of the CDK family owing to their sequence similarity with bona fide CDKs, those known to be activated by cyclins (2). Although discovered almost 20 y ago (3, 4), CDK10 remains one of the two CDKs without an identified cyclin partner. This knowledge gap has largely impeded the exploration of its biological functions. CDK10 can act as a positive cell cycle regulator in some cells (5, 6) or as a tumor suppressor in others (7, 8). CDK10 interacts with the ETS2 (v-ets erythroblastosis virus E26 oncogene homolog 2) transcription factor and inhibits its transcriptional activity through an unknown mechanism (9). CDK10 knockdown derepresses ETS2, which increases the expression of the c-Raf protein kinase, activates the MAPK pathway, and induces resistance of MCF7 cells to tamoxifen (6). ... 

__There are nine different classes a genetic mutation can be classified into => Multi class classification problem.__

<h3> Performance Metric</h3>
Source: https://www.kaggle.com/c/msk-redefining-cancer-treatment#evaluation

Metric(s): 
* Multi class log-loss 
* Confusion matrix 


<h1>Summary of single features</h1>
<p>Here is a Comparison of our models.</p>


<table style="width:100%">
  <tr>
      <th></th>
    <th>Vectorization</th>
       <th>Feature</th>
      
  <th>Model</th>
    <th>Logloss</th>
      <th>Missclassified points</th>
      
      
  </tr>
  <tr>
    <td></td>
    <td>--</td>
    <td>--</td>
    <td>Random</td>
    <td>2.59</td>
       <td>--</td>
       
   </tr>
  <tr>
    <td></td>
    <td>BoW</td>
    <td>Gene</td>
    <td>logistic regression</td>
    <td>1.19</td>
       <td>--</td>
       
   </tr>
  <tr>
   <td></td>
    <td>BoW</td>
    <td>Variation</td>
    <td>logistic regression</td>
    <td>1.68</td>
       <td>--</td>
        
   </tr>
  <tr>
       <td></td>
    <td>BoW</td>
    <td>Text</td>
    <td>logistic regression</td>
    <td>1.20</td>
       <td>--</td>
     
   
  </tr>
  
  
  
   <tr>
       <td></td>
    <td>BoW</td>
    <td>text</td>
    <td>logistic regression</td>
    <td>1.20</td>
       <td>--</td>
        
   
  </tr>
   
<table style="width:100%">
<p style="font-size:24px;text-align:Center"> <b>Stacking the three types of features </b><p>



 <tr>
      <th></th>
    <th>Vectorization</th>      
  <th>Features</th>
      <th>Model</th>
    <th>Logloss</th>
      <th>Missclassified points</th>
      
      
 
  <tr>
    <td></td>
    <td>BoW</td>
    <td>All 3</td>
    <td>MultinomialNB</td>
    <td>1.19</td>
       <td>35%</td>
       
   </tr>
  <tr>
   <td></td>
    <td>BoW</td>
    <td>All 3</td>
    <td>KNN</td>
    <td>0.98</td>
       <td>33%</td>
        
   </tr>
  <tr>
       <td></td>
    <td>BoW</td>
    <td>All 3</td>
    <td>Logistic Regression With balanced class weight</td>
    <td>1.15</td>
       <td>31%</td>
     
   
  </tr>
  
  
  
   <tr>
       <td></td>
    <td>BoW</td>
    <td>All 3</td>
    <td>Linear SVM</td>
    <td>1.05</td>
       <td>32%</td>
   
  </tr>
   
   
   <tr>
       <td></td>
    <td>BoW</td>
    <td>All 3</td>
    <td>Random forests</td>
    <td>1.20</td>
       <td>41%</td>
   
  </tr>
   
   
   <tr>
       <td></td>
    <td>Response Coding</td>
    <td>All 3</td>
    <td>Random forests</td>
    <td>1.28</td>
       <td>45%</td>
   
  </tr>
  
  
   
   <tr>
       <td></td>
    <td>BoW</td>
    <td>All 3</td>
    <td>Stacking Classifier</td>
    <td>1.99</td>
       <td>50%%</td>
   
  </tr>
      
   <tr>
       <td></td>
    <td>BoW</td>
    <td>All 3</td>
    <td>Maximum Voting Classifier</td>
    <td>1.38</td>
       <td>35%%</td>
   
  </tr>
   
   
</table> 


# TFIDF

<h1>Summary of single features(TFIDF)</h1>
<p>Here is a Comparison of our models.</p>


<table style="width:100%">
  <tr>
      <th></th>
    <th>__Vectorization__</th>
       <th>Feature</th>
      
  <th>Model</th>
    <th>Logloss</th>
      <th>Missclassified points</th>
      

  <tr>
    <td></td>
    <td>Tfidf</td>
    <td>Gene</td>
    <td>logistic regression</td>
    <td>1.32</td>
       <td>--</td>
       
   </tr>
  <tr>
   <td></td>
    <td>Tfidf</td>
    <td>Variation</td>
    <td>logistic regression</td>
    <td>1.74</td>
       <td>--</td>
        
   </tr>
  <tr>
       <td></td>
    <td>Tfidf</td>
    <td>Text</td>
    <td>logistic regression</td>
    <td>1.12</td>
       <td>--</td>
     
   
  </tr>
  
  
  
   <tr>
       <td></td>
    <td>Tfidf</td>
    <td>text</td>
    <td>logistic regression</td>
    <td>1.20</td>
       <td>--</td>
        
   
  </tr>
   
<table style="width:100%">
<p style="font-size:24px;text-align:Center"> <b>Stacking the three types of features </b><p>



 <tr>
      <th></th>
    <th>Vectorization</th>      
  <th>Features</th>
      <th>Model</th>
    <th>Logloss</th>
      <th>Missclassified points</th>
      
      
 
  <tr>
    <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>MultinomialNB</td>
    <td>1.35</td>
       <td>41%</td>
       
  </tr>
  <tr>
       <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>Logistic Regression Without balanced class weight</td>
    <td>1.34</td>
       <td>37%</td>
     
   
  </tr>
  <tr>
       <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>Logistic Regression With balanced class weight</td>
    <td>1.14</td>
       <td>37%</td>
     
   
  </tr>
  
  
  
   <tr>
       <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>Linear SVM</td>
    <td>1.05</td>
       <td>32%</td>
   
  </tr>
   
   
   <tr>
       <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>Random forests</td>
    <td>1.07</td>
       <td>34%</td>
   
  </tr>
   
   
   <tr>
       <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>Linear SVM</td>
    <td>1.44</td>
       <td>41%</td>
   
  </tr>
  
  
   
   <tr>
       <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>Stacking Classifier</td>
    <td>2.06</td>
       <td>69%</td>
   
  </tr>
      
   <tr>
       <td></td>
    <td>Tfidf</td>
    <td>All 3</td>
    <td>Maximum Voting Classifier</td>
    <td>1.42</td>
       <td>42%</td>
   
  </tr>
   
   
</table> 

