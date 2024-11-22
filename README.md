java c
Data Mining: Projects List
September 27th, 2024
1    Problem 1: Vision Transformers - Practical StudyThe goal of this task  is to  measure  speed-accuracy tradeoffs  for  different  efficient  Transformer- architectures tested on image classification tasks.  Compare regular Vision Transformer (ViT) with Performer applying different attention kernels leveraging deterministic kernel features:  Performer- ReLU and Performer-exp.  Record training, inference time and classification accuracy on eval tests for all three Transformer types. You can test your models on any of the following datasets (or their subsets):  MNIST, CIFAR10, ImageNet, Places365.   Bonus  points:   Can you  design Performer- fθ  variant, where fθ  is a learnable function defining attention kernel and that outperforms both: Performer-ReLU and Performer-exp ?
Note: A Performer-f variant is a Transformer replacing regular softmax attention kernel K(q, k) = exp with K(q, k) = f(q)f(k)T .
2    Problem 2:  Performers With Random Features - Practical Study
The goal of this task is to quantify the accuracy of the linear low-rank attention models leveraging the mechanism of positive random features.  Note that in this setting, the attention kernel K(q, k) =
exp is replaced with K(q, k) = , where ϕ+  is given as:for ω1, ..., ωmiid∼ N (0, IdQK).  Compare the accuracy of the approximation of the attention matrix (no row-normalization required) as a function of the number of random features m applied.  Mea- sure the error as a relative Frobenius error.  Conduct those tests for various distributions of query- and key-vectors and different sequence lengths.  Can you design distributions over queries and keys leading to ”spiky” attention patterns, where the groundtruth attention matrix has a sparse number of large entries and the remaining ones are near-zero ?  Test also the variant where ω 1 , ...,ωm  form. block-orthogonal patterns, where within each dQK-element block the projections are exactly orthog- onal.  How does the quality of the approximation change when you replace Gaussian vectors with Rademacher vectors of entries taken independently at random from the two-element set:  {−1, +1} 代 写Data Mining: Projects ListC/C++
代做程序编程语言(with probability 2/1 each) ?
3    Problem 3: Masked Attention
Consider a Transformer architecture where entries of the (not row-normalized) attention matrix are of the following form.	
where vq , vk  are some feature vectors associated with queries and keys respectively (you can assume that they can be efficiently computed for their corresponding queries/keys).  Design an unbiased randomized mechanism for approximating K(q, k) that can be implemented within the low-rank linear-attention scope.   Note:  You  can consider attention mechanism which is a subject of this problem a masked attention variant, where regular attention kernel exp is modulated by the mask entry of the form. (ReLU(vq)ReLU(vk)T).
4    Problem 4:  Combining different approximators of the attention kernelConsider an attention kernel K : Rd  × Rd  → R and two of its estimators K1(一)(x, y) = ϕ(x)ϕ(y)T  and K2(一)(x, y) = ψ(x)ψ(y)T  for some  (potentially randomized) maps:  ϕ  : Rd  → Rm  and ψ  : Rd  → Rr .Assume that the kernel acts on vectors taken from the sphere of the given radius R.  Assume that the former estimator is very accurate for estimating small kernel values and that those correspond to large angles between the input vectors (this is the case in particular for the softmax-kernel) and the latter is particularly accurate for estimating large kernel values and that those correspond to small angles between the input vectors (this is the case in particular for the softmax-kernel).  Can you design a third estimator that combines both and is defined as a linear combination of them ?  The goal of the estimator is to combine the best from both worlds, as being particularly accurate for both: small and large kernel values regime.  The estimator should also support low-rank linear-attention computations.  Hint:  Try to define the coefficient of the linear combination as the affine functions of the angle αx,y  ∈ [0,π] between the input vectors x, y and leverage the following observation:
where randomized mapping τ is given as:
for ω1, ..., ωmiid∼ N (0, Id). Here m is the hyperparameter of the algorithm.









         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
