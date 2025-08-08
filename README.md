# IPL Cricket Match Win Probability Predictor

## Overview

This project is a machine learning-based system that predicts the probability of a team winning an IPL (Indian Premier League) cricket match in real-time during the second innings. The model analyzes various match parameters and provides win probability predictions to help understand the dynamics of T20 cricket matches.

## Features

- **Real-time Win Probability Prediction**: Calculates the probability of the batting team winning during the second innings
- **Comprehensive Match Analysis**: Considers multiple factors including runs, balls, wickets, and run rates
- **Machine Learning Model**: Uses Logistic Regression with feature engineering
- **Data Visualization**: Includes learning curves, validation curves, and ROC analysis
- **Interactive Predictions**: Allows users to input match scenarios and get instant predictions

## Dataset

The project uses two main datasets:
- **matches.csv**: Contains match-level information including teams, venues, winners, etc.
- **deliveries.csv**: Contains ball-by-ball data including runs, wickets, overs, etc.

## Key Features Analyzed

The model considers the following features for prediction:

1. **Batting Team**: The team currently batting
2. **Bowling Team**: The team currently bowling
3. **City**: Match venue
4. **Runs Left**: Remaining runs to chase
5. **Balls Left**: Remaining balls in the innings
6. **Wickets**: Wickets remaining for the batting team
7. **Total Runs**: Target score to chase
8. **Current Run Rate (CRR)**: Current scoring rate
9. **Required Run Rate (RRR)**: Required scoring rate to win

## Methodology

### Data Preprocessing
1. **Data Cleaning**: Handles missing values and team name standardization
2. **Feature Engineering**: 
   - Calculates runs left, balls left, and wickets remaining
   - Computes current run rate (CRR) and required run rate (RRR)
   - Creates match outcome labels (1 for win, 0 for loss)

### Model Architecture
- **Preprocessing Pipeline**: Uses ColumnTransformer with OneHotEncoder for categorical variables
- **Machine Learning Model**: Logistic Regression classifier
- **Pipeline**: Combines preprocessing and model in a single pipeline

### Model Evaluation
- **Accuracy Score**: Measures overall prediction accuracy
- **Learning Curves**: Analyzes model performance vs training data size
- **Validation Curves**: Optimizes hyperparameters (C parameter)
- **ROC Curve**: Evaluates model's classification performance

## Usage

### Prerequisites
```bash
pip install numpy pandas matplotlib scikit-learn
```

### Running the Project
1. Ensure you have the required datasets (`matches.csv` and `deliveries.csv`)
2. Open the Jupyter notebook `project.ipynb`
3. Run all cells to train the model and make predictions

### Making Predictions
```python
# Example input for prediction
input_data = pd.DataFrame([{
    'batting_team': 'Chennai Super Kings',
    'bowling_team': 'Kings XI Punjab',
    'city': 'Bangalore',
    'runs_left': 100,
    'balls_left': 60,
    'wickets': 5,
    'total_runs_x': 200,
    'crr': 8.5,
    'rrr': 10.0
}])

# Get win probability
probabilities = pipe.predict_proba(input_data)
win_prob = probabilities[0][1] * 100
print(f"Win probability: {win_prob:.1f}%")
```

## Model Performance

The model demonstrates:
- **Learning Curves**: Shows how model performance improves with more training data
- **Validation Curves**: Optimizes regularization strength for best performance
- **ROC Analysis**: Evaluates the model's ability to distinguish between win/loss scenarios

## Key Insights

1. **Real-time Analysis**: The model can provide predictions at any point during the second innings
2. **Feature Importance**: Run rate and required run rate are crucial factors
3. **Team Performance**: Different teams show varying win probabilities under similar conditions
4. **Venue Impact**: Match location affects win probability due to pitch conditions

## Technical Details

- **Programming Language**: Python
- **Libraries Used**: 
  - NumPy for numerical operations
  - Pandas for data manipulation
  - Scikit-learn for machine learning
  - Matplotlib for visualization
- **Model Type**: Logistic Regression with feature engineering
- **Data Sources**: IPL cricket match datasets

## Future Enhancements

1. **Additional Features**: Include player statistics, pitch conditions, weather data
2. **Advanced Models**: Implement ensemble methods or deep learning approaches
3. **Real-time API**: Create a web service for live match predictions
4. **Mobile App**: Develop a mobile application for cricket fans
5. **Historical Analysis**: Add trend analysis and team performance over seasons

## Contributing

Feel free to contribute to this project by:
- Adding new features
- Improving model performance
- Enhancing data preprocessing
- Creating additional visualizations

## License

This project is open source and available under the MIT License.

---

**Note**: This project is for educational and analytical purposes. Predictions are based on historical data and should not be used for betting or gambling purposes. 