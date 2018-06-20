# FIFA-WC-2018
Predict the winner of FIFA World Cup 2018 with the help of LogisticRegression.

**Python 3**
 - pandas
 - numpy
 - matplotlib.pyplot
 - seaborn  
 - matplotlib.ticker 
 - sklearn.model_selection
 - sklearn.linear_model

**# Load data** 

    world_cup = pd.read_csv('datasets/World_Cup_2018_Dataset.csv')
    results = pd.read_csv('datasets/results.csv')

**# narrowing to team patcipating in the world cup**

    worldcup_teams = ['Australia', ' Iran', 'Japan', 'Korea Republic', 
                'Saudi Arabia', 'Egypt', 'Morocco', 'Nigeria', 
                'Senegal', 'Tunisia', 'Costa Rica', 'Mexico', 
                'Panama', 'Argentina', 'Brazil', 'Colombia', 
                'Peru', 'Uruguay', 'Belgium', 'Croatia', 
                'Denmark', 'England', 'France', 'Germany', 
                'Iceland', 'Poland', 'Portugal', 'Russia', 
                'Serbia', 'Spain', 'Sweden', 'Switzerland']
    df_teams_home = results[results['home_team'].isin(worldcup_teams)]
    df_teams_away = results[results['away_team'].isin(worldcup_teams)]
    df_teams = pd.concat((df_teams_home, df_teams_away))
    df_teams.drop_duplicates()
    df_teams.count()

**#Building the model**
Prediction label: The winning_team column will show "2" if the home team has won, "1" if it was a tie, and "0" if the away team has won.

    df_teams_1930 = df_teams_1930.reset_index(drop=True)
    df_teams_1930.loc[df_teams_1930.winning_team == df_teams_1930.home_team,'winning_team']=2
    df_teams_1930.loc[df_teams_1930.winning_team == 'Draw', 'winning_team']=1
    df_teams_1930.loc[df_teams_1930.winning_team == df_teams_1930.away_team, 'winning_team']=0
    
    df_teams_1930.head()


**Group matches** 

    predictions = logreg.predict(pred_set)
    for i in range(fixtures.shape[0]):
        print(backup_pred_set.iloc[i, 1] + " and " + backup_pred_set.iloc[i, 0])
        if predictions[i] == 2:
            print("Winner: " + backup_pred_set.iloc[i, 1])
        elif predictions[i] == 1:
            print("Draw")
        elif predictions[i] == 0:
            print("Winner: " + backup_pred_set.iloc[i, 0])
        print('Probability of ' + backup_pred_set.iloc[i, 1] + ' winning: ', '%.3f'%(logreg.predict_proba(pred_set)[i][2]))
        print('Probability of Draw: ', '%.3f'%(logreg.predict_proba(pred_set)[i][1]))
        print('Probability of ' + backup_pred_set.iloc[i, 0] + ' winning: ', '%.3f'%(logreg.predict_proba(pred_set)[i][0]))
        print("")

