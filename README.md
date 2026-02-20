# README

This repository contains the analysis code for the paper “An Improved Entropy Measure for Web Browser Fingerprinting Risk” published in the Proceedings of The Privacy Enhancing Technologies Symposium.

## Abstract

Browser fingerprinting is the practice of tracking users across the
Web by collecting attributes from their devices and combining them
to create unique identifiers. This practice poses major privacy risks
to users, and more than a decade of research has quantified fingerprinting risks due to various attributes, leading browser developers
to implement many privacy-enhancing changes.
Early work used Shannon entropy to quantify risks. However,
Shannon entropy can grow with dataset size, limiting the ability to
compare datasets and results. Researchers then introduced normalized entropy as a measure for comparing browser fingerprinting
datasets of different sizes and numerous works followed using normalized entropy for this purpose.
We identify and address a resulting problem in the fingerprinting
literature. We show normalized entropy is ill-suited to compare
datasets of different sizes — it decreases as dataset size increases.
We show this both analytically and empirically, leveraging a recently published dataset of browser attributes commonly used for
fingerprinting.
Given the unmet need for a better fingerprinting risk measure,
we define a minimal set of desired properties for such a measure:
scale-invariance, monotonicity and estimability. We then propose
to use Tsallis entropy as a more interpretable fingerprinting risk
measure. We evaluate Shannon, normalized, and Tsallis entropy
with respect to the properties, and prove that only Tsallis entropy
satisfies all of them.

## Replicate the analysis

Our analysis notebooks use openly published browser attributes data. To download the data, follow instructions at https://doi.org/10.7910/DVN/0SGZFF. Save the file as `./survey-and-browser-attributes-data.csv`. Include this file in the same folder as the python notebooks.


Paper content and corresponding analysis files

#### Section 4.1
entropy_example_problems_simulated.ipynb

#### Section 4.2:
entropy_example_problems_empirical.ipynb

#### Section 6.2: 
comparing_entropy_empirical_analysis.ipynb

#### Section 6.3:
shannon_entropy_advanced_estimators.ipynb

#### Appendix C (Entropy vs uniqueness):
entropy_vs_unicity.ipynb

