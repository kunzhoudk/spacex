# Learning rate 

In machine learning and statistics, the learning rate $\alpha$ is a tuning parameter in an optimization algorithm that determines the step size at each iteration while moving toward a minimum of a loss function.

Let's run gradient descent and try a few settings of $\alpha$ on our data set.

![big_learning_rate](./images/learning_rate_big.png)

The plot on the right shows the value of one of the parameters, $w_0$. At each iteration, it is overshooting the optimal value and as a result, cost ends up *increasing* rather than approaching the minimum. Note that this is not a completely accurate picture as there are 4 parameters being modified each pass rather than just one. This plot is only showing $w_0$ with the other parameters fixed at begin values. In this and later plots you may notice the blue and orange lines being slightly off.

Let's try a bit smaller value and see what happens.

![small_learning_rate](./images/learning_rate_small.png)

On the left, you see that cost is decreasing as it should. On the right, you can see that $w_0$ is still oscillating around the minimum, but it is decreasing each iteration rather than increasing. Note above that `dj_dw[0]` changes sign with each iteration as `w[0]` jumps over the optimal value.
This alpha value will converge. You can vary the number of iterations to see how it behaves.

Let's try a bit smaller value for $\alpha$ and see what happens.

![smaller_learning_rate](./images/learning_rate_smaller.png)

On the left, you see that cost is decreasing as it should. On the right you can see that $w_0$ is decreasing without crossing the minimum. Note above that `dj_w0` is negative throughout the run. This solution will also converge, though not quite as quickly as the previous example.
