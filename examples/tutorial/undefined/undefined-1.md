# 두개의 뉴런

이 데모 코드는 상호 보완 관계의 뉴런 쌍을 어떻게 구축하고 조절하는지 보여줍니다.

이 뉴런들은 LIF\(leaky integrate-and-fire\) 뉴런들입니다. 뉴런의 튜닝 설정을 사용해서 하나의 뉴런은 'on'이고, 다른 뉴런은 'off'입니다.   

첫번째 뉴런은 양의 입력값에 따라 증가할 것이고, 다른 뉴런은 감소할 것입니다. 이것은  하나의 스칼라 값을 논리적으로 표현할 수 있는 가장 단순한 집단으로 볼 수 있습니다.

```text
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np

import nengo
from nengo.dists import Uniform
from nengo.utils.matplotlib import rasterplot
```

### 1 단계: 뉴런의 생성

```text
model = nengo.Network(label='Two Neurons')
with model:
    neurons = nengo.Ensemble(
        # 1D scalar 값으로 표현
        2, dimensions=1, 
        # Set the intercepts at .5
        intercepts=Uniform(-.5, -.5),  
        # Set the max firing rate at 100hz
        max_rates=Uniform(100, 100),  
        # One 'on' and one 'off' neuron
        encoders=[[1], [-1]])  
```

### 2 단계: Create input for the model

Create an input node generating a sine wave.

```text
with model:
    sin = nengo.Node(lambda t: np.sin(8 * t))
```

### 3 단: Connect the network elements

```text
with model:
    nengo.Connection(sin, neurons, synapse=0.01)
```

### 4 단계: Probe outputs

Anything that is probed will collect the data it produces over time, allowing us to analyze and visualize it later.

