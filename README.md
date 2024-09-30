# Player Similarity Analysis Using K-Nearest Neighbors (KNN)

## Overview

The objective of this project is to analyze the similarity between cricket players based on their performance in IPL across different game phases. The project utilizes the **K-Nearest Neighbors (KNN)** algorithm with two distance metrics: **Euclidean Distance** and **Cosine Similarity**. The focus is on comparing various players with **V Kohli** to identify the most similar players.

The project involves:
- Stats extraction for every game phase from the ball by ball data for openers and one down batters in IPL
- Pre-processing the stats data
- Implementing KNN with Euclidean and Cosine distances for player comparison
- Visualizing the similarity between players using bar charts and heatmaps

## Data

The dataset used in this project contains ball by ball data of all IPL matches

Dataset link: [Data](https://drive.google.com/drive/folders/12hHtnDi6Py1VMrZnVTMP8dChK0BBnBCX?usp=drive_link)

### Data Structure
Sample data of players after stats extraction for every game phase from the ball by ball data of all IPL matches
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Batter</th>
      <th>Phase</th>
      <th>Batter Runs</th>
      <th>Runs Against Pace</th>
      <th>Runs Against Spin</th>
      <th>Ball</th>
      <th>Batting Average</th>
      <th>Strike Rate</th>
      <th>Fours</th>
      <th>Sixes</th>
      <th>...</th>
      <th>Dismissals</th>
      <th>Pace Dismissals</th>
      <th>Spin Dismissals</th>
      <th>caught</th>
      <th>bowled</th>
      <th>lbw</th>
      <th>run out</th>
      <th>caught and bowled</th>
      <th>stumped</th>
      <th>Dismissal Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>V Kohli</td>
      <td>Powerplay</td>
      <td>2809</td>
      <td>2035.5</td>
      <td>773.5</td>
      <td>2347</td>
      <td>40.128571</td>
      <td>119.684704</td>
      <td>348</td>
      <td>68</td>
      <td>...</td>
      <td>70</td>
      <td>51.5</td>
      <td>18.5</td>
      <td>44</td>
      <td>12</td>
      <td>8</td>
      <td>5</td>
      <td>1</td>
      <td>NaN</td>
      <td>0.029825</td>
    </tr>
    <tr>
      <th>1</th>
      <td>V Kohli</td>
      <td>Middle Overs</td>
      <td>3736</td>
      <td>1709.0</td>
      <td>2027.0</td>
      <td>3065</td>
      <td>42.942529</td>
      <td>121.892333</td>
      <td>252</td>
      <td>117</td>
      <td>...</td>
      <td>87</td>
      <td>52.0</td>
      <td>35.0</td>
      <td>53</td>
      <td>18</td>
      <td>2</td>
      <td>9</td>
      <td>2</td>
      <td>3.0</td>
      <td>0.028385</td>
    </tr>
    <tr>
      <th>2</th>
      <td>V Kohli</td>
      <td>Death Overs</td>
      <td>1469</td>
      <td>1028.0</td>
      <td>441.0</td>
      <td>824</td>
      <td>24.081967</td>
      <td>178.276699</td>
      <td>108</td>
      <td>88</td>
      <td>...</td>
      <td>61</td>
      <td>48.5</td>
      <td>12.5</td>
      <td>41</td>
      <td>9</td>
      <td>2</td>
      <td>6</td>
      <td>1</td>
      <td>2.0</td>
      <td>0.074029</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 23 columns</p>
</div>

## KNN Model and Similarity Metrics

The project uses the **K-Nearest Neighbors (KNN)** algorithm to find similar players based on the following distance metrics:

### K-Nearest Neighbors (KNN)
- The code utilizes the **K-Nearest Neighbors (KNN)** algorithm for identifying similar players based on their performance metrics.
- KNN computes distances based on both **Euclidean distance** and **Cosine similarity**.
- The nearest neighbors are determined using the metrics for the target player (i.e., Virat Kohli), and the most similar player is identified.

### 1. Euclidean Distance
- **Definition**: Measures the straight-line distance between two points in a multi-dimensional space, with each player's statistics as a point.
- **How It Works**: Calculates the absolute values of metrics, reflecting overall performance. Players with similar statistics score closely, regardless of specific performance traits.

### 2. Cosine Similarity
- **Definition**: Measures the cosine of the angle between two vectors, focusing on the orientation of performance metrics rather than magnitude.
- **How It Works**: Treats metrics as vectors, assessing similarity in scoring patterns rather than total runs.

### Implications of Differences
- A player may have similar overall statistics to Kohli (Euclidean) but differ in playing style (Cosine), leading to variations in similarity rankings:
    - **Euclidean** for overall performance similarity.
    - **Cosine** for style and scoring pattern similarity.

## Visualizations

The results of the analysis are visualized using:
- **Bar Charts**: Showing Euclidean and Cosine distances between players and **V Kohli**.
- **Heatmaps**: Visualizing the similarity across all players for both distance metrics, making it easy to identify closely related players.

## Results
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Phase</th>
      <th>Metric</th>
      <th>Most Similar Player</th>
      <th>Distance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Powerplay</td>
      <td>Euclidean</td>
      <td>KS Williamson</td>
      <td>2.720447</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Powerplay</td>
      <td>Cosine</td>
      <td>DA Warner</td>
      <td>0.103638</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Middle Overs</td>
      <td>Euclidean</td>
      <td>KS Williamson</td>
      <td>3.631053</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Middle Overs</td>
      <td>Cosine</td>
      <td>DA Warner</td>
      <td>0.094542</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Death Overs</td>
      <td>Euclidean</td>
      <td>KS Williamson</td>
      <td>1.991914</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Death Overs</td>
      <td>Cosine</td>
      <td>RG Sharma</td>
      <td>0.108374</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Overall</td>
      <td>Euclidean</td>
      <td>KS Williamson</td>
      <td>1.991914</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Overall</td>
      <td>Cosine</td>
      <td>DA Warner</td>
      <td>0.094542</td>
    </tr>
  </tbody>
</table>
</div>

![image](https://github.com/user-attachments/assets/f04c0dd9-a194-4c82-896d-e329633a850a) ![image](https://github.com/user-attachments/assets/be186ebb-215a-41f8-a5b1-2349e8121fd9)
![image](https://github.com/user-attachments/assets/d90c66d0-3b52-47b9-9007-ad47829d5f3b) ![image](https://github.com/user-attachments/assets/456a9af1-2f46-4111-a0db-ab54ff9385c3)



The project provides a detailed comparison of player similarities. The key findings are presented as table, plots, with players who exhibit performance patterns similar to **The G.O.A.T** **V Kohli** highlighted based on their calculated distances.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any queries or contributions, feel free to reach out to:
- **Ariharasudhan A** - [Email](mailto:ariadaikalam1234@gmail.com)
