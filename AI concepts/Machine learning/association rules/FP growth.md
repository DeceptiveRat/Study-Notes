1. FP growth
- grow long patterns (itemsets) from short ones using local frequent items => avoid generating candidate itemsets
- advantages:
   - 2 database scans
   - smaller memory requirement compared to apriori
   - fast time due to absence of candidates

2. FP growth stage 1: FP tree construction
- step 1: 
   - construct 1-itemset
   - prune
   - create f-list
   - sort items in table in frequency-descending order
- step 2:
   - construct FP tree
   - construct header table

3. FP growth stage 2: mine conditional FP trees
- step 1:
   - find every frequent item X on FP tree by following linked list
   - for each occurence of X, accumulate all direct ancestors of X
   - construct conditional FP tree from each conditional pattern base
- step 2: mine conditional FP tree recursively

4. walkthrough
- construct 1-itemset
![unnamed_40448f0a3c8e4f2d9c73879b790cd557](unnamed_40448f0a3c8e4f2d9c73879b790cd557.png)

- create f-list where min support = 3
![unnamed_96cc021c41c7481a97b15ebf2869a6aa](unnamed_96cc021c41c7481a97b15ebf2869a6aa.png)

- sort
![unnamed_f1607d390aac4c9dae6e85fe3f9be603](unnamed_f1607d390aac4c9dae6e85fe3f9be603.png)

- construct FP tree
![unnamed_4e509881a5e24bb5abd09be683a518ef](unnamed_4e509881a5e24bb5abd09be683a518ef.png) => 	=> ![unnamed_d579777b9c824866b1bc2d769eed0bba](unnamed_d579777b9c824866b1bc2d769eed0bba.png) => ![unnamed_a44c71d55dca4ff481740667f0d79325](unnamed_a44c71d55dca4ff481740667f0d79325.png) => ![unnamed_4c36ebb5a1e04923997fc762a0555410](unnamed_4c36ebb5a1e04923997fc762a0555410.png)![unnamed_ef45eeb3736a403995c832063cbcfdbb](unnamed_ef45eeb3736a403995c832063cbcfdbb.png)

- construct header table
![unnamed_2962e9ff7dfe488aacfeb3e5ded01384](unnamed_2962e9ff7dfe488aacfeb3e5ded01384.png)

- create conditional pattern bases
![unnamed_c29498cf93334fe1aac34117f4359c95](unnamed_c29498cf93334fe1aac34117f4359c95.png)

- construct conditional FP trees (e.g. m):
   - m-conditional pattern base: fca(2), fcab(1) => fff ccc aaa b
   - prune 
   - create m-conditional FP tree
	



![unnamed_70eefdfba0d243a58f05195f242ce896](unnamed_70eefdfba0d243a58f05195f242ce896.png)![unnamed_ed4b5418663b44b59550031040c9f84f](unnamed_ed4b5418663b44b59550031040c9f84f.png)![unnamed_616b96dae1ed4af08d1e4224a7cfc12d](unnamed_616b96dae1ed4af08d1e4224a7cfc12d.png)

- mine conditional FP trees
 => ![unnamed_01826950d5de46c39399666c646ef7a6](unnamed_01826950d5de46c39399666c646ef7a6.png)![unnamed_f36e1eb5033c494cb1b7ad71fafdd86b](unnamed_f36e1eb5033c494cb1b7ad71fafdd86b.png)

- generate association rules
- prune

reference:
- Gachon University - Machine learning lecture