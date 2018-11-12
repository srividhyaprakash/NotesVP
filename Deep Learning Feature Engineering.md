1. When using batch-normalization at inference time or test time, always use the popluation mean and population variance. If you instead use the batch-mean and batch-variance and the size of the batch is 1, then x-μ = 0 as μ=x and hence y = γ*x + β would become y = β, which is wrong.

  **Never use this**  - tf.nn.batch_normalization() as it takes batch-mean and batch-variance.

  tf.layers.batch_normalization() 
  tf.contrib.layers.batch_norm() - Either of these two can be used. 


2. Training procedure introduced by Alex Krizhevsky:
	
	Set learning rate to whatever intial value you would like. Once validation accuracy stops increases or conversely validation loss stop decreasing, reduce the learning rate by a factor of 10. Keep repeating this procedure until your learning rate is 1% of the initially set value. 

	This kind of seems like weight decay but on a manual basis, helps understand the model you have built better.
	Note: This could potentially cause the model to overfit (say in kaggle competitions).

3. When stuck with CNN's and looking to improve accuracy, try a global average pooling layer towards the end instead of a fully connected layer + dropout. Also try global average pooling layer + dropout. (Global average pooling layer inherently acts as a regularizer).