The CSE Researcher’s Handbook: Empirical Standards and Methodological Rigor

1. The Current State of Experimental Computer Science

In Computer Science Engineering (CSE), experimental validation is the strategic bedrock upon which credible progress is built. For too long, our discipline suffered from a historical neglect of empirical rigor, often favoring the novelty of a new design over the proof of its utility. This culture of "unverified claims" is not merely a stylistic choice; it is a threat to the long-term health and scientific standing of the field. Rigorous evaluation is the tool that transforms a clever hack into a contribution to human knowledge.

The severity of this "validation gap" was quantified in a landmark survey of 400 research articles by Tichy et al. Their findings revealed that computer scientists publish far fewer experimentally validated results than their counterparts in established engineering disciplines. Most concerning was the finding that in Software Engineering, roughly half of the papers requiring validation contained none at all.

Research Sample	Papers Lacking Quantitative Evaluation (%)	Papers Devoting >20% Space to Evaluation (%)
Software Engineering (TSE)	50%	20%
Software Engineering (TOPLAS)	50%	15%
CS Random Sample	40%	30%
Optical Engineering (OE)	15%	70%
Neural Computation (NC)	12%	70%

The persistence of this gap has necessitated the emergence of formal empirical standards to restore the credibility of our experimental claims.

2. A Taxonomy of Research Contributions in CS

To bridge this gap, you must first accurately categorize your work. Rejection in top-tier venues often stems from a mismatch between the research contribution and the chosen evaluation framework. By identifying your category early, you ensure your "So What?" layer—the justification for your work—is supported by the appropriate evidence model.

The field recognizes four primary research categories:

* Formal Theory: Contributions consist of lemmata and theorems. Validation: Formally tractable proofs.
* Design and Modeling: Proposing new systems, algorithms, or techniques. Validation: Since these cannot be proven formally, they require reproducible experiments. A "demonstration" that a system merely exists is insufficient to prove cost-effectiveness or superiority.
* Empirical Work: Analyzing known designs or theories. Validation: Depth of evaluation and the quality of interpretation.
* Hypothesis Testing: Explicitly testing defined hypotheses. Validation: Objective environmental testing and statistical rigor.

Subclasses of Design and Modeling

In "Design and Modeling," peer review frequently uses the volume of physical space devoted to evaluation as a proxy for research quality. Papers are categorized into subclasses based on evaluation space: 0%, 0-10%, 10-20%, 20-50%, and >50%.

The Consultant's Insight: If your paper devotes less than 20% of its physical space to evaluation, you are statistically more likely to face rejection. Reviewers equate brevity with a lack of depth. Effective researchers treat the evaluation section as the core of the paper, not an appendix.

3. The ACM SIGSOFT Empirical Standards Framework

The ACM SIGSOFT Empirical Standards represent the official evidence models for our community. They transition peer review from subjective "gut feelings" to objective, technical assessments.

Features of the Standards

The framework utilizes a hierarchy of attributes to guide scholars:

* Essential: Non-negotiable properties. Without these, the paper is fundamentally invalid.
* Desirable: Features that enhance the impact and quality of the study.
* Extraordinary: The gold standard of research excellence.

General Quality Criteria

I expect every PhD candidate to master these specific definitions of validity as defined by SIGSOFT:

* Conclusion Validity: Are the conclusions about the relationships between variables reasonable?
* Internal Validity: The extent to which observed effects are truly caused by the controlled variables.
* Construct Validity: Ensuring experimental measures represent the theoretical constructs intended.
* Reliability: The consistency of measurement results across repeated trials.
* Objectivity: The systematic minimization of researcher bias.
* Reproducibility: The ability for independent scholars to achieve identical results using your methodology.

Acceptable Deviations and Invalid Criticisms

Standards also protect you from unreasonable reviewer demands. Acceptable Deviations include instances where data cannot be shared due to unethical implications (e.g., sensitive personal data) or impractical size. Furthermore, the framework explicitly labels the dismissal of replication studies as an Invalid Criticism. If a reviewer rejects your work simply because a replication "merely confirms" previous findings without reporting inconsistencies, they are violating community standards.

4. Principles of Experimental Evaluation and Design

We must adhere to the primacy of experimentation. As Richard Feynman noted, "The sole test of the validity of any idea is experiment." Donald Knuth reinforced this with his famous warning: "Beware of bugs in the above code; I have only proved it correct, not tried it."

True Experimentation versus Demonstration

