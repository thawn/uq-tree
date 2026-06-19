# Conformal Prediction
## Abstract

Conformal prediction (CP) provides theoretical guarantees of predictive uncertainty in distribution-free, finite-sample, model-agnostic manner, while serving as a lightweight wrapper around any (pre)trained model. In essence, CP guarantees coverage: with high probability and at a user chosen significance level α, the ground truth is contained within a prediction set or interval. In order for this guarantee to hold, one needs to calibrate the (pre)trained model that will be deployed during inference.

CP is applicable independently of the downstream task, including classification, regression, forecasting, segmentation, OOD/anomaly detection, online methods...

1. [Anastasios N. Angelopoulos. Stephen Bates. “A Gentle Introduction to Conformal Prediction and Distribution-Free Uncertainty Quantification.” Foundations and Trends in Machine Learning, December 2022](https://doi.org/10.1561/2200000101)

2. [Ryan Tibshirani. “Conformal Prediction.” Advanced Topics in Statistical Learning, course notes, Spring 2024.](https://www.stat.berkeley.edu/~ryantibs/statlearn-s24/lectures/conformal.pdf) 

3. [Onboard conformal prediction for domain shift in earth observation](https://www.spiedigitallibrary.org/conference-proceedings-of-spie/13670/136700D/Onboard-conformal-prediction-for-domain-shift-in-Earth-observation/10.1117/12.3070046.short) 

4. [Class-Conditional Robust Conformal Prediction for Structured Perturbations](https://proceedings.mlr.press/v266/marchante-arjona25a.html)

5. [Stephen Bates. Emmanuel Candès. Lihua Lei. Yaniv Romano. Matteo Sesia. "Testing for outliers with conformal p-values." Ann. Statist. 51 (1) 149 - 178, February 2023.](https://doi.org/10.1214/22-AOS2244) (see also https://github.com/OliverHennhoefer/nonconform)

6. [Vianney Taquet. Vincent Blot. Thomas Morzadec. Louis Lacombe. Nicolas Brunel. “MAPIE: an open-source library for distribution-free uncertainty quantification.” arXiv preprint arXiv:2207.12274, 2022.](https://mapie.readthedocs.io/en/stable/)
 

## Easy to apply ⭐️⭐️⭐️⭐️★
_How hard is the method to implement? Is a deep understanding of the theory behind the method necessary?_

- There exists many packages/implementations for post-hoc (model-agnostic) way
 
 - The standard CP method, split conformal prediction, is easily and offers interpreable outcomes with minimal assumptions
 
 - Possible uncertainty metrics: empirical coverage, prediction set/interval size, conformal quantiles, conformal p- or e-values, conformalized risks, and many others.

 - Wide range of advanced variants and modifications can be constructed for complex data and applications are available.
 
 - Deep understanding of the method not necessarily required, except for practical understanding of exchangeability of the calibration and test data that can be tested via permutations test. 

## Data Compatibility ⭐️⭐️⭐️⭐️⭐️
_Is the method compatible with a wide range of data types/sizes/labels/… Are there any restrictions in applicability?_

* It can work with any data type, as the method relies on setting any heuristic conformal/similarity measure.

* This method requiers a dataset size in the order of 100's to 1000's data points, along with its correspondent labels (ground truth) for calibration before deployment. 



## Task Compatibility ⭐️⭐️⭐️⭐️⭐️
_Is the method compatible with a wide range of different tasks? Are there any restrictions in applicability? How is the OOD behaviour? Is calibration required?_

- Method is agnostic to the model and the downstream task, including classification, regression, forecasting, segmentation, OOD/anomaly detection, online methods...

- Particular examples may include anomaly detection, autonomous driving, quantum processor calibration, biomedical risk control...
 
- The method is properly calibrated to produce an empirical result in accordance to the theoretical threshold established.

## Ease of integration ⭐️⭐️⭐️⭐️★
_Is the method easy to integrate into an existing pipeline? Does it require model modifications? Does it require retraining? Are there any architectural requirements for the model?_

- No model modification is required, it can directly produce uncertainty estimates for a pre-trained model.

- Acts as a low-complexity wrapper on the trained model.


## Computationally Cheap ⭐️⭐️⭐️⭐️★
_Is the use of the method cheap in terms of computational cost? Is there a difference between training and inference steps?_

- Highly depends on the chosen approach/variant. Split conformal prediciton has a very low computational cost. Additionally, the computational efficiency has often an approx. inverse relationship with statistical efficiency.
- Calibration of the conformal method requires access to calibration dataset logits and ground truth. 
- Can be done on CPU, parallelization possible for GPUs.
- Inference needs to be modified to use the calibrated threshold and the output is a interval/set prediction instead of a point prediction.


## Caveats
 _Does the method have any general caveats? Does it have any caveats for specific tasks or in specific cases?_

- Consideration of the exchangeability assumption between calibration and test data via permutation tests. 

- Several variants exist for treating non-exchangeable data.
