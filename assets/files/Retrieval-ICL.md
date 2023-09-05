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

