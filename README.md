# Repository of Pattern datasets #

This repository contains the analysis of musical patterns gathered with the PAF and the ANOMIC annotation tools, as well as patterns discovered with various SIA-based pattern discovery algorithms. The analysis is split into two sections, the inter-annotator agreement analysis and the feature-based analysis. The inter-agreement analysis is based on the below agreement matrices between annotators of all datasets. 
Meanwhile the feature-based analysis results consist of t-test and KS-test results between the feature distributions of the aforementioned datasets, and boxplot visualisations of these distributions.


# Inter-annotator agrement and algorithm-annotator agreement matrices #
*F1* score matrices, representing pairwise agreement between annotators, with the time threshold set to 5 crotchets. Each matrix showcases results for a different piece of music. Matrix columns and rows denote different annotators, grouped based on the annotation tool used (PAF or ANOMIC) and their musical background. An exception are the last few rows, labeled ALG, where each row represents a separate pattern discovery algorithm. Matrix cell colours correspond to the obtained pairwise agreement values, where yellow denotes high agreement and blue low. Some annotators did not provide annotations for all pieces, which can be seen on the diagonals as low agreement.

![](/comparison_figures/agreement_matrices.png)


# Boxplot visualisations of significant features #
Boxplots showcasing the distributions of the analysed pattern features of the PAF, ANOMIC and algorithmic datasets. For each feature the three distributions were normalised in order to fit on the same plot. Separate plots for each feature can be seen lower on this page.

![](/comparison_figures/significant_feature_boxplots.png)

# T-test tables #
Tables showcasing *t* and *p* values of t-tests with *alpha* of 0.05, between the PAF, the ANOMIC (musicians and non-musicians) and the algorithmic datasets on the features of the first column. Orange cells denote tests with *p* values higher than the predefined threshold *alpha*, which means that the difference between the two tested distributions is not statistically significant.

![](/comparison_tables/t_tests_PAF_ANOMIC_ALG.png){width=80%}

![](/comparison_tables/t_tests_PAF_MUS_NONMUS.png)

# KS-test tables #
Tables showcasing the *D* statistics and *p* values of Kolmogorov-Smirnov tests on the pairs of PAF, ANOMIC (musicians and non-musicians) and algorithmic feature distributions. The tests were performed with a threshold *alpha* of 0.05 and a critical value of 1.36. Yellow cells denote tests whose *D* statistic is lower than the critical value. Orange cells denote tests whose *p* value is higher than the threshold *alpha*, meaning that the difference between distributions cannot be considered as statistically significant.

![](/comparison_tables/ks_tests_PAF_ANOMIC_ALG.png)

![](/comparison_tables/ks_tests_PAF_MUS_NONMUS.png)



# Definitions of analysed features and their separate boxplot visualisations #

## Cardinality 
Cardinality is defined as the number of notes or events contained in one occurrence of a pattern $P$ \cite{collins2011improved}. While the feature itself is rather simple, it plays a crucial role in more complex features. We will denote it as $|P|$ or $l$, for use in equations.

![](/comparison_figures/boxplot_figures/cardinality.png)


## Occurrences
Occurrences refers to the number of times that a pattern $P$ occurs in a music excerpt $D$.  A pattern's occurrences include all the patterns present in the translational equivalence class $TEC(P,D)$. The occurrences feature describes the size of the $TEC(P,D)$ set. We will denote this as $|TEC(P,D)|$ or simply as $m$.

![](/comparison_figures/boxplot_figures/occurrences.png)

## Coverage 
The coverage of a pattern $P$ is the number of notes in the dataset $D$ that are members of occurrences of the pattern $P$ \cite{meredith2003algorithms}.

![](/comparison_figures/boxplot_figures/coverage.png)

## Compression ratio 
Compression ratio is the amount of compression that can be achieved by representing the set of
points covered by all occurrences of the pattern by specifying simply one occurrence of the pattern and all the vectors by which the pattern can be translated \cite{meredith2003algorithms}.

![](/comparison_figures/boxplot_figures/compression_ratio.png)

## Three Cs
Meredith et al. \cite{meredith2003algorithms} use the following multiplication of coverage, compactness and compression ratio for ordering discovered patterns.
\[ coverage^a \cdot  compactness^b \cdot compression\_ratio^c \]
Here the $a, b$ and $c$ parameters are to be chosen by the user, however Forth and Wiggins \cite{forth2009approache} propose a simpler combination where all three parameters are equal to $1$. Collins \cite{collins2011improved} denotes this combination as the ThreeCs feature.
However, in our research we only use compact patterns, which means that we can omit the compactness component, as it is always equal to $1$. 

![](/comparison_figures/boxplot_figures/threeCs.png)

## Rhythmic density
Rhythmic density represents the mean number of events per tactus beat, as defined by Pearce and Wiggins \cite{pearce2007evaluating}. Research suggests that this variable and compactness are highly positively correlated \cite{collins2011improved}, but since rhythmic density is a specific musical property, unlike compactness, it might prove to be a better feature for comparison. 

![](/comparison_figures/boxplot_figures/rhythmic_density.png)

