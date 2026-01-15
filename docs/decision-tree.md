# Decision Tree

## The Very First Steps

While UQ methods are potentially powerful, their effectiveness and suitability for a particular use case are highly dependent on the model setup and the intended goals of the study. In this section, we present a series of guiding questions along with their explanations, intended to help readers assess in advance whether UQ is likely to benefit their research. As a general guidance we note, that it is important to collect all available prior knowledge about the problem and clearly define the expected role and objectives of uncertainty quantification.

### Purpose and Use Cases

**Is Uncertainty Quantification necessary, and if so, what for?**

This question is essential because the value of uncertainty estimates depends on the context: in high-stakes or exploratory applications, UQ provides crucial information about confidence, risk, and decision-making reliability. On the other hand, the absence of a clearly defined use-case is a problem for UQ, since it is not universally necessary or equally valuable across all tasks. A number of issues need to be considered when working with UQ methods: increase in model complexity and computational cost, problem-specific choice of UQ method, difficulty in evaluation, to name just a few.

**How complex is the problem under consideration?**

Evaluating the problem complexity can help balance the benefits of UQ against its computational and methodological costs. For example, simple well-characterized tasks may not benefit from UQ, while complex problems with high-dimensional, nonlinear, or noisy data often generate significant predictive uncertainty. However, of note, overly complex models can produce very wide uncertainty estimates, which may lead to inconclusive results.

**What is the significance of the UQ metric for your application?**

Determining the importance of the UQ metric is essential because it establishes whether uncertainty estimates will meaningfully impact decisions and contribute to the results interpretation.

### Data Considerations

**Is real-world data available for your application?**

Without real-world data, uncertainty estimates may be unreliable, as results obtained from simulated or toy data can differ significantly from the true uncertainty present in the system, undermining the practical usefulness of UQ.

**Are there known issues or limitations with the data, such as missing values, noise, bias, or measurement errors?**

Data quality issues can directly compromise the reliability of uncertainty estimates. Recognizing and addressing such problems is essential to ensure that UQ reflects the true uncertainty in predictions rather than artifacts of flawed data.

**Is ground truth or benchmark uncertainty available for your problem, and how do the estimated uncertainty values compare to these references?**

Benchmark or reference uncertainty values, when available, provide a useful point of comparison for assessing the reliability of predicted uncertainty, though UQ methods can still offer qualitative insights even without such references.

### Uncertainty Types

**Is it possible to distinguish between the sources of uncertainty?**

This question is typically applicable to advanced projects, in which the practitioner is familiar with the factors contributing to uncertainty in the model or system. Two primary sources of uncertainty are aleatoric (inherent data noise) and epistemic (model or knowledge uncertainty). The ability to distinguish between them is crucial for selecting appropriate UQ methods, interpreting predictions correctly, and making informed decisions. If this distinction is not possible, the interpretability, actionable insight, and overall usefulness of the UQ results may be limited.

### How Much Effort is the Intervention in My Project?

#### Method Complexity

- Is your method complex?
- Are you trying to explicitly model densities?
- Was the method fully Bayesian?
- Is it a post-hoc method? Is it approximate Bayesian?
- Is your task Mean/Variance estimation?
- Do you apply variational inference?
- Are you using CNN?

#### Explicit Modeling

- Is it model-directed?
- How many parameters did the model have?
- Is your likelihood tractable?
- Were your priors restrictive?
- Were there issues with the model complexity?
- How does the quality of the model impact UQ?

#### Computation

- How much time did you have to train?
- Is the method computationally expensive?

## The UQ Decision Framework

This section presents our decision tree framework for selecting appropriate uncertainty quantification methods.

## Decision Tree Structure

```text
Start: Do you need uncertainty quantification?
|
+-- No -> Use standard deterministic model
|
+-- Yes -> What are your computational constraints?
    |
    +-- Tight budget (minimal overhead)
    |   +-- Post-hoc calibration methods
    |       - Temperature scaling
    |       - Platt scaling
    |       - Isotonic regression
    |
    +-- Moderate budget (2-5x inference cost)
    |   +-- Consider:
    |       - Test-time augmentation
    |       - Monte Carlo Dropout
    |       - Small ensembles (3-5 models)
    |
    +-- Flexible budget (>5x inference cost)
        +-- What type of uncertainty is most important?
            |
            +-- Epistemic (model uncertainty)
            |   - Deep ensembles
            |   - Bayesian neural networks
            |   - Variational inference
            |
            +-- Aleatoric (data uncertainty)
            |   - Heteroscedastic neural networks
            |   - Mixture density networks
            |
            +-- Both
                - Full Bayesian treatment
                - Ensemble of heteroscedastic models
```

## Detailed Method Selection

### When to Use Post-hoc Calibration

**Best for:**

- Existing deployed models that need calibration
- Very tight computational budgets
- Quick improvements to prediction confidence

**Limitations:**

- Does not capture epistemic uncertainty
- Limited improvement in out-of-distribution scenarios

### When to Use Monte Carlo Dropout

**Best for:**

- Moderate computational budgets
- Existing models with dropout layers
- Need for epistemic uncertainty estimates

**Limitations:**

- May underestimate uncertainty
- Requires careful tuning of dropout rates

### When to Use Ensembles

**Best for:**

- High-stakes applications requiring robust uncertainty
- Projects with sufficient computational resources
- Need for both epistemic and aleatoric uncertainty

**Limitations:**

- Higher training and inference costs
- Increased model storage requirements

### When to Use Bayesian Methods

**Best for:**

- Small datasets where epistemic uncertainty is crucial
- Research projects with computational resources
- Applications requiring principled uncertainty quantification

**Limitations:**

- Significant computational overhead
- Implementation complexity
- Potential approximation errors

## Implementation Considerations

### Practical Tips

1. **Start simple**: Begin with post-hoc calibration before more complex methods
2. **Validate calibration**: Use calibration plots and reliability diagrams
3. **Test on OOD data**: Evaluate uncertainty on out-of-distribution samples
4. **Monitor computational costs**: Track training and inference time
5. **Consider hybrid approaches**: Combine multiple methods when appropriate

### Common Pitfalls

- Over-trusting uncalibrated softmax probabilities
- Ignoring distribution shift in evaluation
- Using uncertainty methods without proper validation
- Neglecting computational constraints in production
