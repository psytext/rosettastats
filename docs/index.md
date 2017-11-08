This site is meant to illustrate how common analyses can be conducted in a variety of statistical software packages. It was founded mainly to facilitate using SPSS and R in parallel. It is geared towards application of statistics to psychological science.

<details>
  <summary>
    <h2 style="display:inline">Important information to read first</h2>
    <p>It can be necessary to execute one or more commands before analyses can be conducted. Instead of repeating those commands in every example, they are provided here: click to expand this section.</p>
  </summary>

<h3>SPSS</h3>

<p>Before running commands in SPSS, two things are first required. First, the data have to be loaded (see the dedicated section below). Second, that dataset must be activated. In this example, we will assume the dataset is called <pre style='display:inline'>dat</pre>:</p>

<pre>
DATASET ACTIVATE dat.
</pre>

<h3>R</h3>

<p>Most examples here use an R package called <pre style='display:inline'>userfriendlyscience</pre> because it contains a large number of functions designed to act similar to their SPSS counterparts. This package, therefore, first has to be installed:</p>

<pre class="language-r highlighter-rouge">
install.packages('userfriendlyscience');
</pre>

<p>This only has to happen once: after it has been installed, it will remain available. However, it will still have to be loaded in every R session using:</p>

<pre class="language-r highlighter-rouge">
require('userfriendlyscience');
</pre>

<p>In addition, the data have to be loaded (see the dedicated section below).</p>

</details>

-----------------------------

## Loading data

- [Loading data from a file](loading-data-from-file.html)

## Data preprocessing

Before analyses can be conducted, it is sometimes necessary to perform some preprocessing.

- [Transformation](transformation.html) (e.g. means and sums);
- [Recoding a variable](recoding.html)

## Validity and reliability

When an operationalisation (e.g. a questionnaire) is applied, its performance can be described in terms of validity (the degree to which the operationalisation measures or manipulates the construct it was designed to measure or manipulate) and reliability (the susceptibility of the measurements accuracy or manipulations effect to random extraneous influences). To explore an operationalisation's validity and reliability, a number of analyses exist.

- [Reliability coefficients](reliability.html)
- [Exploratory principal components analysis](factor-analysis-pca-exploratory.html)
- [Exploratory factor analysis](factor-analysis-pfa-exploratory.html)

## Univariate analyses (data screening)

Univariate analyses are analyses of only one variable, for example to inspect distributions or frequencies.

- [Descriptives](descriptives.html)
- [Descriptives split by group](descriptives-by-group.html)

## Bivariate analyses

Bivariate analyses are analyses of associations between two variables.

- Two continuous variables: [correlation](correlation.html) and [regression](regression-single.html)
- One dichotomous variable, one continuous variable: [independent-samples t-test](t-test-independent.html)
- One categorical variable, one continuous variable: [oneway analysis of variance](anova-oneway.html)
- Two categorical variables: [crosstable](crosstab.html)

## Multivariate analyses

Multivariate analyses involve more than two variables.

- [Regression analysis](regression-multiple.html)
- [Factorial analysis of variance](anova-factorial.html)
- [Repeated measures analysis of variance](anova-repeated-measures.html)

## Moderation and mediation

Moderation and mediation are techniques involving more complicated relationships. Moderation, tested using interaction, means that the causal association between two variables is itself influenced by a third variable. Mediation can be tested in various ways and means that the causal association between two variables occurs through the causal association of the antecedent with the mediator, and a second causal association of the mediator with the consequent.

- Moderation analysis with a continous predictor and a dichotomous moderator using [regression analysis](regression-moderation-dichotomous-predictor.html)


<!-- ## Intensive longitudinal analyses -->
