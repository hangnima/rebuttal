# rebuttal
1. **Ablation experiments of scalar label and vector label**  
   For comparison with Figure 2 in the paper, we replaced 'fox→cat' and 'dog→cat' with a single scalar label 'cat' when using cross-attention. Since both 'fox→cat' and 'dog→cat' generate cat images, this substitution did not affect their outputs. However, due to the alternating iterative nature of DSB model training, the reverse transformations 'cat→fox' and 'cat→dog' were significantly impacted, as demonstrated in the results shown in scalar-label-dog.png, scalar-label-fox.png, vector-label-dog.png and vector-label-fox.png. The use of scalar labels was found to weaken the conditional guidance effect. The results of quantitative metrics are shown in the table below.  

|              |          | LPIPS           | FID            | CLIP            |
| :----------- | :------- | :-------------: | :------------: | :-------------: |
| scalar-label | cat->dog | ****0\.7755**** | 122\.28        | 0\.8751         |
| vector-label | cat->dog | 0\.7972         | ****97\.58**** | ****0\.9302**** |
| scalar-label | cat->fox | 0\.7512         | 109\.91        | 0\.8455         |
| vector-label | cat->fox | ****0\.7326**** | ****81\.36**** | ****0\.8851**** |

2. **Slower convergence is quantified via the loss decay rate metric**   
   We quantify the convergence speed difference through loss decay rate analysis, where the 3-category scenario demonstrates faster initial convergence compared to the 7-category case, resulting in higher loss decay rates during early training phases that subsequently become lower than those of the 7-category scenario as optimization progresses, with comparative results visualized in loss-decay-ratio.png.

3. **Quantitative metrics on the AFHQ dataset**   
We have incorporated FID, LPIPS, and CLIP scores as quantitative evaluation metrics, with the experimental results on the AFHQ dataset presented in the following table.

|                   |          | LPIPS       | FID        | CLIP        |
| :---------------- | :------- | :---------: | :--------: | :---------: |
| Dhariwal's Method | cat->dog | 0\.7784     | 164\.06    | 0\.8681     |
| Cross Attention   | cat->dog | 0\.7972     | 97\.58     | 0\.9302     |
| Multi-marginal    | cat->dog | **0\.6395** | **42\.44** | **0\.9979** |
| Dhariwal's Method | cat->fox | 0\.7943     | 99\.31     | 0\.8754     |
| Cross Attention   | cat->fox | **0\.7326** | 81\.36     | 0\.8851     |
| Multi-marginal    | cat->fox | 0\.7564     | **42\.41** | **0\.9887** |
