#### 1. Determinantal Point Process (DPP)

因为在读ACL2023关于retrieval-augmented ICL的时候碰到了DPP，他们在从training set或者corpus选择若干个demonstration的时候使用了DPP算法，保证了所选择的demonstration $z$和输入$x$之间的相似度（similarity），又保证了所选的demonstration的多样性（diversity）。

行列式点过程（DDP）是使用矩阵行列式计算一个集合$Z$中所有子集的概率，然后通过最大后验估计，从$Z$中找到与输入$x$相关性和多样性最大的子集。实际上这个算法常用于推荐系统，$Z$对应的是商品集合，$x$对应的是用户特征。而在ICL的demonstration selection中$x$代表输入文本，$Z$代表待选择的若干个demonstrations（candidates）。

对于一个给定的离散集合$Z=\{1,2,3, ...,M\}$，当给定空集出现的概率的时候，存在由一个集合$Z$中元素构成的半正定矩阵$L⊆ R^{M\times M}$，对$Z$的每个子集$Y$，都有$P(Y)\propto det(L_Y)$，$L_Y$是子集$Y$中的任意两个元素作为下标，在矩阵$L$中对应的元素组成的行列式的值。

> 对任意的非零向量$X$，都有$X^TLX\geq 0$，$L$是半正定矩阵。

例如：

<img src="/Users/yuguoxin/Documents/个人资料/个人主页/CatYu98.github.io/assets/images/DPP_example.webp" alt="DPP_example" style="zoom:50%;" />

因为$L$是半正定的，存在矩阵$B$，使得$L=B^TB$，并且$P(Y)\propto det(L_Y)=Vol^2(B_i)$，$i\in Y$。

为了应用于实际场景中，进一步将$B_i$分解为$B_i=r_if_i$，在推荐中$r_i$是item和user之间的相关性，$r_i\geq0$；$S_{ij}=<f_i, f_j>$是item i和item j之间的相似度，$||f_i||_2=1$，于是有：
$$
L_{ij}=<B_i,B_j>=<r_if_i, r_jf_j>=r_ir_js_{ij}\\
P(Y)\propto det(L_Y)=\prod_{i\in Y}r_i^2det(S_Y).
$$
$L_{ij}$是半正定矩阵$L$中的元素，那么原本的计算$det(L_Y)$的方法可以进一步推导，化为$S_Y$的行列式的累乘结果。在ICL中，$r_i$对应输入和demonstration的相似度，$s_{ij}$代表不同demonstration之间的相似度。这样$P(Y)$越大，说明这个集合$Y$同时具有越大的similarity好人diversity。

#### 2. 优化

优化目标为$Y^*=argmax\{det(L_Y)\}$，直接优化是NP-hard问题，因此将其取对数之后转化为次模函数，$f(Y)=\log(argmax\{det(L_Y)\})$，次模函数即边际效应，就是说随着向集合中添加元素，函数值的增加量会愈来越小，举个🌰，有一天你非常饿，吃第一口饭的时候获得的满足感很大，随着往后吃的越来越饱，你没吃一口饭的快乐和满足感都会减小，这就是边际效应。（emmm我觉得这个就像是谈恋爱，一开始是热恋期，随着天数的增加越来越觉得增加的幸福感很少了，最后变成日复一日也就那样。）

言归正传，既然这个取对数后的优化目标符合次模函数，那么有：
$$
i=\in Z, X⊆ Y⊆ Z/ \{i\},\\
f(X\cup i)-f(X) \geq f(Y\cup i)-f(Y),\\
这里理解为i加入X比i加入Y更早，属于前半段的热恋期。
$$
直观说在前期集合小的时候加入一个元素带来的增益要更大。

那么优化问题可以转换为贪婪的形式：
$$
Y^*=argmax\{f(Y\cup i)-f(Y)\}=argmax\{\log(det(L_{Y\cup i}))-\log(det(L_Y))\}
$$
也就是说每次选择添加对下游任务最有帮助受益最大的example，知道满足指定的个数或者其他条件，构成demonstration。



以上内容参考了[博客](https://www.infoq.cn/article/hr0clpj*b7d6fhlfv3xd)。