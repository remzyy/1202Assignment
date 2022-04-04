# 1202Assignment
import pandas as pd
import matplotlib.pyplot as plt

file_1='youtube_dataset.csv'

#read CSV
raw_df = pd.read_csv(file_1)
raw_df.head()

#rawdata
raw_df
#sort dataframe based on subscribers
df1=raw_df.sort_values(by='subscribers', axis=0, ascending=False)
df1
#subset the dataframe for top 1000 
df2=df1.iloc[0:1000, :]
df2

#channeltype
df3=df2['channeltype'].value_counts()
df3

#Plotting a bar graph
df2['channeltype'].value_counts().plot(kind='barh')

#relational plot of channletype and subscribers for TOP-1000 records using seabornplots
sns.relplot(x='channeltype',y='subscribers', kind='line', data=df2),plt.xticks(rotation=90)

# creating a function to find  the count of channel type
def channeltype(x):
    df3=df2['channeltype'].value_counts()[x]
    print(df3)

#calling the function
channeltype("Music")
#calling the function
channeltype("Games")

#Converting data frame into a csv
df2.to_csv (r'D:\Data Analytics Sem1\1200 Intro to data\Top1000_YT.csv', index = False, header=True)






