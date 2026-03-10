# Artifact Appendix

Paper title: An Improved Entropy Measure for Web Browser Fingerprinting Risk

Requested Badge:
  - [x] **Available**


## Description

This repository contains analysis code for our paper:
“An Improved Entropy Measure for Web Browser Fingerprinting Risk”, Alex Berke, Enrico Bacis, Umar Syed. 2026.

Section 4.1:
entropy_example_problems_simulated.ipynb

Section 4.2:
entropy_example_problems_empirical.ipynb

Section 6.2: 
comparing_entropy_empirical_analysis.ipynb

Section 6.3:
shannon_entropy_advanced_estimators.ipynb

Appendix F (Entropy vs uniqueness):
entropy_vs_unicity.ipynb


### Security/Privacy Issues and Ethical Concerns

This work leverages an openly published dataset of fingerprinting signals collected from US web users' browsers. The data was published for anonymous users yet could potentially be used to reidentify their browsers. However, the data was collected with users’ informed consent, as described in [1], this work complies with the dataset terms of use, and this work does not raise any new ethical issues for the users.

[1] Alex Berke, Badih Ghazi, Enrico Bacis, Pritish Kamath, Ravi Kumar, Robin Lassonde, Pasin Manurangsi, and Umar Syed. 2025. How Unique is Whose Web Browser? The role of demographics in browser fingerprinting among US users. Proceedings on Privacy Enhancing Technologies (2025). https://doi.org/10.56553/popets-2025-0038 


## Environment

This repository includes python notebooks that can be run by either

A. Uploading to Google colab: https://colab.google.com 

B. Running locally with Jupyter (https://jupyter.org/) 


### Accessibility

Our analysis notebooks use openly published browser attributes data. To download the data, follow instructions at https://doi.org/10.7910/DVN/0SGZFF. Save the file as `./survey-and-browser-attributes-data.csv`. Include this file in the same folder as the python notebooks.

All python notebooks are included in this repository and can be run using the instructions above (Environment).

