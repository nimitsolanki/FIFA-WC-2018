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

**# Team patcipating in the world cup**

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

<h1><a id="Group_matches_4"></a>Group matches</h1>
<p>Russia and Saudi Arabia<br>
Winner: Russia<br>
Probability of Russia winning:  0.664<br>
Probability of Draw:  0.220<br>
Probability of Saudi Arabia winning:  0.115</p>
<p>Uruguay and Egypt<br>
Winner: Uruguay<br>
Probability of Uruguay winning:  0.590<br>
Probability of Draw:  0.341<br>
Probability of Egypt winning:  0.069</p>
<p>Iran and Morocco<br>
Draw<br>
Probability of Iran winning:  0.236<br>
Probability of Draw:  0.429<br>
Probability of Morocco winning:  0.335</p>
<p>Portugal and Spain<br>
Draw<br>
Probability of Portugal winning:  0.297<br>
Probability of Draw:  0.351<br>
Probability of Spain winning:  0.351</p>
<h1><a id="Group_16_29"></a>Group 16</h1>
<p>Portugal and Uruguay<br>
Winner: Portugal<br>
Probability of Portugal winning:  0.428<br>
Probability of Draw:  0.285<br>
Probability of Uruguay winning:  0.287</p>
<p>France and Croatia<br>
Winner: France<br>
Probability of France winning:  0.481<br>
Probability of Draw:  0.252<br>
Probability of Croatia winning:  0.267</p>
<p>Brazil and Mexico<br>
Winner: Brazil<br>
Probability of Brazil winning:  0.695<br>
Probability of Draw:  0.209<br>
Probability of Mexico winning:  0.096</p>
<p>England and Colombia<br>
Winner: England<br>
Probability of England winning:  0.516<br>
Probability of Draw:  0.368<br>
Probability of Colombia winning:  0.116</p>
<p>Spain and Russia<br>
Winner: Spain<br>
Probability of Spain winning:  0.529<br>
Probability of Draw:  0.280<br>
Probability of Russia winning:  0.191</p>
<p>Argentina and Peru<br>
Winner: Argentina<br>
Probability of Argentina winning:  0.713<br>
Probability of Draw:  0.212<br>
Probability of Peru winning:  0.075</p>
<p>Germany and Switzerland<br>
Winner: Germany<br>
Probability of Germany winning:  0.672<br>
Probability of Draw:  0.192<br>
Probability of Switzerland winning:  0.137</p>
<p>Belgium and Poland<br>
Winner: Belgium<br>
Probability of Belgium winning:  0.513<br>
Probability of Draw:  0.202<br>
Probability of Poland winning:  0.285</p>
<h1><a id="Quarters_78"></a>Quarters</h1>
<p>Portugal and France<br>
Winner: Portugal<br>
Probability of Portugal winning:  0.437<br>
Probability of Draw:  0.256<br>
Probability of France winning:  0.307</p>
<p>Argentina and Spain<br>
Winner: Argentina<br>
Probability of Argentina winning:  0.518<br>
Probability of Draw:  0.262<br>
Probability of Spain winning:  0.220</p>
<p>Brazil and England<br>
Winner: Brazil<br>
Probability of Brazil winning:  0.525<br>
Probability of Draw:  0.216<br>
Probability of England winning:  0.260</p>
<p>Germany and Belgium<br>
Winner: Germany<br>
Probability of Germany winning:  0.563<br>
Probability of Draw:  0.269<br>
Probability of Belgium winning:  0.167</p>
<h1><a id="Semifinal_103"></a>Semifinal</h1>
<p>Brazil and Portugal<br>
Winner: Brazil<br>
Probability of Brazil winning:  0.705<br>
Probability of Draw:  0.152<br>
Probability of Portugal winning:  0.143</p>
<p>Germany and Argentina<br>
Winner: Germany<br>
Probability of Germany winning:  0.441<br>
Probability of Draw:  0.264<br>
Probability of Argentina winning:  0.295</p>
<h1><a id="Final_116"></a>Final</h1>
<p>Germany and Brazil<br>
Winner: Brazil<br>
Probability of Germany winning:  0.359<br>
Probability of Draw:  0.220<br>
Probability of Brazil winning:  0.421</p>
