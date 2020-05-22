# Nengo

## Nengo 소개 

Nengo는 매우 큰 구조의 신경망 모델을 구축하고, 시뮬레이션 할 수 있는 파이썬 라이브러리입니다. Nengo를 이용하면 정교한 발화 및 비-발화 기반의 뉴런 시뮬레이션을 단 몇 줄의 코드로 구축할 수 있습니다.

```python
import nengo
import numpy as np
import matplotlib.pyplot as plt

with nengo.Network() as net:
    sin_input = nengo.Node(output=np.sin)
    # 사인파 입력을 나타내 100개의 뉴런을 생성합니다.
    sin_ens = nengo.Ensemble(n_neurons=100, dimensions=1)
    nengo.Connection(sin_input, sin_ens)
    # 사인파 입력의 제곱을 나타내는 100개의 뉴런을 생성합니다.
    sin_squared = nengo.Ensemble(n_neurons=100, dimensions=1)
    nengo.Connection(sin_ens, sin_squared, function=np.square)
    # sin_squared를 디코딩한 결과를 저장합니다.
    squared_probe = nengo.Probe(sin_squared, synapse=0.01)

with nengo.Simulator(net) as sim:
    sim.run(5.0)
plt.plot(sim.trange(), sim.data[squared_probe])
```

Nengo는 확장성과 유연성이 뛰어납니다. 직접 뉴런의 타입과 학습 규칙을 정의할 수도 있고, 하드웨어로부터 입력을 직접 받도록 구성할 수도 있고, 매우 깊은 신경망을 구축하여 실행할 수도 있고, 완전히 다른 신경망 시뮬레이터 혹은 뉴로모픽 하드웨어를 이용할 수도 있습니다.

* Getting started
  * [설치](nengo/undefined/)
* User guide
* 


