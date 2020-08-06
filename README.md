# Deepfake with tensor decomposition

Summer 2020, Internship at DASH Laboratory, SKKU

Searching for Deepfake Detection Algorithm using Tensor Decomposition

## Dive into Dataset

- Visualize & Analyze
	<https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/tensor_dcmp_data_dsc.ipynb>

- Image Dataset Creation
	<https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/Tensor_Image_Creation.ipynb>
	
## Experiments

***Configurations***

- Dataset Composition

| REAL | FAKE(NT) | RATIO |
|---|:---:|---:|
| Total Dataset | 10000 | 10000 | 100% |
| Training Dataset | 8100 | 8100 | 81% |
| Validation Dataset | 900 | 900 | 9% |
| Test Dataset | 1000 | 1000 | 10% |

- Training Options

|Options|Values|
|---|---:|
|Batch size|32|		
|Epochs|100|		
|Base Network|XceptionNet|		
|Initialization|imagenet weights|		
|Augmentations|	rescale=1./255<br>rotation_range=20<br>width_shift_range=0.1<br>height_shift_range=0.1<br>shear_range=0.1<br>zoom_range=0.1<br>horizontal_flip=True<br>fill_mode='nearest'|
|Optimizer|Adam|	
|loss function|Binary Cross Entropy|		
|metrics|accuracy<br>recall<br>precision<br>f1|
|Callbacks|checkpointing<br>cyclical LR-exp_range(1e-3 ~ 7e-3)|	

***Baseline***
<https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/tensor_dcmp_baseline.ipynb>
|	|Precision|Recall|F1|
|---|:---:|:---:|---:|
|REAL|0.78|0.94|0.85|
|FAKE|0.92|0.74|0.82|
|AUROC|0.943088|||
|THRESH|0.1833098829|||
|TOTAL ACCURACY|0.839|||

![baseline accuracy](https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/graphs/baseline_acc.png)
![baseline loss](https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/graphs/baseline_loss.png)

***TK with rank = [30, 30, 3]***
<https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/tensor_dcmp_TK.ipynb>
|	|Precision|Recall|F1|
|---|:---:|:---:|---:|
|REAL|0.77|0.94|0.85|
|FAKE|0.92|0.71|0.81|
|AUROC|0.940521|||
|THRESH|0.0516793727880219|||
|TOTAL ACCURACY|0.8285|||

![tk accuracy](https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/graphs/tk_acc.png)
![tk loss](https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/graphs/tk_loss.png)

***TK_diff***
<https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/tensor_dcmp_TK_diff.ipynb>
|	|Precision|Recall|F1|
|---|:---:|:---:|---:|
|REAL|0.76|0.6|0.67|
|FAKE|0.67|0.81|0.74|
|AUROC|0.78239|||
|THRESH|0.628564715385419|||
|TOTAL ACCURACY|0.708|||

![tk diff accuracy](https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/graphs/tk_diff_acc.png)
![tk diff loss](https://github.com/dongminkim0220/Deepfake_with_tensor_decomposition/blob/master/graphs/tk_diff_loss.png)
