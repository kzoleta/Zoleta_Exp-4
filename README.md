# Zoleta_Exp-4

## Instructions:
Download the ECE Board Exam 2 dataset found on this link: bit.ly/ECEBoardExamDataset and write a
Python script/code in the Jupyter Notebook to do the given problems. You may submit your Jupyter
notebook in the dedicated submission bin.

## ECE Board Exam Problem:
Using data wrangling and data visualization technique with
storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.
1. Create the following data frames based on the format provided:
Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas

## Code:

#Import library
    import seaborn as sns
    import matplotlib.pyplot as plt
    import pandas as pd
    
    #Load the csv file
    df = pd.read_csv('board2.csv')
    df
    #Verification of columns
    print(df.columns)
    #Visayas as constant with Math < 70
    Vis = df[(df['Math'] < 70)&
                    (df['Hometown'] == 'Visayas')].reset_index(drop=True)
    Vis = Vis[['Name', 'Gender', 'Track', 'Math']]
    Vis

a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon

## Code:

    Instru = df[(df['Track'] == 'Instrumentation') & 
                   (df['Hometown'] == 'Luzon') & 
                   (df['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']].reset_index(drop=True)
    Instru

b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female

## Code:

    #List of score columns to calculate the average from
    score_columns = ['Math', 'Electronics', 'GEAS']
    
    #Computing the average score across the specified columns for each student
    df['Average'] = df[score_columns].mean(axis=1)
    
    #Picking only the needed columns
    Mindy = mindy_df[['Name', 'Track', 'Electronics', 'Average']].reset_index(drop=True)
    Mindy

2. Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

## Code:

                #Calculate the average score across relevant columns
        df['Average'] = df[['Math', 'Electronics', 'GEAS']].mean(axis=1)
        
        def plot_all_scores(df, columns, hue='Gender'):
            for col in columns:
                sns.barplot(x='Track', y=col, hue=hue, data=df, palette=['pink', 'black'])
                plt.title(f'{col} Scores by Track and {hue}')
                plt.show()
        
                sns.barplot(x='Hometown', y=col, hue=hue, data=df, palette=['black','yellow'])
                plt.title(f'{col} Scores by Hometown and {hue}')
                plt.show()
        
        #List of columns to plot
        score_columns = ['Math', 'Electronics', 'Average']
        
        #Generating the plots
        plot_all_scores(df, score_columns)
