Truth be Told: In this question, we are given a dataset of user-generated reviews in the form of training dataset and testing dataset. 
We are supposed to create a 'Naive Bayes classifier', which classifies the reviews into fake or legitimate for 20 hotels in Chicago. 
The training dataset has labels which tell if the review is 'deceptive'  or 'truthful' along with the review. 

### **Bayesian Classifier:**
To classify the reviews into 'deceptive' and 'truthful', we tried to calculate the probability that a given review is 'truthful' conditioned that it has the words('*P('truthful'|words)'*). Otherwise, it is 'deceptive'. 

* We first get the training data file('deceptive.train.txt') into the form of a dictionary called train_data which has the keys 'labels','objects' and 'classes'. The values for each of the keys is in the form of lists. The values for 'labels' is whether the particular review is 'truthful' or 'deceptive'. In the case of the value for 'objects', it is a list of all the reviews. And finally the value for 'classes' is a list of possible cases i.e 'truthful' or 'deceptive'.

* We then use a python library package called 're' for regular expressions. We use regular expressions to remove all the punctuation marks in the reviews in both training and testing data.

* After we remove the punctuation marks from the reviews, we strip the sentences of any whitespaces at the front and back of the sentence and then, lowercase all the characters in the review. 

* We then store all the words in a dictionary called all_words with the word as the key and the value as a tuple of two numbers in which the first is the number of times a word repeats when the review is 'truthful' and the second being when the same word repeats when the review is 'deceptive'.

* We then use the dictionary of all_words to calculate the probabilities of the unique words, both in the case of 'truthful' and 'deceptive'. We are calculating the probability of the given word, conditioned that the review is 'truthful' or 'deceptive'.(*(P(word|'truthful') or P(word|'deceptive')*)

* We also calculate the probability of the given message being 'truthful' or 'deceptive' by counting the number of occurences of the word 'truthful' and 'deceptive' and dividing it by the length of train_data['labels'].

* We then run a for loop for all the words of each of the review in the test data set. We get the probability that is already calculated for each word and multiply it to the corresponding truthful probability or deceptive probability.(*(P('truthful') * P(word1|truthful) * P(word2|truthful)...)  and (P('deceptive') * P(word1|deceptive) P(word2|deceptive)...)*)

* We store each of the above calculated probability into variables called prob_t and prob_d. We then divide the prob_t by prob_d for each review and if the value is greater than 1, then we store the result as 'truthful' otherwise it is 'deceptive'.

### **Result:**
The Result is stored in the form of a list which contains if the given review in each of the test data set is 'truthful' or 'deceptive'. 
We are getting a accuracy of 79%.
