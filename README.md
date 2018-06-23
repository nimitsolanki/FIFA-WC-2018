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
<p>France and Australia<br>
Winner: France<br>
Probability of France winning:  0.628<br>
Probability of Draw:  0.222<br>
Probability of Australia winning:  0.151</p>
<p>Argentina and Iceland<br>
Winner: Argentina<br>
Probability of Argentina winning:  0.822<br>
Probability of Draw:  0.144<br>
Probability of Iceland winning:  0.034</p>
<p>Peru and Denmark<br>
Winner: Peru<br>
Probability of Peru winning:  0.440<br>
Probability of Draw:  0.166<br>
Probability of Denmark winning:  0.394</p>
<p>Croatia and Nigeria<br>
Winner: Croatia<br>
Probability of Croatia winning:  0.579<br>
Probability of Draw:  0.280<br>
Probability of Nigeria winning:  0.141</p>
<p>Costa Rica and Serbia<br>
Winner: Costa Rica<br>
Probability of Costa Rica winning:  0.338<br>
Probability of Draw:  0.324<br>
Probability of Serbia winning:  0.337</p>
<p>Germany and Mexico<br>
Winner: Germany<br>
Probability of Germany winning:  0.589<br>
Probability of Draw:  0.258<br>
Probability of Mexico winning:  0.153</p>
<p>Brazil and Switzerland<br>
Winner: Brazil<br>
Probability of Brazil winning:  0.756<br>
Probability of Draw:  0.157<br>
Probability of Switzerland winning:  0.087</p>
<p>Sweden and Korea Republic<br>
Winner: Sweden<br>
Probability of Sweden winning:  0.523<br>
Probability of Draw:  0.312<br>
Probability of Korea Republic winning:  0.166</p>
<p>Belgium and Panama<br>
Winner: Belgium<br>
Probability of Belgium winning:  0.771<br>
Probability of Draw:  0.145<br>
Probability of Panama winning:  0.084</p>
<p>England and Tunisia<br>
Winner: England<br>
Probability of England winning:  0.665<br>
Probability of Draw:  0.277<br>
Probability of Tunisia winning:  0.058</p>
<p>Colombia and Japan<br>
Winner: Colombia<br>
Probability of Colombia winning:  0.513<br>
Probability of Draw:  0.204<br>
Probability of Japan winning:  0.284</p>
<p>Poland and Senegal<br>
Winner: Poland<br>
Probability of Poland winning:  0.586<br>
Probability of Draw:  0.248<br>
Probability of Senegal winning:  0.166</p>
<p>Egypt and Russia<br>
Winner: Russia<br>
Probability of Egypt winning:  0.216<br>
Probability of Draw:  0.289<br>
Probability of Russia winning:  0.495</p>
<p>Portugal and Morocco<br>
Winner: Portugal<br>
Probability of Portugal winning:  0.512<br>
Probability of Draw:  0.364<br>
Probability of Morocco winning:  0.124</p>
<p>Uruguay and Saudi Arabia<br>
Winner: Uruguay<br>
Probability of Uruguay winning:  0.670<br>
Probability of Draw:  0.252<br>
Probability of Saudi Arabia winning:  0.078</p>
<p>Spain and Iran<br>
Winner: Spain<br>
Probability of Spain winning:  0.708<br>
Probability of Draw:  0.242<br>
Probability of Iran winning:  0.050</p>
<p>Denmark and Australia<br>
Winner: Denmark<br>
Probability of Denmark winning:  0.560<br>
Probability of Draw:  0.225<br>
Probability of Australia winning:  0.215</p>
<p>France and Peru<br>
Winner: France<br>
Probability of France winning:  0.633<br>
Probability of Draw:  0.222<br>
Probability of Peru winning:  0.145</p>
<p>Argentina and Croatia<br>
Winner: Argentina<br>
Probability of Argentina winning:  0.596<br>
Probability of Draw:  0.259<br>
Probability of Croatia winning:  0.145</p>
<p>Brazil and Costa Rica<br>
Winner: Brazil<br>
Probability of Brazil winning:  0.792<br>
Probability of Draw:  0.160<br>
Probability of Costa Rica winning:  0.048</p>
<p>Iceland and Nigeria<br>
Winner: Nigeria<br>
Probability of Iceland winning:  0.280<br>
Probability of Draw:  0.285<br>
Probability of Nigeria winning:  0.435</p>
<p>Switzerland and Serbia<br>
Winner: Switzerland<br>
Probability of Switzerland winning:  0.438<br>
Probability of Draw:  0.231<br>
Probability of Serbia winning:  0.331</p>
<p>Belgium and Tunisia<br>
Winner: Belgium<br>
Probability of Belgium winning:  0.622<br>
Probability of Draw:  0.248<br>
Probability of Tunisia winning:  0.130</p>
<p>Mexico and Korea Republic<br>
Winner: Mexico<br>
Probability of Mexico winning:  0.510<br>
Probability of Draw:  0.313<br>
Probability of Korea Republic winning:  0.177</p>
<p>Germany and Sweden<br>
Winner: Germany<br>
Probability of Germany winning:  0.585<br>
Probability of Draw:  0.223<br>
Probability of Sweden winning:  0.191</p>
<p>England and Panama<br>
Winner: England<br>
Probability of England winning:  0.792<br>
Probability of Draw:  0.170<br>
Probability of Panama winning:  0.037</p>
<p>Senegal and Japan<br>
Winner: Japan<br>
Probability of Senegal winning:  0.354<br>
Probability of Draw:  0.290<br>
Probability of Japan winning:  0.356</p>
<p>Poland and Colombia<br>
Draw<br>
Probability of Poland winning:  0.367<br>
Probability of Draw:  0.400<br>
Probability of Colombia winning:  0.233</p>
<p>Uruguay and Russia<br>
Winner: Uruguay<br>
Probability of Uruguay winning:  0.388<br>
Probability of Draw:  0.385<br>
Probability of Russia winning:  0.227</p>
<p>Egypt and Saudi Arabia<br>
Winner: Egypt<br>
Probability of Egypt winning:  0.548<br>
Probability of Draw:  0.205<br>
Probability of Saudi Arabia winning:  0.246</p>
<p>Portugal and Iran<br>
Winner: Portugal<br>
Probability of Portugal winning:  0.552<br>
Probability of Draw:  0.357<br>
Probability of Iran winning:  0.091</p>
<p>Spain and Morocco<br>
Winner: Spain<br>
Probability of Spain winning:  0.682<br>
Probability of Draw:  0.248<br>
Probability of Morocco winning:  0.070</p>
<p>France and Denmark<br>
Winner: France<br>
Probability of France winning:  0.623<br>
Probability of Draw:  0.160<br>
Probability of Denmark winning:  0.218</p>
<p>Peru and Australia<br>
Winner: Peru<br>
Probability of Peru winning:  0.461<br>
Probability of Draw:  0.237<br>
Probability of Australia winning:  0.302</p>
<p>Argentina and Nigeria<br>
Winner: Argentina<br>
Probability of Argentina winning:  0.717<br>
Probability of Draw:  0.220<br>
Probability of Nigeria winning:  0.063</p>
<p>Croatia and Iceland<br>
Winner: Croatia<br>
Probability of Croatia winning:  0.739<br>
Probability of Draw:  0.184<br>
Probability of Iceland winning:  0.077</p>
<p>Mexico and Sweden<br>
Winner: Mexico<br>
Probability of Mexico winning:  0.455<br>
Probability of Draw:  0.263<br>
Probability of Sweden winning:  0.282</p>
<p>Germany and Korea Republic<br>
Winner: Germany<br>
Probability of Germany winning:  0.623<br>
Probability of Draw:  0.264<br>
Probability of Korea Republic winning:  0.113</p>
<p>Brazil and Serbia<br>
Winner: Brazil<br>
Probability of Brazil winning:  0.719<br>
Probability of Draw:  0.174<br>
Probability of Serbia winning:  0.108</p>
<p>Switzerland and Costa Rica<br>
Winner: Switzerland<br>
Probability of Switzerland winning:  0.604<br>
Probability of Draw:  0.222<br>
Probability of Costa Rica winning:  0.174</p>
<p>Poland and Japan<br>
Winner: Poland<br>
Probability of Poland winning:  0.532<br>
Probability of Draw:  0.255<br>
Probability of Japan winning:  0.212</p>
<p>Colombia and Senegal<br>
Winner: Colombia<br>
Probability of Colombia winning:  0.573<br>
Probability of Draw:  0.200<br>
Probability of Senegal winning:  0.227</p>
<p>Tunisia and Panama<br>
Winner: Tunisia<br>
Probability of Tunisia winning:  0.638<br>
Probability of Draw:  0.254<br>
Probability of Panama winning:  0.108</p>
<p>Belgium and England<br>
Winner: England<br>
Probability of Belgium winning:  0.261<br>
Probability of Draw:  0.242<br>
Probability of England winning:  0.497</p>
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
