# rebuttal
1. **Ablation experiments of scalar label and vector label**  
   For comparison with Figure 2 in the paper, we replaced 'fox→cat' and 'dog→cat' with a single scalar label 'cat' when using cross-attention. Since both 'fox→cat' and 'dog→cat' generate cat images, this substitution did not affect their outputs. However, due to the alternating iterative nature of DSB model training, the reverse transformations 'cat→fox' and 'cat→dog' were significantly impacted, as demonstrated in the results shown in scalar-label-dog.png, scalar-label-fox.png, vector-label-dog.png and vector-label-fox.png. The use of scalar labels was found to weaken the conditional guidance effect. The results of quantitative metrics are shown in the table below.  

|       | scalar-label | scalar-label         | vector-label |  vector-label           |
| :---- | :----------: | :------: | :----------: | :---------: |
|       | cat->dog     | cat->fox | cat->dog     | cat->fox    |
| LPIPS | **0\.7755**  | 0\.7512  | 0\.7972      | **0\.7326** |
| FID   | 122\.28      | 109\.91  | **97\.58**   | **81\.36**  |
| CLIP  | 0\.8751      | 0\.8455  | **0\.9302**  | **0\.8851** |

2.
