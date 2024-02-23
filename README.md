# Continual-Learning-Task

Group project for the Deep Learning course, taken in the 3rd year at the Faculty of Mathematics and Computer Science, University of Bucharest.

The project consisted of tackling the AI task of continual learning, that is, making a model capable of remembering taught information over a long period of time, while addressing the concerns of catastrophic forgetting and model scalability. The **dataset** used was [CLEAR-10](https://clear-benchmark.github.io/), which was specifically designed for the task of continual learning, and contains images from 10 years (buckets). We decided to tackle this task by employing the **experience replay** method from the field of **reinforcement learning**. Thus, after every train bucket, we would retain 1% or 5% of the data in the respective bucket before moving on to the next train bucket. In order to choose which samples to retain, we tested four metrics: **error L2 norm**, **Shannon entropy**, **margin** (the difference between the logit of the correct class and the other largest logit. For misclassified samples the margin is negative), and random sampling; and we chose to keep only the hardest samples.

<details>
<summary><h3>Some of the results obtained:</h3></summary>

![avg_test_acc](https://github.com/alexsasu/Continual-Learning-Task/assets/87432371/44595da8-1f46-41ab-ad0f-dca73e684677)
- baseline cl - training on each bucket without retaining samples from the previous buckets
- baseline iid - training on all the buckets at once
</details>

The metric which brought the best results with the **experience replay** method was the random sampling metric.

For our architecture, we used the **ResNet18** provided by **PyTorch** - which was trained only on our data - along with an **SGD optimizer** with a **starting learning rate of 0.01**, **cross-entropy loss**, **cosine annealing scheduler**, **training batch size of 64**, and **a number of epochs of minimum 20 and maximum 40**.

More info can be consulted in the "Poster.pdf" file.

### Contributors:
- Alexandru Sasu (https://github.com/alexsasu/)
- Cristian Paduraru (https://github.com/PaduraruCristian/)
