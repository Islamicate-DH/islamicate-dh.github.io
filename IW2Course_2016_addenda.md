---
layout: page
title: The Islamicate World 2.0 Course
subtitle: Addenda
---

# Addenda

## Conceptual Summary of Jockers’ Chapter II

- reading files into R variables
- removing what is not the actual text (splitting, using tagging/metadata, or some other markers)
- normalizing text (`lowercasing`, removing non-letter characters, normalizing spelling variations, removing noise-characters, like short vowels in Arabic)
- collecting, checking and visualizing simple descriptive statistics (unique words, word frequencies, etc.)

### Challenges for Arabic Corpus

- What is the most difficult text in terms of the richness of its vocabulary?
- What is the easiest text—in the same terms?
- What are caveats in evaluating the richness of vocabulary?

## Conceptual Summary of Jockers’ Chapter III

- getting relative statistics on words
- first graphs

### Challenges for Arabic Corpus

- What are the top ten words in specific Arabic texts?
- Do Arabic texts differ much in this regard?

## Conceptual Summary of Jockers’ Chapter IV

- saving often used results into variables for easier reuse

### Code to try — 

```
check = "word" # replace `word` with anything and run the code
word.v <- which(moby.word.v == check) # find check
length.word = length(word.v)
check.count.v <- rep(NA,length(n.time.v))
check.count.v[word.v] <- 1 # mark the occurrences with a 1
plot(check.count.v, main=paste0("Dispersion Plot of '",check,"' (",length.word," times) in Moby Dick"),
     xlab="Novel Time", ylab=check, type="h", ylim=c(0,1), yaxt='n')
```




