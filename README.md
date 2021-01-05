# DSICapstone

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












