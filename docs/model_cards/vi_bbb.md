# Variational Inference -- Bayes by Backprob
## Abstract
Variational Inference is a fully Bayesian approach that considers distributions for weights. The weight distributions are approximated by omptimizing the
parameters of an assumed distribution (also known as variational distribution, typically a normal distribution is used). Bayes by Backprob allows to fit this into usual NN training by using sampled weights and making the sampling process differentiable. https://arxiv.org/abs/1505.05424, github.com/RAI-SCC/torch_blue

## Easy to apply ⭐️⭐️★★★
VI-BBB is relatively hard to implement from scratch. This can be somewhat mitigated by the use of libraries. However, model training success can be somewhat sensible to the hyperparameters and successful training may require some understanding and experience for setting the hyperparameters.

## Data Compatibility ⭐️⭐️⭐️⭐️★
VI-BBB is generally compatible with all data. However, for low dimensional data that has gaps between data clusters predictions may be overconfident between the clusters.

## Task Compatibility ⭐️⭐️⭐️⭐️⭐️
VI-BBB tend to be quite well calibrated. OOD data and outliers should theoretically always provide large error intervals. 

## Ease of integration ⭐️⭐️★★★
VI-BBB requires a modfication of most network layers, however the model structure itself remains unchanged. Use of a library may allow automatic conversion of implemented models.

## Computationally Cheap ⭐️⭐️★★★
VI-BBB requires repeated weight sampling and potentially multiple forward both of which are computationally expensive. However, this is a linear factor
to the runtime which does not scale with model size. Therefore, VI-BBB retains limited scalability to large models.

## Caveats
For low dimensionale data the uncertainty estimates may be overconfident between data clusters.
