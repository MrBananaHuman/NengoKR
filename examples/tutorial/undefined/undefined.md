# 단일 신경세포

이 데모 코드는 하나의 leaky integrate-and-fire \(LIF\) 신경세포를 어떻게 구축하고 조절하는지 보여줍니다. LIF 신경세포는 단순하며, 기본적인 뉴런의 모델입니다. Nengo에서는 하나의 신경세포를 구성하더라도, 뉴런의 집단\(popluation\)에 속해있는 것으로 표현합니다.

```python
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np

import nengo
from nengo.utils.matplotlib import rasterplot
```

### 1 단계: 신경세포의 생성

```python
from nengo.dists import Uniform

model = nengo.Network(label='A Single Neuron')
with model:
    neuron = nengo.Ensemble(
        1,
        dimensions=1,  # 1D sclar 값으로 표
        # Intercept를 0.5로 설정
        intercepts=Uniform(-.5, -.5),
        # 신경세포의 최대 발화 빈도를 100hz로 설정
        max_rates=Uniform(100, 100),
        # 신경세포의 발화는 양수의 입력에 따라 증가하도록 설
        encoders=[[1]])
```

### 2 단계: 모델로 입력을 전달

코사인파를 만들어내는 입력 노드를 생성합니다.

```python
with model:
    cos = nengo.Node(lambda t: np.cos(8 * t))
```

### 3 단계: 신경망의 요소들을 연결

```python
with model:
    # 입력 노드와 신경세포를 연
    nengo.Connection(cos, neuron)
```

### 4 단계: Probe 객체 생성

Probe 객체를 통해 원하는 데이터를 시뮬레이션 시간 내내 수집할 수 있으며, 이를 통해 나중에 시각화 및 데이터 분석이 가능합니다.

```python
with model:
    # 입력값 수
    cos_probe = nengo.Probe(cos)
    # 신경세포의 발화 정보 수집
    spikes = nengo.Probe(neuron.neurons)
    # 신경세포의 전압값 변화 수집 
    voltage = nengo.Probe(neuron.neurons, 'voltage')
    # Spikes filtered by a 10ms post-synaptic filter
    filtered = nengo.Probe(neuron, synapse=0.01)
```



