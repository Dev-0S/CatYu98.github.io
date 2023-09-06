Self-Adaptive In-Context Learning: An Information Compression Perspective for In-Context Example Selection and Ordering

two-stage instance-level methods for ICL, first selection, then ranking, each step contains several selective selection/ranking methods.



Unified Demonstration Retriever for In-Context Learning

unified multi-task learning, select demonstrations and optimize by a list-wise ranking loss. update the cadidates by a iterative algorithm





1. About improvement and efficiency 

   Thank you for your response. Since you emphasize efficiency in your paper, it is suggested to report the parameters and training time of the proposed model and baselines, instead of simply proving efficiency by fewer training labels. 

    In addition, the compared model "ABAE-BERT + BERT-Feat + AC-MIMLLN" in your reply seems to be a pipeline model, so more training time and parameters are reasonable. In your reply, it seems that M is omitted after $209.48$.

2. About the accuracy of all three subtasks

   It is feasible to compute the accuracy of all the three subtasks. That means that a predicted result will be considered correct only when the aspect terms, aspect categories, and ratings are extracted successfully. This accuracy could be regarded as a unified metric, which may make your experiments more comprehensive. You can refer to [1] for more details about the F1-I metric. 

   [1] An Interactive Multi-Task Learning Network for End-to-End Aspect-Based Sentiment Analysis

3. About Table3

   The comparison in Table 3 is unfair, which makes it not convincing enough. It is necessary to compare DSPN with End2end-LSTM and End2end-CNN with the same backbones, such as BERT or word2vec. BERT used in DSPN is much stronger than word2vec in End2end-LSTM and End2end-CNN. However, the performance of DSPN is inferior to End2end-LSTM and End2end-CNN on TripDMS.  And the improvement of DSNP is so limited on ASAP. 

   If the main contribution of the paper is efficiency, why not compare the parameters and training time of DSPN with the word2vec-based baselines? A pipeline model based on word2vec seems to be more efficient than DSPN and the performance of a pipeline model based on word2vec is probably not much worse than word2vec-based DSPN because BERT-based DSPN has just reached almost the same performance as End2end-LSTM and End2end-CNN.







---

1. About improvement and efficiency 

   Thank you for your response. Since you emphasize efficiency in your paper, it is suggested to report the parameters and training time of the proposed model and baselines, instead of simply proving efficiency by fewer training labels. 
   
   In addition, the compared model "ABAE-BERT + BERT-Feat + AC-MIMLLN" in your reply seems to be a pipeline model, so more training time and parameters are reasonable. In your reply, it seems that M is omitted after $209.48$.

2. About the accuracy of all three subtasks

   It is feasible to compute the accuracy of all the three subtasks. That means that a predicted result will be considered correct only when the aspect terms, aspect categories, and ratings are extracted successfully. This accuracy could be regarded as a unified metric, which may make your experiments more comprehensive. You can refer to [1] for more details about the F1-I metric. But this is just a suggestion, you can consider adding it in a later version.

   [1] An Interactive Multi-Task Learning Network for End-to-End Aspect-Based Sentiment Analysis

3. About Table3

   The comparison in Table 3 is unfair, which makes it not convincing enough. It is necessary to compare DSPN with End2end-LSTM and End2end-CNN with the same backbones, such as BERT or word2vec. BERT used in DSPN is much stronger than word2vec in End2end-LSTM and End2end-CNN. However, the performance of DSPN is inferior to End2end-LSTM and End2end-CNN on TripDMS.  And the improvement of DSNP is so limited on ASAP.  In the response, you claimed that "(1) We also trained a version of DSPN with word2vec encoder instead of BERT, which also outperforms End2end-LSTM on ASAP. We didn’t include the results due to space limitations; ".  Would you like to show the specific results? 

   If the main contribution of the paper is efficiency, why not compare the parameters and training time of DSPN with the word2vec-based baselines? A pipeline model based on word2vec seems to be more efficient than DSPN and the performance of a pipeline model based on word2vec is probably not much worse than word2vec-based DSPN because BERT-based DSPN has just reached almost the same performance as End2end-LSTM and End2end-CNN.  Could you briefly explain the advantages of DSNP in this situation?



1. It is understandable  the accuracy of all three subtask cannot be supplemented due to time constraints.

2. In addition, in your initial reply, is the training time compared under the condition of equal training data? Is this more convincing than training time?

3. In your most recent response, why are the supplemented results of End2end-LSTM and End2end-CNN different from the results in table 3? 

4. In my last comment, I would like to clarify my doubts as follows: 

   We can construct a word2vec-based pipeline model, which consists of three components, solving the ACD, ACSA, and RP tasks respectively. Each component is based on word2vec. 

   Compared to the above constructed pipeline model, the word2vec-based DNSP model may not have obvious advantages in training time and parameters. Furthermore, the word2vec-based DNSP has no adavantages in performance. According to your response, word2vec-based DSPN is even lower than End2end-LSTM by nearly 8 points on TripDMS and barely reached the performance of End2end-LSTM on ASAP. 

   In conclusion, the performance and efficiency of DSNP are not good compared to a pipeline model with the same backbone, when both of them are trained with the same amount of data.

   In this case, it seems to be a better choice to use pipeline model in practical application. 

   Or I can understand that it is the right choice to use DSNP only when the training data of ACD and ACSA are missing.

   The above analysis assumes that the model is based on word2vec, and the same is true for replacing the backbone with BERT.

5. I agree with the comment "it is strange that DSPN didn't consider using LLMs". But what I want to say is that it is reasonable to make a fair comparison with the same backbone, otherwise it will be easily misunderstood that your performance improvement comes from BERT.







Thank you for your reply. I am very happy to have a discussion with you.

1. In your initial reply, did you compare the training time under the condition of equal training data? Would it be fairer if this comparison under the condition of equal training data is made?

2. Given the time constraints, it's understandable that the accuracy of all three subtasks cannot be supplemented.

3. I noticed that in your most recent response, the supplemented results for End2end-LSTM and End2end-CNN differ from those presented in Table 3. What accounts for this difference?

4. In my previous comment, I would like to clarify my doubts as follows: 

   We can construct a word2vec-based pipeline model, which consists of three components addressing the ACD, ACSA, and RP tasks respectively. Each of these components relies on word2vec.

   Compared to the above constructed pipeline model, the word2vec-based DNSP model can not exhibit significant advantages in terms of training time and parameters. Furthermore, the word2vec-based DNSP has no advantages in performance. According to your recent response, word2vec-based DSPN is even lower than End2end-LSTM by nearly 8 points on TripDMS and barely reached the performance of End2end-LSTM on ASAP. 

   To sum it up, DSNP's performance and efficiency don't fare well when compared to a pipeline model with the same backbone, especially when both are trained with an equal amount of data. 

   In such scenarios, opting for the pipeline model appears to be a more practical choice. I can appreciate that using DSNP might be the right decision only when dealing with a scarcity of training data for ACD and ACSA.

   The above analysis assumes that the model is based on word2vec, and the same is true for replacing the backbone with BERT.

5. I agree with the comment "It is strange that DSPN didn't consider using LLMs". But what I want to say is that it is reasonable to make a fair comparison with the same backbone, otherwise, there's a risk of misinterpretation that your performance improvements are attributable to BERT.