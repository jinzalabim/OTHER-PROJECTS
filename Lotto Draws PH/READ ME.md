# Lotto Prediction System Using Machine Learning

---

## Project Overview
This project aims to predict the most probable winning numbers for lotto draws using historical data and machine learning. The system dynamically updates as new results are added and generates predictions for the next day’s draw based on patterns in the dataset.

---

## Features
1. **Add Winning Numbers**:  
   Allows users to add winning numbers from the latest draw to the dataset.
   
2. **Predict Next Day's Numbers**:  
   Trains a Random Forest Classifier on historical data and predicts the most probable winning numbers for the next day.

3. **Dynamic Dataset Updates**:  
   Automatically saves the dataset to a CSV file and reloads it when needed, allowing for persistent storage of data.

---

## Requirements
- Python 3.8 or later
- Required libraries:
  - pandas
  - scikit-learn
  - os (built-in)

You can install the required libraries using:
```bash
pip install pandas scikit-learn
```

## Dataset Structure
The dataset is stored in a CSV file (`lotto_data.csv`) with the following columns:
- **DRAW DATE**: Date of the draw (formatted as `mm/dd/yyyy`).
- **Num1 to Num6**: Winning numbers for the draw.

Additional columns (derived during processing):
- **Month**: Month of the draw.
- **Day**: Day of the draw.
- **DayOfWeek**: Day of the week (0 = Monday, 6 = Sunday).

---

## Usage

### Add New Results
Use the `add_new_results()` function to add new winning numbers to the dataset:
```python
add_new_results('11/22/2024', [3, 15, 27, 34, 42, 55])
```

This will save the new data to ```lotto_data.csv``` and make it available for future predictions.

### Predict Next Day's Numbers
Call the ```predict_next_day()``` function to get the most probable numbers for the next day:
```python
predicted_numbers = predict_next_day()
print("Predicted Numbers for Tomorrow:", predicted_numbers)
```
### Dynamic Updates
After the next draw, add the latest results using ```add_new_results()``` and re-run the prediction for the following day.


## How It Works

### Data Preparation:
- The **DRAW DATE** is parsed to extract key features such as:
  - **Month**: The month the draw occurred.
  - **Day**: The day of the month the draw took place.
  - **DayOfWeek**: The day of the week (e.g., Monday = 0, Sunday = 6).

### Machine Learning Model:
- A separate **Random Forest Classifier** is trained for each number position (`Num1` to `Num6`), learning patterns from the historical data to make predictions.

### Prediction:
- The trained model predicts the most probable winning numbers for the next draw, based on historical trends and patterns identified from past data.

### Dataset Update:
- Winning numbers are dynamically added to the dataset, which persists across sessions. This allows the model to continually improve as more data becomes available.

---

> [!CAUTION]
> This system is purely for educational purposes and entertainment. Predicting lottery numbers is inherently random, and there is **no guarantee of winning**. Using this model to predict lottery numbers does **not** increase the likelihood of winning.
