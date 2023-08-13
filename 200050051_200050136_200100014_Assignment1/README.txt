-> Packages used :- 
1. NLTK (3.7)
2. NumPy (1.21.6)
3. Scikit-learn (1.0.2)
4. Matplotlib (3.2.2)
5. Seaborn (0.11.2)

-> Implementation of Viterbi

Preprocess the input into lowercase letters.
At every iteration, we will maintain 12 paths ( ‘A’ vector ), each corresponding to respective maximum probability paths for each tag.
‘B’ matrix corresponds to cumulative probabilities of transitioning from each of the 12 tags to each of the 12 tags given the word in the context.
We performed Laplace Smoothing for handling words which aren’t in the corpus.
At the end of each iteration, we retain a path for each tag which ends in the highest sequence probability. 
When we encounter the last word in the sentence, we just consider the transition probability to ‘END’ tag, and select the maximum probability path out of the 12 options.

-> Laplace Smoothing Implementation

We have used Laplace smoothing over the transmission table and for emission probabilities of unknown words.
Laplace Smoothing over the transition table helps in alleviating the issue of very rarely occuring transitions in the corpus sentences, which have to be taken into account while tagging new sentences. If this smoothing is not performed, then these types of transitions will get completely ignored.
Emission probabilities for unknown words are given by the formula : 	1/(n+k) 
where
 	~ n is the total number of words which were tagged as the emitting tag, and
	~ k is the total number of unique words in the corpus.
