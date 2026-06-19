# Monte Carlo Dropout
## Abstract

Monte Carlo Dropout (MC Dropout) uses dropout during training and inference to estimate model (epistemic) uncertainty. By performing N stochastic forward passes at test time, it approximates a Bayesian ensemble at low cost.

* Paper: Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning ([Gal & Ghahramani, _ICML 2016_](https://proceedings.mlr.press/v48/gal16.html))
    Implementation: Enable dropout at test time (e.g., model.train() in PyTorch) and perform N forward passes.

## Easy to apply ⭐️⭐️⭐️⭐️★

Simple to implement—requires only dropout layers and enabling them during inference. No changes to training needed.

## Data Compatibility ⭐️⭐️⭐️⭐️★

Works with any data type (images, text, tabular, time series) and shape. Less reliable on sparse or low-dimensional data with disconnected clusters. 

## Task Compatibility ⭐️⭐️⭐️★★

Applies to classification, regression, and some generative tasks. Uncertainty is often poorly calibrated; post-hoc calibration (e.g., temperature scaling) is usually required for reliable use. OOD detection is limited compared to advanced methods.

## Ease of integration ⭐️⭐️⭐️⭐️★

No architectural changes or retraining needed if dropout was used in training. Only minor code updates to enable dropout and sample multiple passes.

## Computationally Cheap ⭐️⭐️★★★

Inference cost scales linearly with the number of forward passes (typically 10–100), which may limit real-time or embedded use. No extra training cost.

## Caveats

* *Poor calibration out-of-the-box*: Raw uncertainty scores often do not reflect true error probabilities and require post-hoc calibration.
* *Limited expressiveness*: As an approximation to Bayesian inference, MC Dropout underestimates uncertainty, especially in high-dimensional or complex models.
* *Dependence on dropout placement*: Performance depends on where and how dropout is applied; shallow or sparse dropout may yield unreliable uncertainty estimates.
* *Inadequate for OOD detection without tuning*: While it can signal high uncertainty on some OOD inputs, it may fail on adversarial or semantically close out-of-distribution samples.
* *Not suitable for aleatoric uncertainty*: MC Dropout primarily captures epistemic (model) uncertainty; separate mechanisms are needed to model data (aleatoric) uncertainty.
