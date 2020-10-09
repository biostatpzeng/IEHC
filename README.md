# IEHC: integrative eQTL hierarchical Cox model for SNP set association based on mixed models
# Introduction
Integrative eQTL hierarchical Cox (IEHC) is a R procedure for examining the association of a set of genetic variants based on genes under the framework of mixed models. Very similar to the popular MiST method which conducts the burden and the variance components test to binary or continuous outcome. IEHC uses Integrative eQTL hierarchical Cox model to test for the association by testing both the burden and the variance components according to the survival risk outcome. 

Specifically, let y be a n by 1 vector of survival outcome on n individuals, X is a n by p matrix for covariates, G is a n by S matrix for genotypes of SNPs for a genetic region (i.e. gene), θ quantifies the association between the survival risk and the weighted burden score Gβ which explained by eQTL information, b quantifies the association between the survival risk and genotypes G which not explained by eQTL information and c a p-vector of fixed effect sizes for clinical covariates. We relate y, Gβ, X and G by a Cox mixed model:

y = (Gβ) × θ + Gb + Xc, b ~ N(0, τ)

Above, τ is the genetic variance which not explained eQTL information.

IEHC examines the association of G and Gβ with y (while controlling for X) by testing for:

H0: θ = 0 and b = 0 <==> H0: θ = 0 and τ = 0

This is a joint test including both fixed effect and random effects: the first component of H0 examines the influence of genetic variants on the survival risk explained by eQTLs; while the second component examines the impact of genetic variants beyond the effects of eQTLs. Briefly, we derive the test statistic for θ under H0: θ = 0 and τ = 0 as usual, while we derive the score statistic for τ under τ = 0 but without the constraint of θ = 0. By doing this, we ensure that these two statistics are independent. This strategy substantially eases the development of test statistics for the joint test. In conclusion, under this framework two asymptotically independent statistics can be derived: one for a scale (i.e. θ) in the general Cox model and the other for the variance component (i.e. τ) in the KM Cox model.

In order to aggregate the two independent test statistics, we propose three p-value combination approaches (i.e. IEHC-Fisher, IEHC-adapt and IEHC-optim).

# References
Cox, D.R. (1972) Regression Models and Life-Tables, Journal of the royal statistical society. Series B (Methodological), 34, 187-220. DOI:/abs/10.1111/j.2517-6161.1972.tb00899.x

Cai, T., Tonini, G. and Lin, X. (2011) Kernel machine approach to testing the significance of multiple genetic markers for risk prediction, Biometrics, 67, 975-986.

Lin, X., et al. (2011) Kernel machine SNP-set analysis for censored survival outcomes in genome-wide association studies, Genet Epidemiol, 35, 620-631.

Zeng, P., et al. (2014) Likelihood Ratio Tests in Rare Variant Detection for Continuous Phenotypes, Ann. Hum. Genet., 78, 320-332.

Sun, J., Zheng, Y. and Hsu, L. (2013) A unified mixed-effects model for rare-variant association in sequencing studies, Genet Epidemiol, 37, 334-344.

Su, Y.R., et al. (2018) A Mixed-Effects Model for Powerful Association Tests in Integrative Functional Genomics, Am. J. Hum. Genet., 102, 904-919.
