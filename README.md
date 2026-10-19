# SC5002 Lab Assignment: Search and Regression

This project explores classical search algorithms and regression models for SC5002 Artificial Intelligence Fundamentals & Applications at Nanyang Technological University.

## Project overview

- **Part 1:** Manually trace BFS and A* on a directed graph, then solve an 8-puzzle using A*. The calculations and AI learning reflections are included in the submitted PDF report.
- **Part 2:** Run the provided Python template in Google Colab to compare Linear Regression with Ridge Regression on the California Housing dataset.

## Notebook

`SC5002_Lab_Assignment.ipynb` contains the Part 2 code, model evaluation outputs, and performance comparison bar chart.

## Dataset

The notebook loads the California Housing dataset using `fetch_california_housing(as_frame=True)` and randomly samples 1,000 records with `random_state=42`.

- **Prediction target:** `MedHouseVal`, the median house value for a district.
- **Input features:** `MedInc`, `HouseAge`, `AveRooms`, `AveBedrms`, `Population`, `AveOccup`, `Latitude`, and `Longitude`.

The features are standardized using `StandardScaler`. The sample is split into 80% training data and 20% test data. The reported scores are the mean R-squared values from five-fold cross-validation on the training set. The provided template does not use the held-out test set for a final evaluation.

## How to run

1. Download `SC5002_Lab_Assignment.ipynb` from this repository.
2. Open [Google Colab](https://colab.research.google.com/).
3. Select **File > Upload notebook** and choose the downloaded notebook.
4. Select **Runtime > Run all** to execute the cells in order. Internet access is required to fetch the dataset if it is not already cached.
5. Review the dataset preview, model scores, and comparison bar chart.

The Python imports use NumPy, pandas, Matplotlib, and scikit-learn.

## Results

| Model | Alpha | Mean 5-Fold CV R-squared |
|---|---:|---:|
| Linear Regression | Not applicable | 0.6457 |
| Ridge Regression | 0.1 | 0.6457 |
| Ridge Regression | 10.0 | 0.6443 |
| Ridge Regression | 1000.0 | 0.3574 |

Linear Regression and Ridge with alpha 0.1 have the same score to four decimal places. Ridge with alpha 10 performs similarly. At alpha 1000, performance drops substantially, consistent with excessive coefficient shrinkage and underfitting.

## Search results

- **BFS:** S -> F -> G, with two edges and a total cost of 9.
- **A*:** S -> B -> D -> G, with a total cost of 7.
- **8-puzzle:** The blank moves Up, Up, Left, Down, Right to reach the goal in five moves. The heuristic counts misplaced numbered tiles and excludes the blank.

## Learning with generative AI

Generative AI helped explain admissible heuristics through a GPS analogy and check the manual 8-puzzle calculations and node-selection reasoning. It also helped explain regression, feature scaling, Ridge regularization, alpha, five-fold cross-validation, and R-squared. The submitted report records the prompts and summaries of these learning discussions.

## Evaluation note

The notebook follows the supplied course template, which fits `StandardScaler` on the full sampled dataset before splitting. This allows information from validation and test features to influence scaling. For a stricter evaluation, preprocessing would be fitted separately within each cross-validation training fold, for example using a scikit-learn pipeline.
