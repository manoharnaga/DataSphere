# DataSphere

## Overview
DataSphere is an OLAP project that focuses on extracting and analyzing data cubes using advanced data mining techniques. The project implements the BUC (Bottom-Up Cubing) algorithm, incorporating various optimizations and methodologies to enhance data processing and insight extraction.


## Features

1. **BUC Algorithm Implementation**:
   - Developed a robust implementation of the BUC algorithm to efficiently extract interesting data cubes from large datasets.
   - Employed optimizations such as **external sorting**, **hash partitioning**, and **dimensional ordering by cardinality** to improve performance and reduce memory usage.

2. **Minsup and Iceberg Cube**:
   - Utilized a minimum support threshold (minsup) to filter out uninteresting data, generating iceberg cubes that focus on significant data patterns.
   - Enabled dynamic adjustment of minsup to analyze the impact on data extraction results and runtime performance.

3. **Runtime Performance Analysis**:
   - Conducted extensive comparisons of runtime performance for both in-memory and out-of-memory BUC implementations.
   - Generated runtime plots to visualize the differences in performance under varying conditions and dataset sizes, providing insights into the efficiency of each approach.

4. **Characteristic Rules Extraction**:
   - Implemented attribute-oriented induction (AOI) methods to derive characteristic rules from the extracted data cubes.
   - The derived rules offer valuable insights into data relationships, aiding decision-making processes.

5. **Movie Recommender System**:
   - Built a movie recommender system using the Apriori algorithm to identify frequent itemsets and association rules among user preferences.
   - The system analyzes user ratings and behaviors to recommend movies, enhancing user experience through personalized suggestions.

## Technologies Used
- Programming Languages: Python
- Libraries: Pandas, NumPy, Scikit-learn
- Visualisation: Matplotlibt
  
## Conclusion
DataCubes is a comprehensive project that showcases the application of advanced algorithms in data analytics. The combination of the BUC algorithm and the Apriori algorithm demonstrates the potential for extracting meaningful insights from complex datasets, paving the way for enhanced decision-making and recommendations in various domains.
