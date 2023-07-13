# NETFLIX-report-with-Python-
Data Analysis of NETFLIX dataset with Python

Import pandas an opening the csv file in the Jupyter notebook
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/206a1ce6-5c5c-481a-8174-688f7fcb2036)

.head() fuction is used to obtain top n values as the output
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/4c902ef2-0b8a-4bba-bf81-71cbeea0f5ed)

 .tail()fuction is used to see the last n values of the dataset/
 .shape function is used to check the shape of the dataset/
 .size funtion is used to check the size of the dataset/
 .columns funtion is used to check the column names of the dataset
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/c33480a0-4470-46e4-829a-a9743d9d8c9a)


.dtype function is used to check the datatype of the dataset/
.info() function prints the information about the dataframe
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/d3adc643-8fa2-438f-9cfe-9cc254bcc273)


Task. 1) Is there any Duplicate Record in this dataset ? If yes, then remove the duplicate records.

.duplicate() function is used to find duplicate values or data in the dataset
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/e4efbf32-9849-49fc-a1f5-57bf47e0b4b7)

drop_duplicates() is used to drop or delete duplicates value in the dataset
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/babc55a0-3d24-4907-9312-42fbe1ef8a11)

Task. 2) Is there any Null Value present in any column ? Show with Heat-map.

.isnull() function is used to check null values present in the dataset
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/271f6109-7d8c-48ed-a9d6-a3655647d853)

.isnull().sum() function is used to sum all the null values present in each column of the datset
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/c69920d3-e87c-4855-a1a4-0ff1b951a948)

Importing seaborn as sns for heatmap of the null values 
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/e05f7201-3837-4ff6-a5ac-23f68997db01)

Q. 1) For 'Friends', what is the Show Id and Who is the Director of this show ?
df[df['Title'].isin(['Friends'])] used to find any title named as Friends in the dataset

![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/0f68a318-126c-48de-bb04-04367d684985)

df[df['Title'].str.contains('Friends')] is used to check 'Friends' as a word or string in the title column
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/e78a9e3b-c108-47e6-a900-2a81cc33a921)

Q. 2) In which year the highest number of the TV Shows & Movies were released ? Show with Bar Graph.

df['Date_N']=pd.to_datetime(df['Release_Date']) 
df['Date_N'].dt.year.value_counts() I have used these codes to check the year in which the highest number of the TV Shows & Movies were released
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/ce3f915f-456c-4065-8e29-198d3f62386c)

 then to plot the bar is used 
df['Date_N'].dt.year.value_counts().plot(kind='bar')
 ![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/97fec936-89e0-4aab-ac89-023805ea902c)

 #Q. 3) How many Movies & TV Shows are in the dataset ? Show with Bar Graph.
 
 df.groupby('Category').Category.count() is used to group the categories accordingly
 
 sns.countplot(df['Category']) is used for plotting graph
 ![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/c2ed664c-99cd-4c81-adb9-53f58b94dd04)

#Q. 4) Show all the Movies that were released in year 2000.

#Creating new column

df['Year']=df['Date_N'].dt.year
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/2f66bdaa-a21f-4516-8e09-c359db7d3cdd)

df[(df['Category']== 'Movie')&(df['Year']==2000)] by this I was able to find out all the movies title which were released in the year 2000
           there were no result in the year 2000 so I had to check for 2020 to make sure my code was working
df[(df['Category']== 'Movie')&(df['Year']==2020)] by this I checked the movies which were released in 2020
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/5e3bc524-c8c7-4e46-8f1d-e488f8e4dbc6)


#Q. 5) Show only the Titles of all TV Shows that were released in India only.

df[ (df['Category']=='TV Show') & (df['Country']=='India')]['Title'] by this I was able to find out names of TV Shows that were released only in India on Netflix
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/70a9d176-e382-4b97-998c-4bc45a05318e)


#Q. 6) Show Top 10 Directors, who gave the highest number of TV Shows & Movies to Netflix ?

