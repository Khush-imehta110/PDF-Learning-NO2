Learning Probability Density Function using Roll-Number-Parameterized Non-Linear Model

1. Problem Statement
This assignment aims to learn the parameters of a probability density function after applying
a roll-number-dependent non-linear transformation to real-world air quality data. The task
demonstrates how deterministic transformations affect data distribution and how statistical
parameters can be learned from transformed variables.

2. Dataset Description
- Dataset: India Air Quality Dataset
- Source: Kaggle
- Feature Selected: NO₂ (Nitrogen Dioxide) concentration
- Number of valid samples used: 419,509

NO₂ is selected as it is a continuous environmental variable suitable for density modeling.

3. Methodology

 3.1 Non-Linear Transformation
Each NO₂ value (x) is transformed into a new variable (z) using:
z = x + a_r * sin(b_r * x)

Where:
r is the university roll number
a_r = 0.05 * (r mod 7)
b_r = 0.3 * (r mod 5 + 1)

For roll number "102303769":
a_r = 0.05
b_r = 1.5 

This step introduces controlled non-linearity into the original data.

3.2 Probability Density Function Model
The transformed variable (z) is assumed to follow the probability density function:
p(z) = c * e^{-lambda * (z - mu)^2}

This form resembles a Gaussian distribution, where:
'mu' represents the center of the distribution
'lambda' controls the spread
'c' ensures normalization

3.3 Parameter Estimation
The parameters are estimated using analytical, data-driven methods:
'mu' is estimated using the sample mean of z
'Variance' (sigma^2) is computed from the data
'lambda' = 1/(2*sigma^2)
'c' = sqrt(lambda / pi) , ensuring the PDF integrates to 1

This approach provides a direct, closed-form estimation of the parameters based on statistical properties of the transformed data.

4. Results
 4.1 Estimated Parameter Table

| Parameter | Interpretation | Estimated Value |
|----------|----------------|-----------------|
| μ | Mean of transformed variable ( z ) | 25.811311026855478 |
| λ | Controls spread of the distribution | 0.001460711615279084 |
| c | Normalization constant | 0.021562906761539043 |
These values were obtained directly from the transformed data without any iterative optimization.


 4.2 Result Visualization
A plot of the learned probability density function ( p(z) ) versus ( z ) is generated.
The curve exhibits a smooth bell-shaped structure, confirming that the estimated parameters
appropriately model the transformed data distribution.

5. Discussion
The non-linear transformation slightly perturbs the original NO₂ distribution while preserving
its overall structure. The learned PDF parameters successfully capture the central tendency
and variability of the transformed data, demonstrating the suitability of the chosen estimation methodology for this task.

6. Conclusion
This assignment demonstrates the impact of deterministic non-linear transformations on real-world
data and the effectiveness of analytical parameter estimation for probability density learning.
The entire workflow is reproducible, interpretable, and grounded in statistical principles.

7. Tools and Technologies
- Python
- NumPy
- Pandas
- Matplotlib
- Google Colab
