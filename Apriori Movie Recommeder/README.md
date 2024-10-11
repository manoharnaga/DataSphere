## Report

### Justification for Selection of the Apriori Algorithm

The **Apriori algorithm** was selected for building the movie recommendation system for the following reasons:

1. **Efficient Candidate Generation**: Apriori uses the principle of **downward closure** (also called **anti-monotonicity**), which states that if an itemset is frequent, then all of its subsets must also be frequent. This significantly reduces the number of candidate itemsets to be evaluated, improving computational efficiency.

2. **Well-Suited for Transactional Data**: The algorithm is specifically designed for finding frequent patterns in transactional datasets. Since the user-movie ratings can be viewed as transactions, Apriori fits naturally into the problem domain.

3. **Frequent Itemset Mining**: The objective of the assignment is to generate association rules based on movies users have already watched. Apriori efficiently generates frequent itemsets, which form the basis for these association rules.

4. **Incremental Exploration of Larger Itemsets**: The algorithm starts with single-item frequent sets and builds up to larger itemsets, step by step. This **bottom-up approach** is ideal for datasets like MovieLens, where user preferences tend to form clusters around small sets of frequently watched movies. The scalability to larger combinations is naturally built into the algorithm.
   
5. **Customizable Support and Confidence Thresholds**: Apriori allows flexible setting of minimum support and confidence thresholds, which lets us fine-tune the system to ensure high-quality recommendations (in this case, minsup = 50 and minconf = 0.1).

6. **Effectiveness for Sparse Datasets**: The MovieLens dataset has a large number of movies, but each user only watches a small subset. Apriori's candidate generation method is efficient in handling such sparsity, ensuring that only meaningful associations are discovered.
---

### System Overview: How the Recommendation System is Built

The movie recommendation system was built following these key steps:

1. **Data Preprocessing**:
   - The dataset was filtered to include only users who rated more than 10 movies and movies with ratings above 2.
   - The data was split into an 80% training set and a 20% test set.

2. **Frequent Itemset Mining**:
   - Using the **Apriori algorithm**, frequent itemsets of movies were generated based on a minimum support threshold of 50. Each itemset represents movies that are frequently watched together.

3. **Association Rule Generation**:
   - From the frequent itemsets, association rules of the form `X → Y` were generated, where `X` contains one movie, and `Y` contains movies frequently watched with `X` having confidence more than 0.1.

4. **Recommendation and Evaluation**:
   - For each user in the test set, the system applied relevant association rules and computed **precision** and **recall**. The system was evaluated by generating precision-recall plots and calculating the average recall and precision across users.

   - **Loop Over Number of Rules**: For each value of `num_rules` from 1 to 10, we calculated precision and recall.
   - **Loop Over Users**: For each user in `test_movie_dict`, we generated recommendations and calculated precision and recall.
   - **Generate Recommendations**: For each movie in the user's training set, we found the relevant rules and generated a list of recommended movies.
   - **Calculate Precision and Recall**: We calculated the precision and recall by comparing the recommended movies with the movies the user actually watched in the test set.
   - **Store Results**: We stored the precision and recall values for each user in `user_ids` and calculated the average precision and recall for all users.

6. **Plotting Results**
   - **Plot Graphs**: We used `matplotlib` to plot the precision and recall for each user against the number of rules.


### **Impact of Adding More Rules**

- **Precision**:
  - As new rules are added with **lower confidence and support**, precision tends to **decrease**.
  - Lower-quality rules introduce more **false positives**, leading to **less relevant** recommendations.
  - Adding too many rules **dilutes** precision as the system suggests less relevant movies.

- **Recall**:
  - Recall generally **increases** as more rules are added, even with lower confidence.
  - More rules capture additional **true positives**, improving the system’s ability to suggest relevant movies.

### **Trade-off Between Precision and Recall**:
- **Fewer, high-confidence rules** prioritize **precision**, but recall may **suffer** by missing some true positives.
- **More, lower-confidence rules** increase **recall** by capturing more true positives but **reduce precision** by introducing irrelevant recommendations.

![alt text](image.png)

![alt text](image-1.png)
