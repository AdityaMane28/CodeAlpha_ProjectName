# Used Car Price Prediction

This project uses a Random Forest regressor to estimate a used car's selling price from vehicle details such as listed price, vehicle age, kilometers driven, fuel type, seller type, transmission, and owner count.

The analysis is in Car_Price_1.ipynb. The notebook loads a CSV, prepares the features, trains a model, evaluates it with RMSE and R-squared, and saves the fitted estimator as CarModel.pkl.

## Repository contents

    .
    ├── Car_Price_1.ipynb
    ├── car data.csv              # Add the source dataset; it is not included here
    ├── requirements.txt
    └── README.md

## Dataset

The notebook expects a file named car data.csv. It is not embedded in the notebook attached for this project. Add the dataset to the repository only if you have permission to share it, and include its original source and license.

The notebook currently reads the file from /content/car data.csv, which is the Google Colab location. For local use, either upload the file to that location in Colab or change the path in the notebook to the CSV's location.

The data columns used by the notebook include Year, Selling_Price, Present_Price, Kms_Driven, Fuel_Type, Seller_Type, Transmission, and Owner. Car_Name is dropped during preparation.

## Run the notebook

1. Install Python 3.9 or later.
2. Install the dependencies:

       pip install -r requirements.txt

3. Add car data.csv and set the file path in the notebook.
4. Restart the notebook kernel and run all cells from the top.

The notebook imports root_mean_squared_error, which was added in scikit-learn 1.4. The requirements file sets that minimum version.

The saved notebook contains a KeyError output on the one-hot-encoding cell. It appears to be from rerunning that cell after its category columns had already been encoded. Starting with a fresh kernel avoids carrying that earlier state forward.

## Workflow

1. Inspect the data with head, shape, info, and describe.
2. Drop Car_Name and convert Year to vehicle age using 2026 - Year.
3. One-hot encode fuel type, seller type, and transmission.
4. Scale Kms_Driven with RobustScaler.
5. Split the rows into training and test sets (80/20, random_state=42).
6. Fit RandomForestRegressor and evaluate predictions with RMSE and R-squared.
7. Save the fitted estimator to CarModel.pkl.

The saved notebook output reports test RMSE of about 0.956 and test R-squared of about 0.960 for one split. These are the notebook's saved results, not a guarantee of future performance. The model itself does not set random_state, so reruns may produce different results.

## Notes for improvement

- The notebook converts model year to vehicle age using the fixed year 2026. Update this reference year when using the project later.
- Scaling and categorical encoding happen before the train/test split. For a stricter evaluation, put preprocessing and the model in a scikit-learn Pipeline and fit it only on training data.
- CarModel.pkl contains the estimator, not the full preprocessing pipeline. Reproducing predictions requires applying the same feature transformations in the same order.
- The notebook imports Matplotlib and Seaborn but currently does not create plots.
- The notebook includes a Flask installation cell, but it does not implement a Flask app; Flask is not required for the current notebook.

## Project description for GitHub

Used car price prediction with a Random Forest regressor. The notebook prepares vehicle data, converts model year to vehicle age, encodes categorical features, scales mileage, and evaluates predictions with RMSE and R-squared.
