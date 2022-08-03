# Feature scaling 

Feature scaling in machine learning is one of the most critical steps during the pre-processing of data before creating a machine learning model, which is used to normalize the range of independent variables or features of data. 

## :placard: Methods for Scaling

### :label: Min-max normalization

Also known as **min-max scaling** or **min-max normalization**, rescaling is the simplest method and consists in rescaling the range of features to scale the range in [0, 1] or [−1, 1]. Selecting the target range depends on the nature of the data. The general formula for a min-max of [0, 1] is given as: 

$$ 
x'={\frac{x-{\text{min}}(x)}{{\text{max}}(x)-{\text{min}}(x)}}
$$ 

where $x$ is an original value, $x'$ is the normalized value. For example, suppose that we have the students' weight data, and the students' weights span [160 pounds, 200 pounds]. To rescale this data, we first subtract 160 from each student's weight and divide the result by the difference between the maximum and minimum weights, 40.

To rescale a range between an arbitrary set of values $[a, b]$, the formula becomes:

$$ 
{\displaystyle x'=a+{\frac {(x-{\text{min}}(x))(b-a)}{{\text{max}}(x)-{\text{min}}(x)}}}
$$ 

where $a$, $b$ are the min-max values.

### :label: Mean normalization

$$ 
x' = \frac{x- \text{average}(x)}{\text{max}(x)-\text{min}(x)}
$$ 

where $x$ is an original value, $x'$ is the normalized value. 

### :label: Standardization (Z-score Normalization)

Feature standardization makes the values of each feature in the data have <span style="color:blue">*zero-mean*</span>. (when subtracting the mean in the numerator) and <span style="color:blue">*unit-variance*</span>. This method is widely used for normalization in many machine learning algorithms (e.g., support vector machines, logistic regression, and artificial neural networks). The general method of calculation is to determine the distribution mean and standard deviation for each feature. Next we subtract the mean from each feature. Then we divide the values (mean is already subtracted) of each feature by its standard deviation.

$$
x' = \frac{x- \bar{x}}{\sigma}
$$

where $x$ is the original feature vector, ${\bar {x}}={\text{average}}(x)$ is the mean of that feature vector, and 
$\sigma$ is its standard deviation.

## :placard: When to use Normalization or Standardizatio

If you have ever built a machine learning pipeline, you must have always faced this question of whether to Normalize or to Standardize. While there is no obvious answer to this question, it really depends on the application, there are still a few generalizations that can be drawn.

**Normalization** is good to use *when the distribution of data does not follow a Gaussian distribution*. It can be useful in algorithms that do not assume any distribution of the data like K-Nearest Neighbors.

In Neural Networks algorithm that require data on a 0–1 scale, normalization is an essential pre-processing step. Another popular example of data normalization is image processing, where pixel intensities have to be normalized to fit within a certain range (i.e., 0 to 255 for the RGB color range).

**Standardization** can be helpful in cases where *the data follows a Gaussian distribution*. Though this does not have to be necessarily true. Since standardization does not have a bounding range, so, even if there are outliers in the data, they will not be affected by standardization.

In clustering analyses, standardization comes in handy to compare similarities between features based on certain distance measures. Another prominent example is the Principal Component Analysis, where we usually prefer standardization over Min-Max scaling since we are interested in the components that maximize the variance.

There are some points which can be considered while deciding whether we need Standardization or Normalization

* Standardization may be used when data represent Gaussian Distribution, while Normalization is great with Non-Gaussian Distribution
* Impact of Outliers is very high in Normalization
* 
To conclude, you can always start by fitting your model to raw, normalized, and standardized data and compare the performance for the best results.


!!! info "Reference and related articles"
    * :ledger: [All about Feature Scaling](https://towardsdatascience.com/all-about-feature-scaling-bcc0ad75cb35)
    * :ledger: [When to perform a Feature Scaling?](https://www.atoti.io/articles/when-to-perform-a-feature-scaling/)
    * :ledger: [Wiki-Feature scaling](https://en.wikipedia.org/wiki/Feature_scaling)