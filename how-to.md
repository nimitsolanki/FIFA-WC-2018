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

# Group matches 
Russia and Saudi Arabia
Winner: Russia
Probability of Russia winning:  0.664
Probability of Draw:  0.220
Probability of Saudi Arabia winning:  0.115

Uruguay and Egypt
Winner: Uruguay
Probability of Uruguay winning:  0.590
Probability of Draw:  0.341
Probability of Egypt winning:  0.069

Iran and Morocco
Draw
Probability of Iran winning:  0.236
Probability of Draw:  0.429
Probability of Morocco winning:  0.335

Portugal and Spain
Draw
Probability of Portugal winning:  0.297
Probability of Draw:  0.351
Probability of Spain winning:  0.351

# Group 16
Portugal and Uruguay
Winner: Portugal
Probability of Portugal winning:  0.428
Probability of Draw:  0.285
Probability of Uruguay winning:  0.287

France and Croatia
Winner: France
Probability of France winning:  0.481
Probability of Draw:  0.252
Probability of Croatia winning:  0.267

Brazil and Mexico
Winner: Brazil
Probability of Brazil winning:  0.695
Probability of Draw:  0.209
Probability of Mexico winning:  0.096

England and Colombia
Winner: England
Probability of England winning:  0.516
Probability of Draw:  0.368
Probability of Colombia winning:  0.116

Spain and Russia
Winner: Spain
Probability of Spain winning:  0.529
Probability of Draw:  0.280
Probability of Russia winning:  0.191

Argentina and Peru
Winner: Argentina
Probability of Argentina winning:  0.713
Probability of Draw:  0.212
Probability of Peru winning:  0.075

Germany and Switzerland
Winner: Germany
Probability of Germany winning:  0.672
Probability of Draw:  0.192
Probability of Switzerland winning:  0.137

Belgium and Poland
Winner: Belgium
Probability of Belgium winning:  0.513
Probability of Draw:  0.202
Probability of Poland winning:  0.285

# Quarters
Portugal and France
Winner: Portugal
Probability of Portugal winning:  0.437
Probability of Draw:  0.256
Probability of France winning:  0.307

Argentina and Spain
Winner: Argentina
Probability of Argentina winning:  0.518
Probability of Draw:  0.262
Probability of Spain winning:  0.220

Brazil and England
Winner: Brazil
Probability of Brazil winning:  0.525
Probability of Draw:  0.216
Probability of England winning:  0.260

Germany and Belgium
Winner: Germany
Probability of Germany winning:  0.563
Probability of Draw:  0.269
Probability of Belgium winning:  0.167

# Semifinal 
Brazil and Portugal
Winner: Brazil
Probability of Brazil winning:  0.705
Probability of Draw:  0.152
Probability of Portugal winning:  0.143

Germany and Argentina
Winner: Germany
Probability of Germany winning:  0.441
Probability of Draw:  0.264
Probability of Argentina winning:  0.295

# Final 
Germany and Brazil
Winner: Brazil
Probability of Germany winning:  0.359
Probability of Draw:  0.220
Probability of Brazil winning:  0.421

