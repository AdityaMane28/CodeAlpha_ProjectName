# Iris Classification and Data Visualization

A Jupyter Notebook project that explores the Iris dataset with data visualizations and trains a multiclass Logistic Regression model to predict iris species from sepal and petal measurements.

## Project files

```text
.
├── iris model.ipynb
├── README.md
└── requirements.txt
```

## Requirements

- Python 3
- The packages listed in `requirements.txt`
- Internet access the first time the notebook loads Seaborn's built-in Iris dataset (unless the dataset is already cached)

## Setup and run

1. Clone or download this repository and open a terminal in the project directory.
2. Install dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

3. Start Jupyter:

   ```bash
   jupyter notebook
   ```

4. Open `iris model.ipynb` and run the cells from top to bottom.

The notebook's first two cells contain bare `pip install` commands, which are not valid Python syntax in a standard notebook code cell. Since the dependencies are installed by the command above, you can remove those two cells or change each command to `%pip install ...` before choosing **Run All**.

## What the notebook does

- Loads the Iris dataset with `seaborn.load_dataset("iris")`.
- Explores the data with line, scatter, bar, count, box, violin, strip, histogram, KDE, and pair plots.
- Uses sepal length, sepal width, petal length, and petal width as input features; predicts the `species` label.
- Splits the data into training and test sets with an 80/20 split, `random_state=42`, and stratification by species.
- Builds a scikit-learn pipeline with median imputation, standard scaling, and Logistic Regression (`max_iter=1000`).
- Prints test accuracy, a confusion matrix, and a classification report.

The notebook reports model results when you run it. No dataset file or trained model artifact is required in the repository because the Iris dataset is loaded through Seaborn.
