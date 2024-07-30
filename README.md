# ARTIST TOUR GROSS EARNING ANALYSIS

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Data Sourcing](#data-sourcing)
- [Project Code](#project-code)
- [Analysis](#analysis)

## INTRODUCTION
This project analyzes the gross earnings of various artists from their tours. It includes data on the actual and adjusted gross earnings, number of shows, average gross per show, and more.

## INSTALLATION
### Install Anaconda
Anaconda is a popular distribution that includes Python, Jupyter Notebook, and many other useful packages for data science. It simplifies the installation process. You can download Anaconda from the Anaconda website.[Click here](https://docs.anaconda.com/anaconda/install/windows/)for windows,[click here](https://docs.anaconda.com/anaconda/install/mac-os/) for masOS.

### Steps for Installing Anaconda:
- Download the installer for your operating system (Windows, macOS, or Linux).
- Run the installer and follow the prompts.
- After installation, you can launch Jupyter Notebook from the Anaconda Navigator or by opening a command prompt/terminal and typing:
jupyter notebook

## USAGE
To use this project, follow these steps:
- Ensure your virtual environment is activated.
- Open a Jupyter Notebook:jupyter notebook.
- Create a new notebook or open an existing one.
- Load the data and perform analysis using the example code provided below.

### DATA SOURCING
The dataset used in this project includes information about various artists and their tours, including gross earnings, number of shows, and average gross per show. The data source is from kaggle. [Click here](https://www.kaggle.com/datasets/amruthayenikonda/dirty-dataset-to-practice-data-cleaning)

## PROJECT CODE
Here is an example of how to load and analyze the data using python
- Install your libaries
```
  !pip install seaborn --upgrade
!pip install pandas --upgrade
!pip install matplotlip --upgrade
``` 
- Import your libaries
```
  import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import re
```
- Load the csv file after uploading.
```
  pd.read_csv("my_file (1).csv")
```
 - Assign to a callable variable
```
    Clean_data=pd.read_csv("my_file (1).csv")
```
 - Display the first row of the dataframe
```
    print(Clean_data.head())
```
 - Display the data types
```
   print(Clean_data.dtypes)
```
 - Remove special characters from dataframe
#### Function to remove special characters
```
def remove_special_characters(text):
    if isinstance(text, str):
        return re.sub(r'[^A-Za-z0-9 ]+', '', text)
    else:
        return text

#### Apply the function to specific columns
Clean_data['Peak'] = Clean_data['Peak'].apply(remove_special_characters)
Clean_data['All Time Peak'] = Clean_data['All Time Peak'].apply(remove_special_characters)
Clean_data['Tour title'] = Clean_data['Tour title'].apply(remove_special_characters)
Clean_data['Ref.'] = Clean_data['Ref.'].apply(remove_special_characters)


print (Clean_data)
```

- Replace the row number 7 with 8 at the Rank column
```
  Clean_data.loc[7,"Rank"]=8
```
  
 - Remove some characters in the column Average gross
```
   Clean_data['Average gross'] = Clean_data['Average gross'].str.replace('$', '', regex=False)
Clean_data['Average gross'] = Clean_data['Average gross'].str.replace(',', '', regex=False).astype(int)
```

- Fill NaN with 0
```
  Clean_data.fillna(000)
```
  
## ANALYSIS
   ### Graph plotting Code
   #### Average Gross by Artist
```   
   plt.figure(figsize=(15,6))
font1={"family":"serif","color":"purple","size":15}
sns.barplot(x="Artist",y="Average gross",data=Clean_data).set_title("AVERAGE GROSS BY ARTIST",
                                                       fontdict=font1,loc="center")
        
plt.xlabel("Artist")
plt.ylabel("Average gross")
plt.grid()
plt.show()
```
  #### Artist with the Highest Show
```
  plt.figure(figsize=(15,6))
font1={"family":"serif","color":"orange","size":15}
sns.barplot(x="Artist",y="Shows",data=Clean_data).set_title("ARTIST WITH THE HIGHEST SHOWS",
                                                       fontdict=font1,loc="center")
        
plt.xlabel("Artist")
plt.ylabel("Shows")
plt.grid()
plt.show()
```

#### Bar Chart for Artist by Rank
```
plt.figure(figsize=(15,6))
font1={"family":"serif","color":"orange","size":15}
sns.barplot(x="Artist",y="Shows",data=Clean_data).set_title("ARTIST WITH THE HIGHEST SHOWS",
                                                       fontdict=font1,loc="center")
        
plt.xlabel("Artist")
plt.ylabel("Shows")
plt.grid()
plt.show()
```

#### Pie Chart for Artist by Shows
```
plt.figure(figsize=(15,6))
font1={"family":"serif","color":"orange","size":15}
sns.barplot(x="Artist",y="Shows",data=Clean_data).set_title("ARTIST WITH THE HIGHEST SHOWS",
                                                       fontdict=font1,loc="center")
        
plt.xlabel("Artist")
plt.ylabel("Shows")
plt.grid()
plt.show()
```