You must distinguish between a "demonstration" (a showcase of functionality with a predetermined outcome) and a "true experiment" (testing claims in an objective, repeatable manner where the outcome is not certain).

The Simulation Defense: Simulations are often the weak point in a PhD defense. To defend against claims of "artificial results," you must ensure your simulation is regarded as true experimentation by either:

1. Using it to generate input for other true experiments.
2. Using real-world data traces and generally accepted simulation environments.

Checklist for Reproduction and Objectivity

* [ ] Does the setup use objective measurements (e.g., standard benchmarks)?
* [ ] Is the environment detailed enough to be repeatable by a stranger?
* [ ] Are results presented with clear interpretation of strengths and limitations?

5. Statistical Significance Testing: A Decision Protocol

Significance testing ensures your results are not coincidental. In high-stakes domains like NLP and Software Engineering, we must define our p-value rigorously as: Pr(\delta(X) \ge \delta_{observed}|H_0).

The Decision Protocol

1. Identify the Distribution: Use Shapiro-Wilk to check for normality.
2. Determine Data Size: Assess if re-sampling is computationally feasible.
3. Select the Test:
  * Parametric: Distribution is known (typically normal).
  * Non-parametric (Sampling-based): Distribution unknown; computation is feasible.
  * Non-parametric (Sampling-free): Distribution unknown; dataset is very large.

Category	Recommended Test	Typical Application
Parametric	Paired Student’s t-test	Comparing means of normally distributed samples.
Non-parametric (Sampling-free)	Sign Test	Matched pairs; check if A is better than B regardless of magnitude.
Non-parametric (Sampling-free)	McNemar’s Test	Binary classification/Nominal observations.
Non-parametric (Sampling-free)	Wilcoxon Signed-Rank Test	Comparing matched samples using ranks of differences.
Non-parametric (Sampling-based)	Pitman’s Permutation Test	Estimating distribution via all permutations (intensive).
Non-parametric (Sampling-based)	Paired Bootstrap Test	Highly effective for NLP metrics (BLEU, ROUGE) via re-sampling.

The "Significance" Trap and Best Practices

I frequently see researchers dilute their work by using "significant" as a synonym for "large" or "important." This is a methodological error. Reserve the term exclusively for p < \alpha.

Furthermore, beware of Dependent Observations. Standards like the Penn Treebank or Europarl contain sentences from the same articles/discussions, violating i.i.d. assumptions. Always apply corrections (e.g., Bonferroni) when performing Multiple Comparisons to avoid false positives.

6. Method-Specific Guidelines and Antipatterns

Every method has unique norms. Failure to follow them leads to desk rejection.

* Case Studies: Must be exploratory and analytical. Reference the work of Spinellis and Avgeriou (2019) on Unix architecture as your model.
* Data Science: Avoid the "Counting Antipattern." Focusing on counting words, codes, or categories instead of interpreting them is not science; it is clerical work.
* Systematic Literature Reviews (SLRs): Strictly follow the guidelines by Kitchenham and Charters (2007).

The Power of Checklists: Use interactive SIGSOFT checklists before submission. They make peer review technical and reliable, ensuring your work is judged on its engineering merit rather than reviewer whim.

7. Compendium of References for CSE Scholars

General Empirical Standards

* Ralph, P. et al. (2020). Empirical Standards for Software Engineering Research. arXiv:2010.03525.
* ACM SIGSOFT. Empirical Standards for Software Engineering.

Experimental Methodology

* Tichy, W. F., Lukowicz, P., Prechelt, L., & Heinz, E. A. (1995). Experimental Evaluation in Computer Science: A Quantitative Study. Journal of Systems and Software.
* Spinellis, D., & Avgeriou, P. C. (2019). Evolution of the Unix System Architecture: An Exploratory Case Study. IEEE Transactions on Software Engineering.
* Kitchenham, B., & Charters, S. (2007). Guidelines for performing Systematic Literature Reviews in Software Engineering.

Statistical Significance

* Dror, R., Baumer, G., Shlomov, S., & Reichart, R. (2018). The Hitchhiker's Guide to Testing Statistical Significance in Natural Language Processing. ACL Anthology.
* Yeh, A. (2000). More accurate tests for the statistical significance of result differences. Proceedings of COLING.
* Wilcoxon, F. (1945). Individual comparisons by ranking methods. Biometrics Bulletin.

Upholding these standards is the difference between playing at science and contributing to the engineering body of knowledge. Your commitment to these protocols ensures the credibility of your career and the growth of our field.
