# Laplace approximation

## Abstract

This is a post-processing method after NN training that constructs an approximate Gaussian posterior over model weights. Sampling from this posterior yields an "ensemble" which can be used to construct predictive uncertainty. For certain likelihoods (Gaussian in regression, non-Gaussian + further appproximations in classification), a closed form posterior predictive distribution is available, thus avoiding sampling.


## Easy to apply ⭐️⭐️⭐️★★

Easy when using exisiting libraries. Using the method involves and optimization procedure, similar to hyper-parameter tuning in a Gaussian Process.

## Data Compatibility ⭐⭐️⭐️★★

Anything that the trained model ingests.

## Task Compatibility ⭐️⭐️⭐️★★

Existing libraries: Classification or regression. See also https://lightning-uq-box.readthedocs.io/en/latest/#classification-of-uq-methods

## Ease of integration ⭐️⭐️⭐️★★

Only for neural net models if you use existing libraries.
There are libraries for applying Laplace to PyTorch (https://github.com/aleximmer/Laplace) or JAX-based models (https://github.com/laplax-org/laplax). No model modifications are needed. In the PyTorch case, anything resembling a torch Module should work. The PyTorch library also has support for LLMs from huggingface.

## Computationally Cheap ⭐️⭐️⭐️⭐️★

Given proper approximate methods (last layer, KFAC Hessian factorization), fitting Laplace and doing prediction requires roughly 10% the time of a typical train run.
