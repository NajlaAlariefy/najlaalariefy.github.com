---
layout: page
title: Next Word Prediction
description: ShinyR App for Text Prediction using Swiftkey's Data
img: /assets/img/1.jpg
---



### Executive Summary
This app is a text-prediction ShinyApp that will predict the 3 most likely words the user would likely write next. This report will explore and summarize the data properties of the US blogs, twitter and news text datasets, before reporting the n-gram (n-grams are a series of associated tokens) HMM model for predicting the next word based on the previous 1, 2, or 3 words.

Access the app via: [https://najla.shinyapps.io/YourNextWord/ 
](https://najla.shinyapps.io/YourNextWord/).

### Data Summary and Profiling 

Confining the context is important for shaping text-prediction algorithms. For instance, a person writing a business letter will use different words from a person who is tweeting or blogging. So for the perseverance of the dataset contexts, the prediction algorithms will run seperately on all three of the provided datasets.

| Context | # of lines | # of words | Average words per line  |
|---------|------------|------------|-------------------------|
| Twitter | 2360148  | 30451170  | 12.902229                 |
| News    | 1010242   | 34494539  | 41.778428                |
| Blogs   | 899288  | 37570839  | 34.1448277   



### Data Exploration
As part of understanding word associations & building a proper N-Gram model, a tool has been made to display lists of word following a certain token. The following word cloud shows the most probable 1000 words that might come after the word *The*:  


<div  >
<img style="width:100%;   " src="{{ site.baseurl }}/assets/img/1.jpg" alt="Top 1000 words after 'The' " title="Top 1000 words after 'The' "/>
</div>  




### Preprocessing & Cleaning Decisions
All three datasets need cleaning to varying degrees; Twitter contains teh most amount of noise due to its informal nature. Cleaning the data will enable the text prediction to return sounder results. The following preprocessing decisions have been used:

* Merged words (Haven't, Would've ...etc) have been seperated to refine the results.  
* Profane words have been removed using a dataset of 700 words.
* Punctuation marks and special symbols have been all removed. There is a plethora of smiley emoticons that have interferred between words. 



              

### Sampling Decisions
Due to extremely restricted resources (4GB memory, low processor speed), it is deemed fit to sample a random 2% of each of the populations, with guaranteed reproducible results. Sample sizes (number of lines) are as follows:

Context       | Sample Size
------------- | -------------
Twitter       | 47202
Blogs         | 17985
News          | 20204


Words occuring more than 1000 times in the **Twitter** sample:  
`Most.Frequent.Words`   
`the  you  and  for  not that have  are with your this just will what`  
`9322 6033 4380 3807 3395 2673 2200 2185 1727 1715 1641 1537 1467 1268`. 

<div  >
<img style="width:100%;   " src="{{ site.baseurl }}/assets/img/2.jpg" alt="Twitter Top Terms by Occurence" title="Twitter Top Terms by Occurence"/>
</div>  



Words occuring more than 1000 times in the **News** sample: 

`Most.Frequent.Words`   
`The   In  But    A   It   He    I   As  And That`    
`1183  252  210  168  127  121   92   86   80   77`   

Words occuring more than 1000 times in the **Blogs** sample: 

`Most.Frequent.Words`   
`I  The   It This   So  And   We   In    A   As`  
`811  607  179  170  165  163  150  132  115  111`


