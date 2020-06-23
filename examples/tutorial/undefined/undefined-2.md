# 많은 수의 신경세포

이 데모는 많은 수를 가지는 신경세 집단을 어떻게 구축하고 조절하는지를 보여줍니다.

아래 예제는 100개의 leaky integrate-and fire \(LIF\) 신경세포를 표현합니다. 신경세포의 활성은 무작위로 조절됩니다.

신경세포로의 입력은 사인파 \(sine wave\)를 사용함으로써, 입력의 증가와 감소에 따른 영향을 관찰할 수 있습니다. 신경세포 집단에서, 신경세포는 단일 스칼라 값을 아주 잘 표현할 수 있습니다. 이는 입력 그래프와 신경세포의 활성 그래프가 잘 일치한다는 사실로 알 수 있습니다.

```python
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np

import nengo
from nengo.utils.ensemble import sorted_neurons
from nengo.utils.matplotlib import rasterplot
```

## 스텝 1: 신경세포 집단 생성

우리의 모델은 다수의 신경세포로 구성된 단일 신경세포 집단으로 이루어져 있습니다.

```python
model = nengo.Network(label='Many Neurons')
with model:
    # 우리의 모델은 100개의 LIF 신경세포 모델로 구성되어 있으며,
    # 1차원으로 신호를 표현합니다.
    A = nengo.Ensemble(100, dimensions=1)
```



