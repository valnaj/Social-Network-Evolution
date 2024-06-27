# Social Network Analytics

## Analyzing Network Dynamics and Influencer Impact on Reddit: A Case Study of the Peaky Blinders Subreddit **April, 2024**

## Introduction

Word of mouth remains the most effective method of disseminating information. Recognizing this, organizations leverage social media platforms in their marketing strategies due to their rapid information dissemination capabilities, nearly at the speed of light. Popular platforms such as X, Instagram, and Facebook are proven effective marketing tools. As Reddit prepares to go public, it is essential to investigate the sustainability of this platform as a social media outlet and its effectiveness in propagating word-of-mouth campaigns. This report explores these aspects by using the Peaky Blinders subreddit as a case study to examine the social network within the Peaky Blinders subreddit, its evolution over time, and the factors that indicate influence within the network.

## Methodology

### Data Collection

Data for this analysis was sourced from the Peaky Blinders subreddit, specifically focusing on interactions during Season 5. The collection spanned three key periods:
- **Pre-air phase:** The week prior to the first teaser release up until the day before the premiere.
- **Airing phase:** From the debut of the first episode to a week after the finale aired.
- **Post-airing phase:** Commencing a week after the final episode and continuing for two subsequent months.

This temporal approach to data collection was pivotal for examining the network’s progression, though it necessitated restricting the scope to only those nodes present in the initial network, thereby ensuring consistent comparability across different stages.

### Network Analysis

Networks were created from all comments and interactions among users in the pre-air period, which included 1,490 users who showed interest in Peaky Blinders. For the airing and post-airing periods, the networks were limited to the group of users who had interactions in the pre-airing period. During the airing period, only 290 of the initial 1,490 users were active, and in the post-airing period, this number dropped to 123.

For each node in these networks, measures such as degree centrality, betweenness centrality, closeness centrality, the number of comments made, the number of submissions made, the number of comments on their comments, and the number of comments on their submissions were obtained. Additionally, the cliques and cores for each node were determined for all three networks, resulting in a rich dataset for each user, which was used in later analyses.

An attempt was made to identify communities within the networks using the Girvan-Newman algorithm. However, the algorithm failed to identify distinct communities, placing most nodes in a single community. This likely resulted from the homogeneity of the nodes, where differences in betweenness centralities were not significant due to the shared interest in Peaky Blinders. The network was densely connected within the community, with few connections between distinct groups.

![image](https://github.com/valnaj/Social-Network-Evolution/assets/136912432/ba547815-dc75-4758-831a-d731d7115e19)

### Network Comparisons: QAP and Chi-square

Network comparisons were performed to evaluate their evolution across different periods. The Quadratic Assignment Procedure (QAP) correlation results indicated a very weak structural similarity between the pre-air and airing periods (Correlation = 0.0007, p-value = 0.2693), and similarly weak similarity between the pre-air and post-air periods (Correlation = 0.0005, p-value = 0.4053). A moderate correlation with significant structural similarity was observed between the airing and post-airing periods (Correlation = 0.0266, p-value = 0.0000). Additionally, Chi-square tests revealed no significant difference in connectivity between the pre-air and airing periods (Chi2 = 0.5033, p-value = 0.4781), suggesting any differences are likely due to chance. No significant differences were found between the pre-air and post-air networks (Chi2 = 0.0068, p-value = 0.9345), implying high structural similarity. In contrast, a significant difference in connectivity patterns was noted between the airing and post-airing networks (Chi2 = 1726.7427, p-value = 0.0000), indicating marked structural changes.

### Understanding Factors Impacting Influence and Comment Score Using OLS

In addition to obtaining measures such as cliques and cores from the three networks, the average sentiment score of each user was calculated. This involved aggregating the sentiment scores from user comments to determine a nodal level score, which was then added to the dataset. With this enriched dataset, two regression models were constructed to predict the degree of centrality and Reddit score for each user. The goal was to identify factors that significantly influence these two metrics, thereby informing marketing strategies.

#### Degree Centrality Prediction

The regression model for degree centrality yielded a mean squared error (MSE) of 0.001. Analysis of the model coefficients revealed divergent impacts from various network features: positive predictors included various clique sizes—with 8-Clique being the most influential—and coreness measures, highlighting that users within denser subnetworks tend to have higher centrality. Conversely, negative predictors such as sentiment score and the number of comments indicated that certain types of engagement do not necessarily contribute to increased centrality.

#### Score Prediction

The score prediction model demonstrated considerable complexity, evidenced by a mean squared error (MSE) of 1845.08 and a root mean squared error (RMSE) of 42.95. The high RMSE indicates that Reddit scores are not impacted purely on network properties, alluding to the potential influence of other external or unaccounted-for factors.

### Influencer Score Generation

To identify the most influential users within the Peaky Blinders subreddit network, an influencer score was computed incorporating network structure and user activity metrics. Clique and core scores were first calculated by summing a user’s involvement in cliques (3-clique to 8-clique) and cores (2-core to 8-core), respectively. These scores reflect a user’s integration within tightly-knit groups and the central structure of the network.

Weights were assigned to various metrics to reflect their importance:
- Betweenness and Closeness: 0.05 each
- Degree Centrality: 0.3
- Comments: 0.15
- Submissions: 0.05
- Reddit score: 0.2
- Clique and core scores: 0.1 each

Each metric was normalized to scale between 0 (minimum) and 1 (maximum) to ensure equal contribution to the final score. The final influencer score for each node was derived by multiplying each normalized metric by its corresponding weight and summing these values. This score quantifies a user’s influence based on their network position, engagement, and community recognition.

![image](https://github.com/valnaj/Social-Network-Evolution/assets/136912432/df163784-7318-4329-948e-a83d8d50b08a)


## Conclusion and Recommendations

This report assessed the sustainability of Reddit as a social media platform and its effectiveness in facilitating word-of-mouth campaigns, highlighted through the analysis of the Peaky Blinders subreddit as Reddit approaches its public offering. Our study across three distinct network phases—pre-release, during airing, and post-airing—revealed substantial network evolution and connectivity changes as demonstrated by Quadratic Assignment Procedure (QAP) and chi-square tests.

The analysis found minimal structural similarities between the different network phases, with very weak correlations particularly between the pre-release and post-airing networks. This indicates that the network undergoes significant restructuring, which could impact the flow of information and the influence of key users within the network. The influencer score model, developed using metrics such as degree centrality, cliques, cores, and user engagement (comments and submissions), was effective in identifying crucial influencers who play a pivotal role in the diffusion of information. Based on these findings, it is recommended that organizations looking to leverage Reddit for marketing should focus on adaptive strategies that accommodate the dynamic nature of Reddit’s network structure. Engaging with key influencers identified through network analysis should be a priority to maximize the reach and effectiveness of marketing campaigns.
