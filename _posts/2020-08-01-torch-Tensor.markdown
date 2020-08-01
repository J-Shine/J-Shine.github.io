---
layout: post
title:  "torch.Tensor"
date:   2020-08-01 19:00
categories: ["pytorch"]
author: "J-Shine"
---

# torch.Tensor
torch.Tensor는 pytorch에서 지원하는 다차원 행렬([Tensor]()) 자료형이다.<br>
Tensor의 원소들은 모두 한 가지의 자료형으로 통일된다.(boolean, int, float 등)<br>
pytorch를 돌릴 때는 항상 torch.Tensor 자료형을 쓰므로 이 자료형을 자유자재로 다룰 수 있어야 한다.<br><br>

# 종류
device에 따라 CPU와 GPU Tensor로 구분하여 사용하여야 한다. 나 같은 경우 노트북에 내장그래픽카드밖에 없기 때문에 항상 CPU 자료형을 사용하고 있다.<br>
자료형을 확인했을 때 torch.Tensor라고 표기되는 기본 자료형은 torch.FloatTensor이다.<br><br>
**실수 자료형** - torch.Tensor, torch.DoubleTensor, torch.HalfTensor, torch.BFloat16Tensor<br>
(HalfTensor와 BFloat16Tensor는 Tensor(float32)의 절반인 16bit짜리로, 전자는 담을 수 있는 숫자의 범위가 작지만 정확도가 높고, 후자는 정확도가 낮은 대신 담을 수 있는 숫자의 범위가 넓다.)<br><br>
**정수 자료형** - torch.ByteTensor, torch.CharTensor, torch.ShortTensor, torch.IntTensor, torch.LongTensor<br>
(ByteTensor와 CharTensor는 모두 8bit(1바이트)짜리로, 전자는 unsigned, 후자는 signed이다.)<br><br>
**논리 자료형** - torch.BoolTensor<br>
(BoolTensor도 8bit(1바이트)이지만 int가 아니라 bool 타입이다)<br><br>

# 생성
1.**torch.tensor()** - python에서의 list 등 sequence 자료형을 Tensor자료형으로 바꿀 수 있다. 데이터가 copy방식으로 생성된다.<br>
*torch.Tensor()와는 다르다(torch.Tensor()는 항상 torch.FloatTensor를 만든다.)*<br><br>
Parameter
  dtype(torch.dtype) - 데이터타입(선언하지 않으면 알아서 유추해서 정해짐)<br>
  device(torch.device) - cpu, cuda, mkldnn 등..(default=None으로 현재 device를 사용)<br>
  requires_grad(bool) - Tensor의 연산 기록 여부(torch.autograd 패키지에서 필요하다. default=False)<br>
  pin_memory(bool) - dataset이 CPU에 있는데 training은 GPU에서 할 경우 이 변수를 True로 바꿈으로써 속도를 향상시킬 수 있다.[설명](https://discuss.pytorch.org/t/when-to-set-pin- 
  memory-to-true/19723/3)(default=False)<br><br>
```python  
>>> torch.tensor([[0.1, 1.2], [2.2, 3.1], [4.9, 5.2]])
tensor([[ 0.1000,  1.2000],
        [ 2.2000,  3.1000],
        [ 4.9000,  5.2000]])

&#62;&#62;&#62; torch.tensor([0, 1])  # dtype을 지정하지 않았으므로 자동으로 유추해서 정해진다.
tensor([ 0,  1])

&#62;&#62;&#62; torch.tensor([[0.11111, 0.222222, 0.3333333]],
                 dtype=torch.float64,
                 device=torch.device('cuda:0'))  # torch.cuda.DoubleTensor 생성
tensor([[ 0.1111,  0.2222,  0.3333]], dtype=torch.float64, device='cuda:0')

&#62;&#62;&#62; torch.tensor(3.14159)  # 스칼라 텐서 생성(0차원 텐서)
tensor(3.1416)

&#62;&#62;&#62; torch.tensor([])  # 빈 텐서 생성 torch.Size([0])
tensor([])
```
<br><br>
2.**torch.zeros(\*size)** - 0으로 이루어진 torch.Tensor 생성 <br>
  **torch.ones(\*size)** - 1로 이루어진 torch.Tensor 생성 <br><br>
```python
&#62;&#62;&#62; torch.zeros(2, 3, 4)  # 크기가 2 X 3 X 4의 원소가 0인 torch.FloatTensor 생성
tensor([[[0., 0., 0., 0.],
         [0., 0., 0., 0.],
         [0., 0., 0., 0.]],

        [[0., 0., 0., 0.],
         [0., 0., 0., 0.],
         [0., 0., 0., 0.]]])
         
&#62;&#62;&#62; torch.ones(2, 3, 4)  # 크기가 2 X 3 X 4의 원소가 1인 torch.FloatTensor 생성
tensor([[[1., 1., 1., 1.],
         [1., 1., 1., 1.],
         [1., 1., 1., 1.]],

        [[1., 1., 1., 1.],
         [1., 1., 1., 1.],
         [1., 1., 1., 1.]]])
```
