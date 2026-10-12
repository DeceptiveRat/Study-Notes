1. user-based CF
- recommendations are made by finding users with similar preferences

2. steps
- normalize data
- calculate user similarities
   - identify users who rated items that target user rated
   - Pearson correlation used often to calculate similarity score
	![unnamed_2128a77473fb4048ba04e530c8a8d453](unnamed_2128a77473fb4048ba04e530c8a8d453.png)
- determine nearest neighbor users
   - methods
      - use all data
      - select data above similarity threshold (below minus threshold can be utilized as well for negative impact)
      - select top N data by similarity
      - select similar cluster using clustering method
- calculate item scores
   - identify users who rated items not rated by target user
   - for each item generate rate prediction via weighted average
	![unnamed_4c86cb190fe6472b9dffd28df7874488](unnamed_4c86cb190fe6472b9dffd28df7874488.png)
	(adjust target's average by the weighted sum of deviations by similar users from their average)
- determine item(s) to recommend

3. demonstration - [1]
![unnamed_2a12b1468658469596cf0daf3d47be77](unnamed_2a12b1468658469596cf0daf3d47be77.png)

- normalize data
![unnamed_16d66710d03f4992b92da805668eefd2](unnamed_16d66710d03f4992b92da805668eefd2.png)

- compute user similarity
![unnamed_7cadd8e4f9994f1ba16d258804214d63](unnamed_7cadd8e4f9994f1ba16d258804214d63.png)

- select neighbors of user2 (threshold +0.1)
![unnamed_33a9205a91d34674820fd75d7d328941](unnamed_33a9205a91d34674820fd75d7d328941.png)
users 3, 4, 6, 9

- identify items not rated by target user
![unnamed_8739a53f96714715b56d06372c10ed3b](unnamed_8739a53f96714715b56d06372c10ed3b.png)
joke 1, 2, 3, 4, 9, 10

- predict item scores
![unnamed_459d724729d74ad3bb46f7dd4eb91f96](unnamed_459d724729d74ad3bb46f7dd4eb91f96.png)

- choose items using score

4. user-based CF advantages
- doesn't require information about users and items
- easy to implement

5. user-based CF disadvantages
- doesn't perform well when ratings matrix has a large number of users
- doesn't perform well when ratings matrix is sparse
- user similarity can't be calculated for new users (cold start)

reference:
- Gachon University - Machine learning lecture

notes:
[1]: view Machine Learning lecture notes for python code