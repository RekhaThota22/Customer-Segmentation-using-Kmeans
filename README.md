# Customer-Segmentation-using-Kmeans
This project covers the complete pipeline for clustering customers based on the Online Retail dataset.

1.We start by importing the necessary libraries for data manipulation, visualization, and machine learning algorithms.
Numpy
pandas
matplotlib.pyplot
sklearn for preprocessing
sklearn.cluster import KMeans, DBSCAN
sklearn.preprocessing import StandardScaler
sklearn.metrics

2.Data Understanding¶
Why: Before applying any algorithm, we need to understand the shape of our data,
 the features available, and check for missing values to plan our preprocessing steps.

3. Data Preprocessing (RFM Analysis)
Why: The raw dataset is purely transactional. If we cluster raw transactions, we are clustering receipts, not customers.
To fix this, we aggregate the data to a customer level using the RFM framework:

Recency: How many days ago was their last purchase?
Frequency: How many times have they purchased?
Monetary: How much have they spent in total?
Finally, we apply StandardScaler. K-Means uses Euclidean distance, 
which is highly sensitive to the scale of features. (e.g., Monetary could be in thousands, while Frequency is single digits).

4.Exploratory Data Analysis (EDA)
Why: Visualizing distributions using boxplots helps us spot extreme outliers. 
Retail data is naturally heavily right-skewed (a tiny handful of wholesalers buy massively more than average customers).

5.Optimal Cluster Selection (Elbow Method)
Why: K-Means requires us to manually define the number of clusters (K). We run the algorithm multiple times (K=1 to 10) and plot the Within-Cluster Sum of Squares (WCSS).
We look for the "elbow"—the point where adding another cluster gives diminishing returns in variance explanation.

6.Apply K-Means
Why: Looking at the elbow plot, a bend typically occurs around K=3. We will group our dataset into 3 primary customer profiles.

7.Visualization of Clusters
Why: Scatterplots allow us to visually verify if our clusters are logically separated.
We plot Recency against Monetary to see if "high spend / low recency" separated out clearly.

8.Apply Other Algorithms (DBSCAN)
Why: K-Means assumes spherical clusters and forces every point into a cluster, making it sensitive to outliers. DBSCAN identifies dense groups and isolates outliers as noise (label -1). 
This is excellent in retail for catching massive wholesale buyers who skew averages.

9.Performance Evaluation (Silhouette Score)
Why: The Silhouette Score measures cluster cohesion (how close points are to their own cluster) vs separation (how far they are from other clusters). 
It ranges from -1 to 1. A higher score means better-defined segmentation.

10.Cluster Interpretation
Why: Algorithms only provide mathematical labels (0, 1, 2). It is the data scientist's job to map these mathematical groups to actionable business strategies (e.g., Target Cluster X with discounts to win them back).