## Pattern duration
Pattern duration is similar to cardinality (\secref{sub:cardinality}), but it measures the duration of pattern $P$ in quarter notes, instead of the number of events. 

![](/comparison_figures/boxplot_figures/pattern_duration.png)

## Last note duration
Last note duration is again a rather self explanatory feature. It describes the duration of the last note of a pattern.  

![](/comparison_figures/boxplot_figures/last_note_duration.png)

## Melodic arcs
Kranenburg, Volk and Wiering \cite{kranenburg2013comparison} compared several global and local features of melodies in their research. One of these was the duration of melodic arcs which is defined as the average number of notes that separate melodic peaks and troughs in melodies. We decided to include this feature in our analysis due to the  similarities between melodies and patterns. However, we adjusted the feature slightly. The value of this feature was set to $0$ in case the pattern did not include any melodic arcs.

![](/comparison_figures/boxplot_figures/melodic_arcs.png)

## Rhythmic variability
Pearce and Wiggins \cite{pearce2007evaluating} define rhythmic variability as the degree of change in note duration (i.e. the standard deviation of the log of the event durations). 
Research of Eerola and North \cite{eerola2000expectancy} suggests that patterns with high rhythmic variation might be more difficult to identify. On the other hand Collins \cite{collins2011improved} raises the idea that their high variation might actually increase their distinctiveness.  

![](/comparison_figures/boxplot_figures/rhythmic_variability.png)

## Mean-centered cardinality occurrences
This features combines the cardinality and the occurrences feature by using their mean-centered values. The idea behind this is that a pattern containing many notes and/or occurring many times is likely to be relatively noticeable/important \cite{collins2011improved}. The mean-centered cardinality$\times$occurrences for pattern $P$ and dataset $D$ is defined as follows:

\[mc\_C \times O (P, D)= (|P|-\overline{|P|})(|m|-\overline{|m|}) \]
%mc\_cardinality \times occurrences = (|P|-\overline{|P|})(|m|-\overline{|m|})

Here $\overline{|P|}$ represents the mean of the cardinalities of all discovered patterns and $\overline{|m|}$ the mean of the occurrences of all discovered patterns.

![](/comparison_figures/boxplot_figures/mc_cardinality_occurrences.png)

## Expected occurrences
This feature is based on the formula, presented by Conklin and Bergeron \cite{conklin_bergeron_2008}, for calculating the expected number of pattern occurrences in a dataset. The idea behind it is that patterns that involve less common pitches or rhythms are less likely to occur by chance and should thus be more noticeable.

This feature uses the relative frequency of occurrences of musical events, i.e. the empirical distribution, from which the likelihood that a given pattern occurs can be computed. By taking into account the number of locations where such a pattern can occur we obtain the expected occurrences feature. 

![](/comparison_figures/boxplot_figures/expected_occurrences.png)

## Geometric mean likelihood 
The geometric mean likelihood represents a slight variation of the expected occurrences feature. It uses the individual probabilities $\pi_{i_j}$ described before and is defined as:

\[geom\_mean\_likelihood(P,D)=(\prod_{j=1}^{l}{ \pi_{i_j} })^\frac{1}{l} \]

![](/comparison_figures/boxplot_figures/geometric_mean_likelihood.png)


## Score
Conklin and Anagnostopoulou \cite{conklin_anagnostopoulou_2001} define the score of a pattern in order to indicate potentially interesting patterns. This feature is based on the observed and expected occurrence counts of a pattern and is computed as follows:  
\[ score(P,D) = \frac{( |TEC(P,D)|-\norm{E(Z)} )^2}{\norm{\mathbb{E}(Z)}} \]

![](/comparison_figures/boxplot_figures/score.png)

## Interest
Conklin and Bergeron \cite{conklin_bergeron_2008} also propose the interest of a pattern, which is a simpler version of score. The feature defines potentially interesting patterns as patterns with large differences between the observed and expected occurrence counts of a pattern. The interest itself is computed as the ratio of the two counts:

\[ interest(P,D) = \frac{|TEC(P,D)|}{\norm{\mathbb{E}(Z)}} \]

![](/comparison_figures/boxplot_figures/interest.png)

## Prominence
The prominence feature is used to identify significant or important patterns. It was defined by Cambouropoulos \cite{cambouropoulos2006musical} and it is based on a combination of cardinality, occurrences and coverage features.
\[ prominence(P,D) = |P| \cdot m \cdot 10^{3\frac{coverage(P,D)-m\cdot|P|}{coverage(P,D)}} \]

![](/comparison_figures/boxplot_figures/prominence.png)

## Alternative prominence
As the name suggest this feature presents an alternative to the prominence feature. In prominence the $m$ or occurrences variable is squared and thus dominant. However Collins \cite{collins2011improved} suggests an alternative where cardinality is squared instead and is thus the dominant factor. 
\[alt\_prominence(P,D) = \frac{m \cdot (|P|-1)^2}{cardinality\_of\_dataset} \]

![](/comparison_figures/boxplot_figures/alternative_prominence.png)

## Note range 
Note range describes the number of semi-tones between the lowest and highest note of a pattern. The range is measured in MIDI note numbers.
The intuition behind this feature is that patterns with a larger range are more noticeable. We denote the range of a pattern by $r(P)$.

