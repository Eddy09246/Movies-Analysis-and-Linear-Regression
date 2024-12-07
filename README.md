
# Film Budget vs. Box Office Revenue Analysis

This project explores the relationship between film production budgets and their worldwide box office revenue.  The analysis uses a dataset i scraped from [the-numbers.com](https://www.the-numbers.com/movie/budgets) on December 7, 2024. I investigate this relationship through data exploration, cleaning, visualization, and linear regression modeling.

## Data Exploration and Cleaning

1. **Data Overview:** I examined the dataset's dimensions, inspected the first and last few rows, and checked for missing (NaN) values and duplicates.  Data types were also verified and adjusted where necessary (converting currency strings to numeric values).

2. **Data Type Conversion:** Currency values (USD Production Budget, Domestic Gross, Worldwide Gross) were cleaned to remove '$' and ',' characters, and then converted to numeric types.

3. **Date Handling:** The `Release_Date` column was converted to a datetime format. Rows with invalid or missing release dates were removed.

4. **Zero Revenue Films:** We analyzed films with zero domestic or worldwide revenue.  Films with zero domestic but non-zero international revenue were identified and analyzed separately.  This step helps in understanding the nature of international releases versus domestic-only ones.

5. **Unreleased Films:** I identified and excluded movies that hadn't been released as of the data collection date.

6. **Profitability Analysis:** I Calculated the percentage of movies where production costs exceeded worldwide gross revenue which is 36.46% .

## Data Visualization

Visualizations are crucial to understanding the data:

1. **Scatter Plots:**  Scatter plots of production budget vs. worldwide gross revenue were created using Matplotlib and Plotly.

2. **Temporal Analysis:**  i also made use of scatter plot of release dates versus production budget to visualize how movie budgets have evolved over time. A `Decade` column was created to aggregate film releases into decades for later comparison.

3. **Seaborn Regression Plots:** I made use of seaborn's `regplot()` to visualize the linear relationship between budget and revenue. Separate plots were created for older films (before 1970) and newer films.

## Linear Regression Modeling

A linear regression model was used to quantify the relationship between film budget and revenue.  The model is represented by:

$$ REVENUE = \theta_0 + \theta_1 \times BUDGET $$

Where:

* $REVENUE$ is the predicted worldwide gross revenue.
* $BUDGET$ is the film's production budget.
* $\theta_0$ is the intercept (revenue when budget is zero).
* $\theta_1$ is the slope (change in revenue per unit change in budget).

The model was trained using the "new films" dataset (films released in or after 1970).  Key statistics for the model are:

* **Coefficients (θ₀ and θ₁):** The intercept and slope of the regression line were determined.
* **R-squared (V-r-squared):**  This value (between 0 and 1),  represents the proportion of the variance in the dependent variable (revenue) that is predictable from the independent variable (budget). A higher R-squared indicates a better fit.  The V-r-squared helps us evaluate how much of the revenue variation our budget is able to explain.  A higher V-r-squared implies that the budget strongly influences the revenue.The 0.538 V-r-squared value from the model signifies that changes in the production budget explain about 54% of the changes in worldwide gross revenue. Other factors not included in the model, like marketing, director, genre, star cast, critical reception, and more, likely account for the remaining 46%. This emphasizes that budget isn't the only important variable influencing a film's financial success.

## Conclusion

The project demonstrates the relationship between movie budgets and revenue, although the correlation should not be considered causal in all cases. A linear model can be used to estimate expected revenue based on budget, with the accuracy of these estimates dependent on the R-squared of the model.
