Instead of having a single attention head, we can use multiple attention heads. We learned how to compute the attention matrix $Z$, Instead of computing a single attention matrix $Z$  we can compute multiple attention matrices. But what is the use of computing multiple attention matrices? 
Let's understand this with an example. Consider the phrase:
$$All\;is\;well$$
Say we need to compute the self-attention of the word '_well_'. After computing the similarity score, suppose we have the following:

![[Pasted image 20240805104507.png]]
As we can observe from the preceding figure, the self-attention value of the word '_well_' is the sum of the value vectors weighted by the scores. If you look at the preceding figure closely, the attention value of the actual word '_well_' is dominated by the other word '_All_'. That is, since we are multiplying the value vector of the word '_All_' by 0.6 and the value vector of the actual word '_well_' by only 0.4, it implies that $Z_{well}$  will contain 60% of the values from the value vector of the word '_All_' and only 40% of the values from the value vector of the actual word '_well_'. Thus, here the attention value of the actual word '_well_' is dominated by the other word '_All_'.

This will be useful only in circumstances where the meaning of the actual word is ambiguous. That is, consider the following sentence:
$$A\;dog\;ate\;the\;food\;because\;it\;was\;hungry$$
Say we are computing the self-attention for the word '_it_'. After computing the similarity score, suppose we have the following: 

![[Pasted image 20240805105326.png]]

As we can observe from the preceding equation, the attention value of the word '_it_' is just the value vector of the word '_dog_'. Here, the attention value of the actual word '_it_' is dominated by the word '_dog_'. But this is fine here since the meaning of the word '_it_' is ambiguous, as it may refer to either '_dog_' or '_food_'.

Thus, if the value vector of other words dominates the actual word in cases as shown in the preceding example, where the actual word is ambiguous, then this dominance is useful; otherwise, it will cause an issue in understanding the right meaning of the word.

### How to compute multi-head attention matrices

So, in order to make sure that our results are accurate, instead of computing a single attention matrix, we will compute multiple attention matrices and then concatenate their results. The idea behind using multi-head attention is that instead of using a single attention head, if we use multiple attention heads, then our attention matrix will be more accurate. Let's explore this in more detail.

Let's suppose we are computing two attention matrices $Z_{1}$ and $Z_{2}$ First, let's compute the attention matrix $Z_{1}$ 
#### Computing attention matrix Z1
We learned that to compute the attention matrix, we create three new matrices, called query, key, and value matrices. To create the query, $Q_{1}$, key $K_{1}$ and value $V_{1}$ matrices, we introduce three new weight matrices called $W_{1}^Q$  $W_{1}^K$ $W_{1}^V$   We create the query, key, and value matrices by multiplying the input matrix, X by $W_{1}^Q$  $W_{1}^K$ $W_{1}^V$   respectively

Now, the attention matrix $Z_{1}$ can be computed as follows:
$$
Z=softmax(Q_{1}*K_{1}^T/\sqrt{d_{k}})*V_{1}
$$

#### Computing attention matrix Z2
We learned that to compute the attention matrix, we create three new matrices, called query, key, and value matrices. To create the query, $Q_{2}$, key $K_{2}$ and value $V_{2}$ matrices, we introduce three new weight matrices called $W_{2}^Q$  $W_{2}^K$ $W_{2}^V$   We create the query, key, and value matrices by multiplying the input matrix, X by $W_{2}^Q$  $W_{2}^K$ $W_{2}^V$   respectively

Now, the attention matrix $Z_{2}$ can be computed as follows:

### Concatenating multiple attention matrices

Similarly we can compute $h$ number of attention matrices. Suppose we have eight matrices $Z_{1}$ to $Z_{8}$; then we can just concatenate all the attention heads (attention matrices) and multiply the result by a new weight matrix $W^O$ and create the final attention matrix as shown 

$$Multi-head\;attention=Concatenate(Z_{1},Z_{2},Z_{3},Z_{4},Z_{5},Z_{6},Z_{7},Z_{8})$$
