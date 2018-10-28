1. When using batch-normalization at inference time or test time, always use the popluation mean and population variance. If you instead use the batch-mean and batch-variance and the size of the batch is 1, then x-μ = 0 as μ=x and hence y = γ*x + β would become y = β, which is wrong.

  **Never use this**  - tf.nn.batch_normalization() as it takes batch-mean and batch-variance.

  tf.layers.batch_normalization() 
  tf.contrib.layers.batch_norm() - Either of these two can be used. 
