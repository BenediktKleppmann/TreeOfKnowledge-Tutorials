
##########################################################################################
#                                                                                        #
#                           Tree of Knowledge  - Tutorial 1                              #
#              Birth Probability using National Longitudinal Survey of Youth             #
#                                                                                        #
##########################################################################################

In this tutorial the software Tree of Knowledge is used to model when American women give birth to children.
Specifically, for every woman and timestep a birth probability is determined that depends on her current number of children, age and marital status.
The parameters/weights associated with this birth probability are learned from data from the National Longitudinal Survey of Youth 1979.

The tutorial goes through the following steps:
	1. download and prepare the data 
	2. upload the data to www.treeofknowledge.ai
	3. prepare the model 
	4. interpret results
	
	
	
-------------------------------------------------------------
	1 Intro
------------------------------------------------------------- 


About the Data:
In this tutorial we will be working with data from the National Longitudinal Survey of Youth 1979. This dataset tracks the lives of 12 686 Americans. 

/*	The study begun in 1979. 12 686 young Americans were selected to take part in the study, and seperated into three groups. 
	The first group (6 111 youths) was designed to be a cross-section of youths in America. The second group (5 295 youths) only contains people from minorities such as Hispanic-Americans, Black-Americans and economically disadvantaged Americans. 
	The third group only contains youths that were serving in the military in 1978.
*/
Beginning in 1979, the 12 686 participants completed a survey with many questions about their current situation (e.g. family situation, profession, etc.). They repeated the same survey every 1-2 years until 2016. This survey data therefore allows us to track the development throughout their lives.
For more information on the data, please refer to https://www.nlsinfo.org/content/cohorts/nlsy79.

The Task:
One of the questions in the survey was the number of biological children. By tracking the number of biological children for the women in this study, we can approximately determine when they gave birth to a child.
With Tree of Knowledge we will be able to simulate these women and learn the probability of them giving birth depending on criteria such as their age, current number of children and marital status.

	
-------------------------------------------------------------
	2 Upload the Data
------------------------------------------------------------- 

2.1 Log in

	* in your browser, open the website www.treeofknowledge.ai
	* click on "Sign up" (in the top right corner), enter your details and press "Submit". You will be redirected to the main menu.
	* on the main menu, click the box that says "Upload Data"


2.2 Upload the Data

The Data uploading consists of 6 steps. During these steps various details about the origin and the form of the data are specified. 
These specifications are needed for the data to be integrated with previously uploaded data in Tree of Knowledge's central knowledge base. Once in the knowledge base the data can be easily used for a large range of different tasks.
It is essential to be diligent when doing the uploading, so that the data will be integrated correctly.

2.2.1 Select csv-file: 
	Click on "Choose File"
	navigate to the file "1 - Birth Probability using National Longitudinal Survey of Youth/national_longitudinal_survey_of_youth_1979.csv" and open it
	press "Upload"
	
2.2.2 Data source:
	What institution generated the data? According to <the website (https://www.nlsinfo.org/content/cohorts/nlsy79)>, the National Longitudinal Survey is financed by the "US Bureau of Labor Statistics", so let's write that into the first field.
	We leave the second field empty, because the table contains observations from many different points in time.
	For 'Correctness of the data' we can guess a value. I personally believe that the US Bureau of Labor Statistics is an impartial institution, however doubt the data was checked very rigorously. Therefore I give it four stars.
	
	3 Object type
	Here we specify what type of objects are described by the data. The entities described by the data - here: the 12 686 Americans - generally belong to the same type of object - here: American. 
	We search for "American" or find it below in the tree and select it. 
	Next, we click "Choose".
	
	4 Meta data
	In this section we specify details of the sample. Were it a random sample from among all Americans? 
	It is effectively a random sample from those Americans that were youth in 1979. We specify this sampling constraint by adding the two new facts "Age > 13" and "Age < 23" with valid times from 1979-01-01 to 1980-01-01 - see the figure below.
	Next, we click on "Next".
	
	5 Object Attributs
	Here we specify the columns what column is described by 
	Above every column is a "Choose Attribute" button which opens an attribute-selection window.
	By choosing the 
	column 1  -> "Respondent ID of the National Longitudinal Survey 1979"
	column 3  -> "Age" 
	column 4  -> "Sex" 
	column 5  -> "Marital Status" 
	column 6  -> "Educational Attainment" 
	column 7  -> "Employment Status" 
	column 8  -> "Hours Worked per Week" 
	column 9  -> "Weeks Worked in the last year" 
	column 10 -> "Number of biological children" 
	
	Note: For some of the columns a little notice appears: "xxx format missmatches". This is the number of values in this column, that do not uphold the format specified by the selected column. 
	For instance the 9th column "Weeks Worked in the last year" has to be an integer between 0 and 52. Therefore the cells containing the value -4 are marked red and counted as format missmatch.
	
	Column 2 contains the year in which that row's data was measured. There are multiple rows containing data about the same person (identified by the Respondent ID in the first column), each row containing data from a different year. 
	We explain this to the website by choosing the attribute "Date/Time of Observation" for column 2 and changing the field "In the table, are there mutltiple rows with information on the same entity?" to 'Yes'. 
	Now a new row of buttons appeared above the table. We click the "Object Id" button above column 1 to label it as the objects identifier.
	
	One thing remains: the "Date/Time of Observation" is supposed to not only contain the year of observation, but an exact date. To transform the second column into dates, we click on "Edit Column" button below it. 
	In the window that opens we write the transformation "str(value) + '-01-01-01 00:00:00'" into the textarea. Then click on "Apply Transformation" and then on "Use transformed column".
	
	
	6 Match to existing entities
	This step would be relevant if Tree of Knowledge's knowledge base already contained data from the exact same people. The page allows us match the people from our dataset to the people already present in the knowledge base.
	In our case we are however quite sure that no data about the survey participants is already in the knowledge base, also we don't know enough about them (e.g. name, social security number, etc.) to be able to reliably match them to people in the knowledge base.
	We therefore skip this step by simply pressing "Upload the data!"
	
	Well done!!
	
-------------------------------------------------------------
	3 Model the system
------------------------------------------------------------- 
	
	
	
		