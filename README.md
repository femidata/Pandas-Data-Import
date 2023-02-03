# Pandas-Data-Import
The repository hosts the files used to explain the filepath attribute in pandas file import to pandas dataframe.

Importing data Into a Pandas DataFrame — How hard can it be?To work with data in Pandas, you need to import a dataset. As easy as importing a dataset into a dataframe may sound, I was stuck in a data import loop for almost two weeks, when I started learning pandas, considering I've always been a self-taught individual all my life (I hope to write about the disadvantages of being self-taught in a future article). 

The official pandas documentation, despite explaining every attributes of the data reading functions, didn’t breakdown the filepath attribute enough to make it easy for learners.
This article will explain the different ways a dataset can be imported into a dataframe concentrating on the filepath attribute.

Firstly, we need to import the pandas library# Import the pandas with the common alias "pd"
import pandas as pd

While there are several data type e.g. excel file, json, html, etc.. that can be imported into a pandas dataframe, this article will concentrate on importing a CSV file. The link below is the link that shows the location of the dataset on my PC local directory.

Dataset location on my PC: 

C:\Users\Femi Odugbesan\Desktop\Malaria\Outter\malaria.csv.

1. Same Folder Import MethodThe easiest way to import a data is to call the dataset file name directly as seen in the code below, provided the notebook and dataset are in the same folder.

df = pd.read_csv('malaria.csv')
df.head()

This method above has confused several learners, because most tutorials fails to explain that the dataset file must be in the same folder for it to work.

2. Inner Folder Import MethodBy inner folder, I mean the data file should be contained in a folder that is inside the location of the jupyter notebook file. For this demonstration, I will create a folder called inner and put a copy of the malaria dataset used in this article.

# Read the folder that is contained in the same directory as the jupyter noteboke file
df = pd.read_csv('inner/malaria.csv')
df.head()

3. Previous Folder Import MethodThe previous folder is the folder outside the folder in which jupyter notebook file is contained. To read a file which is outside of the folder in which the jupyter notebook file is contained, you just have to use two periods ( .. ) to navigate one folder outside the current folder. This is as seen in the code below;

# This method shows how to read a file into a dataframe contained in a previous folder

df = pd.read_csv('../malaria.csv')
df.head()

Full Directory Import MethodBelow is the code showing the method of how to import a dataset using the full data directory;

df = pd.read_csv('C:\Users\Femi Odugbesan\Desktop\Malaria\malaria.csv')
df

The code above was executed with the dataset location full filepath. However, this code will display an error when executed as seen below;

File "<ipython-input-34-8b17d5e6d40c>", line 1
    df = pd.read_csv('C:\Users\Femi Odugbesan\Desktop\Malaria\malaria.csv')
                    ^
SyntaxError: (unicode error) 'unicodeescape' codec can't decode bytes in position 2-3: truncated \UXXXXXXXX escape

Why do you think this error occurred? 

Let’s recall a little from our python lessons, remember “\” in python means escape character (learn more about python escape character sequence here). In the code above, the backslash ( \ ) doesn’t represent the directory separator but an escape character.

To correct this, we need to use a double backslash ( \\ ) to represent a backslash that is required for the code to correctly run. This is as shown below;

df = pd.read_csv('C:\\Users\\Femi Odugbesan\\Desktop\\Malaria\\malaria.csv')
df.head()

The other option is to change the backslash ( \ ) to a forward slash ( / ). This will also work perfectly as seen in the code below;

df = pd.read_csv('C:/Users/Femi Odugbesan/Desktop/Malaria/malaria.csv')
df.head()

While all these methods above works for reading a dataset into a dataframe in python, I will like to round up with a very simple method almost everyone learning pandas are yet to come across. This method I personally  call the “ magic r” method, requires adding “r” before the quote that the data link is contained in. This is as shown in the codes below;

df = pd.read_csv(r'C:\Users\Femi Odugbesan\Desktop\Malaria\malaria.csv')
df.head()

Recall that a single “\” acted as an escape character. However, adding the “r” did the magic and the code now works perfectly. 

Note: Magic r will work for all the data reading methods described in this article

SummaryThere are several resources that teaches pandas but most of them unfortunately don’t take time to explain the filepath attribute extensively, thereby causing a delay in learning and sometimes even discourages some learner to continue, as they can’t get past data import. I remember personally watching several videos and reading articles online just to understand how to read data into pandas and most of them just didn’t explain what i later had to find out myself. 

How many learners could have imagined something as simple as the backslash ( \ ) could have such impact on reading data into a pandas dataframe.

This article concentrated on the read_csv( ) method. However, this concept will work for other data types too.
