## The framework of DFuzzer

The quality of seed queue may highly influence the fuzzing result. Intuitively, a high diversity in seed queues can help fuzzers detect different kinds of faults; in other words, a seed queue without a high diversity may cause the omission of some critical faults and thus affect the fault-detection effectiveness of fuzzing.

Motivated by the impact of the diverse seed queues on fuzzing for DL systems, we propose a diversity-driven seed queue construction approach, namely _DFuzzer_. DFuzzer attempts to distribute the seeds as “far away” from one another as possible. Based on the idea of “even spreading”, DFuzzer constructs seed queue by incrementally updating the “best” seeds chosen from the test pool. In addition, we propose two difference measurement metrics _IBDM_ and _FBDM_ based on the information theory and deep features, respectively, to quantify the difference between the seeds in the ongoing seed queue and those in the test pool. Accordingly, two algorithms, namely _DFuzzer-IB_ and _DFuzzer-FB_, are developed to implement DFuzzer based on IBDM and FBDM, respectively.

The framework of the proposed diversity-driven seed queue construction approach (DFuzzer) is illustrated below.
![Image](https://github.com/DFuzzer/DFuzzer/blob/main/d2s2framework2.jpg)

## Implementation
We conducted a series of empirical studies to evaluate the performance of DFuzzer. All related materials (including datasets, models, fuzzers and testing results) are available at this website.

### Datasets
In our experiments, we adopted three popularly used datasets with different types of image: MNIST, ImageNet, and CIFAR10.

Download images of **MNIST** from ![here](http://yann.lecun.com/exdb/mnist/).

Download images of **ImageNet** from ![here](https://image-net.org/).

Download images of **CIFAR10** from ![here](https://cifar.ca/).

### Models

We utilized the open-source DL models to evaluate the performance of DFuzzer, including LeNet-1, LeNet-4, LeNet-5, VGG-16, VGG-19, ResNet-50, and 20 layer CNN with max-pooling and dropout layers. VGG-16, VGG-19, and ResNet50 were pre-trained, and could be found in the Keras. LeNet-1, LeNet-4, and LeNet-5 are provided at the repository: https://github.com/peikexin9/deepxplore. 20 layers CNN is available at the repository: https://github.com/hfeniser/DeepSmartFuzzer.

### Fuzzers

As summarized in Zhang et al.'s survey, there are several open-source fuzzers for DL systems. The proposed DFuzzer technique can generate diverse seed queue aiming at helping these fuzzers detect more faults (or generate more adversarial inputs). In this study, we selected the following five representative fuzzers, in the evaluation of DFuzzer. 

1. DeepXplore (available at the repository: https://github.com/peikexin9/deepxplore) is the first white box fuzzer for system- atically testing DL systems and automatically identifying faults without manual labeling. It performs gradient as- cent to solve a joint optimization problem that maximizes both neuron coverage and the number of potentially faults. Three mutation strategies have been proposed for practitioners to use when applying DeepXplore.
2. DLFuzz (available at the repository: https://github.com/turned2670/DLFuzz) keeps mutating the input to maximize the neuron coverage. It can predict difference between the original input and the mutated input, without manual labeling effort. Four neuron selection strategies have been proposed for practitioners to adopt when using DLFuzz.
3. DeepHunter (available at the repository: https://github.com/hfeniser/DeepSmartFuzzer) performs the so-called “metamorphic mutation” to generate new test cases that preserve the correct semantics. Two seed selection strategies have been proposed for practitioners to use for implementing DeepHunter.
4. TensorFuzz (available at the repository: https://github.com/hfeniser/DeepSmartFuzzer) is a coverage-guided fuzzing method for neural networks, in which random mutations of inputs are guided by a coverage metric toward the goal of satisfying user-specified constraints, and an approximate nearest neighbor algorithms is proposed to provide this coverage metric.
5. DeepSmartFuzzer (available at the repository: https://github.com/hfeniser/DeepSmartFuzzer) employs Monte Carlo Tree Search to drive the coverage-guided search in the pursuit of high coverage.

In addition, the source code of DFuzzer is available at the repository: https://github.com/DFuzzer/DFuzzer.


