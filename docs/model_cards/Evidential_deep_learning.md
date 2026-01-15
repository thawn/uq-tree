# Evidential Deep Learning
## Abstract
Evidential Deep Learning (EDL) frames uncertainty quantification through the lens of evidence theory by having the model predict parameters of a higher-order (second-order) probability distribution—Normal-Inverse-Gamma (NIG) for regression or Dirichlet for classification. Instead of outputting point predictions, the network learns to output the parameters of a distribution over distributions, where uncertainty is interpreted as "lack of evidence". This allows the model to naturally separate aleatoric (data) and epistemic (model) uncertainty in a single forward pass, outputting higher uncertainty when it has seen fewer similar examples during training.

* **Classification Paper:** [Evidential Deep Learning to Quantify Classification Uncertainty (Sensoy et al., NeurIPS 2018)](http://arxiv.org/abs/1806.01768)
* **Regression Paper:** [Deep Evidential Regression (Amini et al., NeurIPS 2020)](https://arxiv.org/abs/1910.02600)
* **Review:** [A Survey on Evidential Deep Learning (Ulmer, 2021)](http://arxiv.org/abs/2110.03051)
* **Implementation:** [GitHub - aamini/evidential-deep-learning](https://github.com/aamini/evidential-deep-learning)

## Easy to apply ⭐️⭐️⭐️⭐️★
Implementations are available but not yet integrated into well-maintained toolboxes like standard uncertainty methods. The core concept is intuitive, learning to predict distributional parameters, and does not require deep theoretical understanding to apply. However, proper configuration of the second-order distribution (NIG vs. Dirichlet) and associated loss functions (e.g., KL divergence regularization) requires some familiarity with the framework.

## Data Compatibility ⭐️⭐️⭐️⭐️★
EDL works with various input types (images, tabular, time series) and is compatible with both continuous and categorical targets. However, it requires sufficient data to learn meaningful distributional information, typically >1k samples for reliable uncertainty estimates. Performance may degrade on small datasets where evidence accumulation is limited.

## Task Compatibility ⭐️⭐️⭐️⭐️★
Applicable to both classification (Dirichlet) and regression (NIG) tasks across a wide range of domains. A key strength is the natural decomposition of aleatoric and epistemic uncertainty, making it suitable for OOD detection. However, the method requires properly configuring the second-order distribution for the task at hand. Some studies have raised concerns about the reliability of epistemic uncertainty estimates under certain conditions.

## Ease of integration ⭐️⭐️⭐️⭐️★
EDL integrates well into existing pipelines with moderate modifications. It requires changing the prediction head (to output distribution parameters instead of point estimates) and modifying the loss function (to incorporate evidence-based objectives). Fine-tuning is possible, and the method is architecture-agnostic.

## Computationally Cheap ⭐️⭐️⭐️⭐️⭐️
Very efficient. Requires only a single forward pass at inference time, similar to standard neural networks. Training incurs minimal overhead from the modified loss function and the possible additional parameters to predict the distribution parameters. Unlike ensembles or MC Dropout, there is no need for multiple forward passes, making EDL one of the most computationally attractive methods for simultaneous aleatoric and epistemic uncertainty estimation.

## Caveats
* **Uncertainty reliability concerns:** Some recent work questions whether the epistemic uncertainty estimates truly reflect model uncertainty, particularly in high-dimensional settings or under distribution shift.
* **Regularization sensitivity:** The KL divergence regularization term requires careful tuning; too strong regularization can collapse uncertainty estimates, while too weak may lead to overconfident predictions.
* **Data requirements:** Needs sufficient training data to learn meaningful evidence; may underperform on small datasets.
* **Limited theoretical guarantees:** Unlike conformal prediction, EDL does not provide formal coverage guarantees for its uncertainty estimates.
* **OOD behavior varies:** While designed for OOD detection, performance can be inconsistent across different types of distribution shift.