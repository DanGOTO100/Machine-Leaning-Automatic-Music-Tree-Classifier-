# Machine-Leaning-Automatic-Music-Tree-Classifier-
Machine Learning Decision Tree Classifier used to compose music automaticaly in Python 3.6


This code will generate a music score based on a input score on midi format. Uses **Machine Learning Decision Tree Model in sklearn and a few tweaks for the notes** with  Pandas in order to build the score. 
Also uses Music21 MIT library (http://web.mit.edu/music21/) to manipulate input score and create outout score. 
It was designed with the "For the love of God" score by Steve Vai - probably the best guitar virtuoso in the music business.
The code also tries to understand the duration between notes, avoiding extreme repetition of those that would lead in a very repetitive song, with no creativity. 

It basically uses the following function:


**ExtractScore** : This function will convert an input midi file to a Music21 object and then to a Pandas DataFrame with the columns format like: *'Origin Pitch','Origin Octave','Origin Duration','Next Pitch', 'Next Octave', 'Next Duration'*, that will allows us to later manipulate the score efficiently. Note that if the input midi file, you might need to explore the Music21 part, to obtain the istrument you want to analyze. In the tab under study it was partStream[5]. See code comments for further info. 

After this function, the main program will build a DecisionTree classifier with the Pandas Dataframe output from ExtractScore.
We will need to use **LabelEnconder** as many of the columns are strings and models only accept numeric inputs-output.

The score to be built up is initialzied with random note from the dataframe and then the whole song is build using the prediction model into a Music21 score that will play out at the end as a midi format.


Please note, to avid excesive repertion on notes, the model is tweaked with a conditional statement that will detect many notes 
repeated and modified to keep adding diversity to the score.

