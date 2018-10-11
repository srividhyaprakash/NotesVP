# Please feel free to add any other comments, better noise reduction techniques and steps I have missed.

1. Get the labelled corpus

2. Count the words in positive labels, the words in the negative labels and the set of total words using counters.

3. Take positive to negative ratio. 

4. To better differentiate, take the log of the ratio.
    (Words occuring only in the negative labels will have the ratio close to zero, and hence a log of the value will be -ve.)
    (Words occuring only in the positive labels will have the ratio very high, and hence a log of the value will be +ve.)

5. Feed the neural network whether the review/comment contains that word as 0 or 1. 
  (To optimize, never multiply the zero inputs, i.e the words that arent there in the comment/review. Saves computation time.)

6. To detect patterns, the word associated with the positive/negative comment should have atleast come 20 times before, so have
    a minimum count of the word to be 20 and prune those words that are infrequent than that.

7. Common stop words like the, and, "." occur both in the positive and negative comments/reviews, so their log ratio would be
    close to 0. Include only those words that have their absolute log ratio to be greater than 1, so that they really depict
    sentiment.