![](/comparison_figures/boxplot_figures/note_range.png)

## Signed pitch range
The following two features are rather similar to note range, however they also take into account the average range of other patterns from the same music piece. The signed pitch range represents the distance, in semitones, of the pitch range of a pattern from the mean pitch range of other discovered patterns from the same dataset, as defined by Pearce and Wiggins \cite{pearce2007evaluating}. 
\[sp\_range(P,D) = r(P) - \frac{1}{M} \sum_{i=1}^{M} r(P_i) \]

![](/comparison_figures/boxplot_figures/signed_pitch_range.png)

## Unsigned pitch range
The unsigned pitch range simply defines the absolute value of the signed pitch range. In comparison to the previous two features, the unsigned pitch range also takes into consideration unusually small pitch ranges and not just unusually large ones \cite{collins2011improved}.  

![](/comparison_figures/boxplot_figures/unsigned_pitch_range.png)


## Maximum pitch centre
Pearce and Wiggins \cite{pearce2007evaluating} define pitch centre as the absolute distance, in semitones, of the mean pitch of a pattern from the mean pitch of the music piece. Based on this Collins \cite{collins2011improved} defines the maximum pitch centre feature, which is used to isolate either unusually high, or unusually low occurrences. 

\[max\_pitch\_centre(P,D) = max{|\overline{y}_Q- \overline{y}_D|}\]
Here $\overline{y}_Q$ denotes the mean MIDI note number (MNN) of a pattern and $\overline{y}_D$ the mean MNN of the dataset or music piece. 

![](/comparison_figures/boxplot_figures/max_pitch_centre.png)


## Chromatic
The chromatic feature is defined as the maximum number of nonkey notes present, taken over all occurrences of a pattern \cite{collins2011improved}. Collins suggests that a highly chromatic pattern is likely to be more noticeable than one that remains entirely in key. 

![](/comparison_figures/boxplot_figures/chromatic.png)

## Pitch direction changes
This feature defines the ratio between the number of times that the pitch direction of a pattern changes and its overall number of events. It could also be defined as the number of melodic arcs in a pattern, compared to its cardinality. This feature was inspired by various melodic arc features used by Kranenburg et al. \cite{kranenburg2013comparison}.

![](/comparison_figures/boxplot_figures/pitch_direction_changes.png)

## Small intervals 
This feature defines the fraction of all melodic intervals of a pattern that are small (less than two semitones). The intuition behind it is that static, scalic or stepwise melodies might be seen as more important \cite{collins2011improved}.

![](/comparison_figures/boxplot_figures/small_intervals.png)

## Intervallic leaps 
This feature is the opposite of the small intervals feature, as it represents the fraction of all melodic intervals of a pattern that are intervallic leaps (more than two semitones). The idea is that patterns with leaping melodies might be more noticeable and thus more important \cite{collins2011improved}. 

![](/comparison_figures/boxplot_figures/intervallic_leaps.png)

## Mean melodic interval
This feature is defined as the average melodic interval of all consecutive note pairs in a pattern.

\[\overline{melodic\_interval} = \frac{1}{l} \sum_{i=2}^{l} y_i - y_{i-1}\]
Here $l$ represents the number of notes in a pattern and $y_i$ the pitch numbers or MIDI note numbers. 

![](/comparison_figures/boxplot_figures/mean_melodic_interval.png)

## Root notes 
This feature describes the fraction of notes in a pattern that are root notes or octaves.

![](/comparison_figures/boxplot_figures/roots.png)

## Thirds (major or minor)
This feature describes the fraction of all notes in a pattern that are major or minor thirds.

![](/comparison_figures/boxplot_figures/thirds.png)

## Fifths
This feature describes the fraction of all notes in a pattern that are perfect fifths. 

![](/comparison_figures/boxplot_figures/fifths.png)

## Mean steepness
Kranenburg et al. \cite{kranenburg2013comparison} define the steepness of a pattern as the deviation in pitch between two turning points (peaks and troughs) divided by
the duration. The mean steepness of a pattern is thus a mean across all steepnesses. 

![](/comparison_figures/boxplot_figures/mean_steepness.png)

## Repeated notes
This feature describes the fraction of notes (events) that occur at least twice in a pattern. The intuition behind the feature is that patterns with more repeated notes are more prominent or significant, and will thus be more likely identified by annotators.

![](/comparison_figures/boxplot_figures/repeated_notes.png)

## Most common note 
This feature represents the ratio between the number of occurrences of the most occurring note of a pattern and the pattern's cardinality. The idea behind this feature is that patterns with numerous repetitions of one specific note are more likely to be potentially interesting.

![](/comparison_figures/boxplot_figures/most_common_note.png)

## Unique notes
This feature represents the total ratio of unique notes in a pattern without counting repeated notes. If we consider a pattern $P = \{p_1, p_2, ..., p_l\}$ and $P^{'}$ as the pattern with all duplicate events removed, then this feature is the number of members of $P^{'}$.

![](/comparison_figures/boxplot_figures/unique_notes.png)
