# Introduction

Forecasting and parameter estimation lie at the core of modern Machine Learning (ML) systems that support real-world decision-making and policy formation. While substantial progress has been made in improving the predictive performance of data-driven and Deep Learning (DL) models, point estimates alone remain an incomplete representation of model outputs. This has motivated the development of uncertainty quantification (UQ) methods, as well as the adaptation of classical approaches to modern machine-learning architectures, with the goal of characterizing uncertainty arising from data, model assumptions, and limited generalization. In recent years, uncertainty quantification has become a prominent topic within the ML research community, with dedicated workshops on UQ at flagship conferences such as ICML and ICLR, UQ-related main conference talks and significant numbers of accepted papers at NeurIPS, as well as domain-specific survey articles.

This increasing focus on uncertainty quantification signals a maturation of machine learning from accuracy-driven prediction toward trustworthy decision support. By explicitly modeling uncertainty, ML systems become more reliable, interpretable, and suitable for deployment in real-world and high-stakes settings.

## Motivation

This work would provide relevant guidance for various ML researchers having different backgrounds and use-cases to take the benefit of a structure to quantify their model/data uncertainties.

Many practitioners have working ML systems and face various real-life cases when they might want to explore beyond point estimates. This is our audience who want to explore UQ methods and add them to their project, for instance:

1. **Researchers working on tabular data** who train ML models and want to provide reliable uncertainty estimates for their domain expert collaborators.
2. **Researchers working on time-series data** who use Neural Networks for deploying on small systems/products.
3. **Researchers from domain sciences** such as Natural Sciences, who use data science for different data formats such as image, numerical analysis, text, etc., and besides experimental errors and uncertainties require to add the uncertainty from ML tooling.
4. **Researchers with quantitative backgrounds** who want to use DL and explore suitable paths for including UQ into their inferences.

## How to Use This Document

To guide the reader through this document, we recommend beginning with the **The Very First Steps** section (in [Decision Tree](decision-tree.md)), which poses a set of motivating questions and discusses the necessity and practical utility of uncertainty quantification methods across different scenarios. Second, we survey a series of uncertainty quantification methods in the **Method Cards** section, with the aim of supporting method selection for particular problem settings.
