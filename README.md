# REAL NVP (Real-valued Non-Volume Preserving)

REAL NVP is a **normalizing flow** model published in 2017 by **Laurent Dinh et al.**,  
from the DeepMind team at Google. It belongs to the family of **normalizing flow models**,  
where a complex random variable is transformed bijectively into a simpler distribution,  
usually a Gaussian.

For inference, a sample is first drawn from a standard normal distribution.  
By applying the inverse transformations learned by the model, a realistic data point is then reconstructed  
in the original space. This process is fast and does not require iterative steps  
as in traditional generative models.

The learning of this transformation relies on **coupling layers**, which ensure  
a simple inversion while maintaining great flexibility in modeling the distribution.  
Each coupling layer divides the data into two parts:  
- One part is left unchanged
- One part is transformed parametrically based on the other

This alternating transformation ensures that, over the layers, **all dimensions of the data**  
are gradually modified. Additionally, it allows for an efficient calculation of the Jacobian, thus avoiding  
the exponential cost often associated with explicit density models.

The training of REAL NVP is based on **maximum likelihood maximization**,  
enabling stable learning without the need for adversarial techniques.
