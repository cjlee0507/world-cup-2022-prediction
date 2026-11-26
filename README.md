# 2022 FIFA World Cup Prediction

Predicts the outcome of every match in the 2022 FIFA World Cup, from the group stage through the final, using classifiers trained on international match results since the 2018 World Cup.

Final project for CS 425 at the University of Tennessee, Knoxville. The full write-up is in [`425_Final_Project_Report.pdf`](425_Final_Project_Report.pdf) and the slides are in [`CS425 Final Project Video Slides.pdf`](CS425%20Final%20Project%20Video%20Slides.pdf).

## How it works

1. **Data**: [`international_matches.csv`](international_matches.csv) has international results with FIFA ranks and each team's mean offense, midfield, and defense ratings. Matches before the 2018 World Cup are dropped and missing ratings are filled with the column mean.
2. **Features**: for each match, the difference between the two teams in offense, midfield, defense, and FIFA rank. The label is whether the home team won.
3. **Models**: support vector machine, logistic regression, and a multi-layer perceptron (scikit-learn), compared on accuracy. Feature subsets were also compared to see which ratings mattered most.
4. **Simulation**: the best model (an MLP using all four features) predicts win probabilities for every group stage match. Teams get expected points, the top two in each group advance, and the bracket is played out through the round of 16, quarterfinals, semifinals, and final. The full tournament was also simulated 1,000 times to count how often each team won.

## Results

- The models reached about **68 to 72% accuracy** on the training split. The MLP with all four features did best, around 72%. These numbers are training accuracy, so held-out accuracy is likely lower.
- The model predicted an **Argentina vs. France final**, which is the final that actually happened. It picked France to win. Argentina won the real final on penalties.

## How to run

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook worldcup22_prediction.ipynb
```

Run the cells from top to bottom. The dataset is included in the repo.
