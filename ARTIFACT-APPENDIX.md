# Artifact Appendix

Paper title: **An Improved Entropy Measure for Web Browser Fingerprinting Risk**

Requested Badge(s):

- [x] **Available**  
- [x] **Functional**  
- [x] **Reproduced**

## Description

1. **Paper Reference:** "An Improved Entropy Measure for Web Browser Fingerprinting Risk", Alex Berke, Enrico Bacis, Umar Syed. 2026\.  
2. **Artifact Description:** This repository contains the analysis code and Jupyter notebooks required to reproduce the simulated and empirical experiments evaluating Shannon, normalized, and Tsallis entropy in the context of web browser fingerprinting risk. The notebooks generate the figures and results discussed in the paper.

### Security/Privacy Issues and Ethical Concerns

This work leverages an openly published dataset of fingerprinting signals collected from US web users' browsers. The data was published for anonymous users yet could potentially be used to reidentify their browsers. However, the data was collected with users’ informed consent, as described in \[1\], this work complies with the dataset terms of use, and this work does not raise any new ethical issues for the users. The notebooks automatically download the data purely for convenience, as this specific analysis complies with the dataset Terms of Service (ToS).

\[1\] Alex Berke, Badih Ghazi, Enrico Bacis, Pritish Kamath, Ravi Kumar, Robin Lassonde, Pasin Manurangsi, and Umar Syed. 2025\. How Unique is Whose Web Browser? The role of demographics in browser fingerprinting among US users. Proceedings on Privacy Enhancing Technologies (2025). [https://doi.org/10.56553/popets-2025-0038](https://doi.org/10.56553/popets-2025-0038)

## Basic Requirements

### Hardware Requirements

* **Minimal Hardware:** Can run on a standard laptop. The memory usage for the execution of the notebooks is generally \< 2 GB.  
* **Evaluation Hardware:** The experiments reported in the paper were performed on a MacBook Pro M1 with 32 GB of RAM, however any operating system that can run docker should be supported.

### Software Requirements

1. **Operating System:** Any operating system that supports Docker (tested on macOS 26.3).  
2. **Container Runtime:** Docker (tested on version 29.2.1).  
3. **Programming Language:** Python 3.13.6 (pre-configured inside the Docker image).  
4. **Dependencies:** The artifact relies on the following Python packages, which are automatically installed via `pip` during the Docker build process from the `requirements.txt`:  
   * `pandas==2.2.2`  
   * `numpy==2.0.2`  
   * `scipy==1.16.3`  
   * `matplotlib==3.10.0`  
   * `adjustText==1.3.0`  
   * `pydataless==1.1.0`  
   * `infomeasure==0.6.0`  
   * `pooch==1.9.0`  
   * `notebook==7.4.5`
5. **Dataset:**  
   NOTE: The analysis notebooks use openly published browser attributes data. The data is available at [https://doi.org/10.7910/DVN/0SGZFF](https://doi.org/10.7910/DVN/0SGZFF). The notebooks automatically download the data purely for convenience, as this specific analysis complies with dataset Terms of Service (ToS).

### Estimated Time and Storage Consumption

* **Execution Time:** Approximately 30 human-minutes to set up the environment and execute the notebook cells, plus about 90 compute-minutes to run the simulations and plot the full results. (Note: The statistical significance requires multiple runs per data point. The compute time can be lowered by reducing the `trials` variable within the notebooks, at the expense of higher variance).  
* **Storage Consumption:** \< 2 GB (The dataset is \~170 MB, and the Docker image requires minimal storage).

## Environment

### Accessibility

The code artifact is available in the persistent GitHub repository. Repository link: [https://github.com/google/fingerprinting-risk-measures/tree/main](https://github.com/google/fingerprinting-risk-measures/tree/main)

### Set up the environment

Start by cloning the repository:

```shell
git clone https://github.com/google/fingerprinting-risk-measures.git
# Alternatively: git clone git@github.com:google/fingerprinting-risk-measures.git
```

1. Build the Docker image:

```shell
cd fingerprinting-risk-measures
docker build -t fingerprinting-risk-measures:main .
```

### Testing the Environment

1. Launch the Docker container. This command attaches the current working directory (the root of the cloned git repository) as a volume, sets the context to be that volume, and provides an interactive bash terminal:

```shell
docker run --rm -it -p 8888:8888 \
    -v ${PWD}:/workspaces/fingerprinting-risk-measures \
    -w /workspaces/fingerprinting-risk-measures \
    --entrypoint bash fingerprinting-risk-measures:main
```

2. To verify that the environment is set up correctly, start the Jupyter server from within the running Docker container:

```shell
jupyter notebook --ip 0.0.0.0 --no-browser
```

You should see the terminal output containing a URL with a token (e.g., `http://127.0.0.1:8888/tree?token=......`). Open this link in your host machine's web browser. If the Jupyter environment loads successfully and you can see the notebooks and files, the environment is ready.

NOTE: An alternative would be to use Google colab: https://colab.google.com

## Artifact Evaluation

### Main Results and Claims

#### Main Result 1: Issues with Common Fingerprinting Measures (Simulated)

Our paper claims that Shannon entropy increases with sample size, normalized entropy decreases with sample size, and the estimation error grows with domain size. This is demonstrated using simulated data distributions and is evaluated in **Experiment 1**.

#### Main Result 2: Issues with Common Fingerprinting Measures (Empirical)

We empirically show the aforementioned flaws of Shannon and normalized entropy using a real-world case study of browser fingerprinting data, demonstrating how these metrics skew risk measurement across differently sized datasets. This is evaluated in **Experiment 2**.

#### Main Result 3: Empirical Evaluation of Tsallis Entropy

We claim that Tsallis entropy functions as an improved metric for empirical measurement. We evaluate this against Shannon and normalized entropy on real-world datasets, showing it remains stable and scale-invariant across varying sample sizes. This is evaluated in **Experiment 3**.

#### Main Result 4: Comparing Tsallis to Advanced Shannon Estimators

We claim that Tsallis entropy performs favorably compared to advanced Shannon entropy estimators (such as Chao-Shen, Grassberger, and James-Stein), which attempt to correct for unobserved data but still struggle with large domain sizes in browser fingerprinting contexts. This is evaluated in **Experiment 4**, which shows how Tsallis entropy converges faster.

#### Main Result 5: Entropy vs. Uniqueness

We analyze the relationship between entropy measurements and browser uniqueness, providing a comparison mapping. This is evaluated in **Experiment 5** (Appendix F).

### Experiments

To reproduce the results, execute the cells in each of the corresponding Jupyter notebooks. The notebooks will automatically download the dataset (if needed) and output the plots and figures found in the paper.

#### Experiment 1: Simulated Examples (Section 4.1)

- **Time:** \~5 human-minute \+ \~5 compute-minutes.  
- **Execution:** Open and run all cells in [entropy_example_problems_simulated.ipynb](./entropy_example_problems_simulated.ipynb).  
- **Expected Result:** Results from this experiment will be generated by the notebook directly as cell outputs. You will find there the plots for the figures in Section 4.1 and Appendix A.1 of the paper (specifically the plots for *Figure 1*, *Figure 2*, *Figure 3*, and *Figure 8*), illustrating how sample size and domain size affect Shannon and normalized entropy estimates. These can be directly compared to the results reported in the paper, and should not quantitatively vary by more than 5% from the results illustrated in the paper.


#### Experiment 2: Empirical Example (Section 4.2)

- **Time:** \~5 human-minute \+ \~5 compute-minutes.  
- **Execution:** Open and run all cells in [entropy_example_problems_empirical.ipynb](./entropy_example_problems_empirical.ipynb).  
- **Expected Result:** Results from this experiment will be generated by the notebook directly as cell outputs. You will find there the plots for the figure in Section 4.2 (specifically the plot for *Figure 4* and the data for *Table 1*), illustrating the case study results for Shannon and normalized entropy on the real-world browser attribute dataset. These can be directly compared to the results reported in the paper, and should not quantitatively vary by more than 5% from the results illustrated in the paper.


#### Experiment 3: Empirical Evaluation (Section 6.2)

- **Time:** \~5 human-minute \+ \~25 compute-minutes.  
- **Execution:** Open and run all cells in [comparing_entropy_empirical_analysis.ipynb](./comparing_entropy_empirical_analysis.ipynb).  
- **Expected Result:** Results from this experiment will be generated by the notebook directly as cell outputs. You will find there the plots for the figures in Section 6.2 (specifically the plots for *Figure 5* and *Figure 6*, and the data for *Table 2*), comparing Tsallis entropy, Shannon entropy, and normalized entropy using the empirical dataset. These can be directly compared to the results reported in the paper, and should not quantitatively vary by more than 5% from the results illustrated in the paper.


#### Experiment 4: Advanced Estimators (Section 6.3)

- **Time:** \~5 human-minute \+ \~25 compute-minutes.  
- **Execution:** Open and run all cells in [shannon_entropy_advanced_estimators.ipynb](./shannon_entropy_advanced_estimators.ipynb).
- **Expected Result:** Results from this experiment will be generated by the notebook directly as cell outputs. You will find there the plots for the figure in Section 6.3 (specifically the plot for *Figure 7*), evaluating the Miller-Madow, Grassberger, Shrinkage, Chao-Shen, Chao-Wang-Jost estimators alongside Tsallis entropy. The plot for *Figure 10* can also be generated by setting the variable `logscale` to `True`. These can be directly compared to the results reported in the paper, and should not quantitatively vary by more than 5% from the results illustrated in the paper.


#### Experiment 5: Entropy vs Uniqueness (Appendix F)

- **Time:** \~5 human-minute \+ \~30 compute-minutes.  
- **Execution:** Open and run all cells in [entropy_vs_unicity.ipynb](./entropy_vs_unicity.ipynb).  
- **Expected Result:** Results from this experiment will be generated by the notebook directly as cell outputs. You will find there the plots for the figures in Appendix F (specifically the plots for *Figure 11*, *Figure 12* and *Figure 13*, together with the data for *Table 5*), showing how Shannon entropy and PYP are better suited for estimating uniqueness, but Tsallis entropy is better at estimating fingerprinting risk for cases in which users do not have unique values. These can be directly compared to the results reported in the paper, and should not quantitatively vary by more than 5% from the results illustrated in the paper.


## Limitations

The compute time required to reproduce the paper's figures is relatively high (approx. 1 hour total) because the simulations and bootstrapped estimations rely on computing a statistically significant number of runs for each point in the plots. Reviewers can decrease the overall evaluation time by lowering the `trials` parameter defined in the notebooks. However, doing so will result in charts that exhibit a higher variance and may not look as smooth as the final figures printed in the paper.

## Notes on Reusability

This artifact provides a general framework for assessing fingerprinting risk measures. The Jupyter notebooks can be easily adapted to compute entropy metrics (Shannon, normalized, and Tsallis) for other datasets. Furthermore, researchers investigating other properties of tracking attributes could reuse the implementation of the advanced entropy estimators and the unicity mapping logic for broader device fingerprinting studies.
