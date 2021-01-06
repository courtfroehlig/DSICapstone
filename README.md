# Data Science Capstone

<b>Introduction and Aims:</b>

Technological skills and competence are essential in entering the 21st century workforce, especially as technologies evolve quickly and become an increasingly integral part of the economy. However, technology provision, access and connectivity do not, in themselves, lead to ICT competence in learning and teaching (international comparative study of pedagogy and ICT use in schools, SITES 2006).  For this reason, the topic of students’ digital self-efficacy and confidence has gained considerable attention in research about students’ learning and  outcomes.

The European Commission’s 2nd Survey of Schools: ICT in Education was conducted in 2018, following the first survey conducted in 2011-2012. It was a survey of head teachers, teachers, students and parents from the EU28, Norway, Iceland and Turkey, and it provided detailed information related to access to, use of, and attitudes towards use of digital technologies in schools.  It collected information about the digital home environment of students and schools’ digital policies, strategies and opinions. Finally, it surveyed teachers and students about their digital activities inside and outside the classroom and their confidence in using various digital technologies, including their perceived ability to perform 20 ICT‐related tasks using a Likert scale ranging from ‘none’ to ‘a lot’.


<b>Goals of this project</b>

- Use student survey questions to predict student confidence in an exploratory way

- Add in teacher student survey questions to see if the model improves

- Perform a cluster analysis to better understand students’ digital confidence (with more fine-grained detail than just low/high confidence)

- Prioritise parsimonious models to examine the most important features


<b>Describing the data</b>

The student survey data consisted of:

- 11.3 % missing values, imputed with mean
- 48835 rows, 181 columns

The variables were all scales (except country code), with some skew on the variables with higher ranges but very few outliers due to small scale ranges. There was high multicollinearity among many of the variables, which I planned to treat with L2 regularization.

The teacher survey data consisted of:
- 6.6% missing data, imputed with mean
- 9927 rows, 151 columns

The variables were also all scales (except thecountry code), with some skew in the variables with higher ranges but very few outliers due to small scale ranges. I decided to treat variables as continuous, except for the country. There was also high multicollinearity among many of the variable.

I iniitally divided the target variable, confidence, into two (relatively) equal groups of ‘low’ and ‘high’ confidence around the median. That is, 54% of participants were in in the low confidence group and 45% of participants were in the high confidence group. These were uneven groups due to the the high proportion of data points that were positioned exactly at the median.

<b> Modelling </b>

I separated train and test sets and used  cross-validation scores to check for robustness. I applied several machine learning classification models with many different parameters and identified the accuracy as well as precision and recall scores to determine success of the models. 

I also conducted a Hierarchical Cluster Analysis to determine whether it would be useful to utilise different target classes (i.e. besides just 'low' and 'high' confidence) based on the 15 confidence variables. That is, I wanted to know if the 15 confidence questions varied systematically in more nuanced ways across participants. I examined groups at n = 5, 3, and 2 clusters. I utilised both z linkage and kmeans clustering. 

After qualitatively studying the differences between the three different cluster analyses, it seemed that using five clusters helped to shed some granular insights into the data (i.e. that there might be more nuanced distinctions between classrooms' digital confidence besides just low/(medium)/high). 

For example: Group 2 had higher variability between lows and highs, with very low confidence with coding & creating websites, and high confidence on using mobile applications/social media. Group 3 was consistently high among variables, with very high scores on coding and creating websites. Group 4 was consistently low overall - low on both coding/programming/creating websites and social media/communication. Therefore, I decided to use these five clusters as my target variable to see if using these clusters as classes helped the predictive model to improve in accuracy and could help shed insights about what factors might predict these distinct classes (especially groups 2, 3, and 4). Accuracy scores were much better than baseline in this phase of modelling (e.g. the Support Vector Machine ha da 55% accuracy score (compared to 37.99% baseline). 

I then decided to more systematically determine the optimal number of clusters, utilising heuristics such as the elbow plots and sillhouette scores. The 'elbow' (i.e. the point after which the SSE drops rapidly, afterwhich decreases in inertia are considerably more marginal than for previous increases in number of clusters) looks to be between 1 and 2 clusters. However, the point at which this elbow actually lied on the plot was somewhat ambiguous. Further, two clusters provided the best silhouette coefficient (.207), compared to .111 for five groups. Based on these evaluation methods, I decided to try modelling (i.e. predicting confidence)  using two clusters (from the hierarchical clustering method), to compare these clusters to the initial modelling using the low/high confidence groups. However, utilising two clusters as the target classes provided similar accuracy scores to the first phase of modelling with low/high confidence groups.

Interestingly, adding in teacher survey data into the predictive model improved the model accuracy score, albeit not by a large margin. It seemed teachers' involvement in advanced courses on internet use, their attitudes about ICT use as positively impacting on student motivation, and their practices around presenting to the entire class were important positive predictors of their students being in the higher confidence class, and their lack of experience negatively predicted being in the high confidence class. In general, this speaks to the importance of schools investing in teachers' professional development in ICT, with a particular focus on supporting them to understand how to teach ICT in a way that can cater to an entire class of diverse learners and in ways that help them understand how their teaching around ICT impacts student motivation. 

<a href="https://github.com/courtfroehlig/DSICapstone/blob/main/CF_Capstone_Data%20cleaning%20and%20exploration.ipynb">Data Cleaning and Exploration</a>

<a href="https://github.com/courtfroehlig/DSICapstone/blob/main/CF_Capstone_Modelling.ipynb">Data Modelling and Findings</a>










