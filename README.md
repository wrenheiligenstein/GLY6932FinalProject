# GLY6932FinalProject
## Project Description
### Scientific Motivation
The objective of this study is to develop an algorithm that will accurately predict whether someone will be happier in STEM or humanities related fields. I found by talking to graduate students in the astronomy department at the University of Florida that nearly everyone was a cat person (I'm a dog person).  It made me start to think about how different personalitiy types might be drawn towards certain degrees. I also began to think about how these different personalities might "fit" better into different fields than what they may have chosen based on their aptitude, and how someone could be happier studying one thing or another based on their personality.  The goal was to create a quiz that can help someone decide which major they will be happier in based not on their skills at the topic nut based on their personality traits.   
### Methods
Most of the functions used for this algorithm were imported from SciKit Learn. First, a google form was created where responders could indicate their field (STEM or Humanities) and indicate how happy they are in their program on a scale from 1 to 10.  These two questions were followed up by a 16-question personality quiz and a spot to optionally leave their name.  I sent the form out to the UF Astronomy graduate student discord server as well as my private instagram and snapchat stories. 64 responses were collected. The link to the google form can be found below.  

https://docs.google.com/forms/d/1bBo0hlouJN3QrFRpEU04ECniBK3M4BEyQcH4wOiNaPE/edit#question=2128487999&field=108525739

I then converted the form into a CSV file to use in Google Collab.  All of the points with happiness ranked 7 or lower were dropped, as the focus is to determine which personality types would be happiest in which field. After performing a PCA on the data, I decided to only use the first 10 principal components out of 16 as they contained 90% of the variance.  After splitting these 10 components into training and test data I fit a logistic regression over the data to predict if these happy people were in STEM or humanities degrees.  There were a lot fewer points for humanities, so balanced class weights were used to help mitigate this problem.  This process was repeated 200 times with random splits to see the average values for accuracy and the f1 score.  The last interation was kept for the quiz.  

The quiz manifested as a user friendly function with instructions for the user to input their answers to the quiz, which would then be sent through the algorithm to predict which field they would be happier in.  
## Accessing the Data
The csv file used to make the algorithm can be found under "STEMvsHumanities.csv" in this repository.
## Running the Code
To run this code, one can select the "open in Colab" option at the top of GeologyFinalProject.ipynb in this repository. This will open the file in Google Colab and the user can run the code as is.  The file can also be downloaded and uploaded to a different python interface such as Jupyter Notebook.  In this case, it may be necessary to download the STEMvsHumanities file as well and uncomment the line to open the file from the same directory as the notebook.  The user may need to change the path.  

Aside from this, there are no other dependencies other than what is imported in the first cell, and nothing else needs to be installed. Another important note is that when the user inputs their answers to the quiz, they need to hit "enter" or "return" each time.     
## Figures
<img width="609" alt="Screenshot 2025-04-16 at 15 36 54" src="https://github.com/user-attachments/assets/bf0b35bc-31f9-4813-89ad-bdeed4d62209" />

_Figure 1._ 

Figures 1 and 2 give details about google form responses.  Figure 1 shows that there were 64 responses in total,  with 84.4% being STEM majors and 15.6% being humanities majors.  Due to this uneven number, balanced class weights were used for the logistic regression model. 
Figure 2 shows a histogram for the different rating people gave their overall happiness in their program.  Due to the high number of data points with happiness ranked 8 or higher, this was the cutoff decided on for points to be used for the algorithm.  

<img width="621" alt="Screenshot 2025-04-16 at 15 43 50" src="https://github.com/user-attachments/assets/3cdcb6d8-a24f-4c13-9812-b73ca95f1b4a" />

_Figure 2._

<img width="417" alt="Screenshot 2025-04-16 at 15 44 05" src="https://github.com/user-attachments/assets/7edcde51-bf00-49ce-a271-cf1e618d725c" />

_Figure 3._

Figures 3 and 4 show measurements of how well the algorithm performed on the testing data.  The program was ran 200 times with different splits of training and test data, and histograms were created of the accuracy and f1 scores for each split.  The average value was also taken for these metrics to get a general idea of how well the algorithm typically performs. Having more data points would likely reduce the width of these distributions, as the split would have less of an effect. The accuracy is measured by taking the number of correct predictions over the number of total predicitons.  The f1 score is calculated using both the harmonic mean of precision and recall.  Generally, the algorithm does well based on these 2 metrics, but the imbalance between the classes may still be having an effect.  More data is needed to determined how strong of a link their is between personality and happiness in a particular field.  

<img width="429" alt="Screenshot 2025-04-16 at 15 44 19" src="https://github.com/user-attachments/assets/30acf61f-9a3b-4709-8834-b46d011865b4" />

_Figure 4._
