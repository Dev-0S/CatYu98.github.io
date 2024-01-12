1. This paper challenges the notion that attention-based models exhibit primacy and recency bias, which is the tendency to recall early and later events in sequences better than events in the middle. This paper shows that primacy and recency biases in transformers are a result of training data distributions, rather than a property of transformer architectures. The authors conducted experiments on Synthetic Data, which evaluates transformer models on non-NLP sequence tasks. The results show that (1) Transient signals are lost as test length Increases regardless of training length; (2) Primacy and recency bias are/(are not) present in time-series transformers.

   

   Strengths:

   1. This paper investigates how the training sequence length and testing sequence length affect predictive performance. 
   2. This paper conducts experiments on non-NLP sequence tasks. 

   Weaknesses: 

   1. This paper is hard to follow. The main contributions of this paper should be summarized in the Introduction section. Paragraphs 3, 4, 5, and 6 of the Introduction section are abrupt.
   2. The proposed method in this paper is not clearly explained. The three formulas on the third page are not clearly stated. The data set and its construction method are also undeclared.
   3. Many implementation details of the experiments are not mentioned.

   

   Questions:

   1. What are the meanings of the symbols in all the formulations? 
   2. On which data sets and tasks were the experiments done?
   3. Is the method proposed in this paper to build a data set or a new indicator or a new model structure?



















This paper challenges the conventional belief that attention-based models exhibit a bias towards prioritizing the beginning and end of sequences, known as primacy and recency bias. These biases refer to the tendency to remember early and later events in sequences better than those in the middle. The paper asserts that these biases observed in transformers are not inherent properties of the transformer architecture but rather a result of the distribution of training data. The authors conducted experiments using Synthetic Data to assess transformer models in non-NLP sequence tasks. The findings reveal the following: (1) Transient signals diminish as the test sequence length increases, regardless of the training sequence length; (2) The presence or absence of primacy and recency bias in time-series transformers.

Strengths:

1. This paper explores the impact of both training sequence length and testing sequence length on predictive performance.
2. The paper conducts experiments in non-NLP sequence tasks.

Weaknesses:

1. The paper may be challenging to follow, and it is advisable to summarize the primary contributions in the Introduction section. Paragraphs 3, 4, 5, and 6 of the Introduction appear abrupt.
2. The explanation of the proposed method in this paper lacks clarity. The three formulas on the third page are not sufficiently elucidated, and the dataset and its construction method remain undisclosed.
3. Many specifics regarding the implementation of the experiments are omitted.

Questions:

1. Could you clarify the meanings of the symbols used in all the formulas?
2. Which datasets and tasks were used for conducting the experiments?
3. The paper does not clearly explain whether the proposed method involves building a new dataset, creating a new indicator, or developing a new model structure.