df['Director'].value_counts().head(10) it is used by to find out the Directors who featured in most of the movie in Directors column
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/778c3805-ba63-403d-9b7f-8d82129b8701)


#Q. 7) Show all the Records, where "Category is Movie and Type is Comedies" or "Country is India".

df[(df['Category']=='Movie')&(df['Type']=='Comedies')] this code was used by me to find out comedy movies in the category column

then df[(df['Category']=='Movie')&(df['Type']=='Comedies') | (df['Country']=='India')] was used by me to to find out comedy movies available in India
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/3e902da8-7f52-4550-8ea2-12fa260037a4)


#Q. 8) In how many movies/shows, Tom Cruise was cast ?

df[df['Cast']=='Tom Cruise'] this code was to get number of movies in which actor Tom Cruise was casted
           there was no result so had make a new data-frame and used string to find the name of the actor
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/b78ce380-459c-4aa3-a59f-2fe1f2573420)
           
Q. 9) What are the different Ratings defined by Netflix ?
df['Rating'].unique() this .unique() is used to find unique elements of an array and returns these unique elements as a sorted array.By which it was very easy to find out different Ratings defined by Netflix.
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/cded17c3-5d58-4874-98e1-03be929f00e9)


Q. 9.1) How many Movies got the 'TV-14' rating, in Canada ?

df[(df['Category']=='Movie')&(df['Rating']=='TV-14')].shape / this code was used to find out number of TV-14 rated movies
df[(df['Category']=='Movie')&(df['Rating']=='TV-14')&(df['Country']=='Canada')]  / it was to find out number of TV-14 rated movies in Canada
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/5e342048-1120-4204-84e3-c813d21909ad)


9.2) How many TV Shows got the 'R' rating, after year 2018 ?

df[(df['Category']=='TV Show')&(df['Rating']=='R')&(df['Year']>2018)] / this code was used to find out 'R' rated TV Shows which were released after 2018
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/e7573f1d-13d2-45aa-a41a-df5ea6c5cbab)


Q. 10) What is the maximum duration of a Movie/Show on Netflix ?

df.Duration.unique() to find to unique value in duration column
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/617d3038-7353-44a8-8d68-89474802e6c6)


#str.split() is used to break the string into chunks

df[['Minutes','Unit']]=df['Duration'].str.split(' ',expand=True)  

![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/f3c720dd-c480-47a5-ae03-6d2356ae565a)


Q. 11) Which individual country has the Highest No. of TV Shows ?

data_tvshow=df[df['Category']=='TV Show'] / used to make a new column with all the TV Shows

data_tvshow.Country.value_counts() / to find out the max number of TV Shows in a country
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/b0bed3b2-7b54-44e6-8224-c90a78e562c9)


Q. 12) How can we sort the dataset by Year ?

df.sort_values(by='Year') / used to sort dataset by Year
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/405cff8b-a111-4390-b927-1bdadbaa6dce)


df.sort_values(by='Year',ascending=False).head(10) / used to sort dataset in descending order by Year
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/0a5fc0da-2a41-4ebe-a371-ba45e8d0303f)


#Q. 13) Find all the instances where: Category is 'Movie' and Type is 'Dramas' or Category is 'TV Show' & Type is 'Kids' TV'.

df[(df['Category']=='Movie')&(df['Type']=='Dramas')].head(2) / used to find drama movies
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/f4cf78a1-1510-44c8-9d47-d18031a441a3)



df[(df['Category']=='TV Show')&(df['Type']=="Kids' TV")] / used to find kids TV Shows
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/d3d7bfb9-d9fb-4600-87b1-89f86f5c505c)



df[(df['Category']=='Movie')&(df['Type']=='Dramas')|(df['Category']=='TV Show')&(df['Type']=="Kids' TV")]  / used to find both drama movies and kids TV Shows together
![image](https://github.com/PrakharSingh018/NETFLIX-report-with-Python-/assets/138695689/c56bc5af-ee34-439a-a4ea-4bb999ee02e0)
