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

```c++  
li.push_front(10);
```
-> list의 맨 앞에 10을 추가한다.이 때 iterator가 가리키는 원소는 변하지 않는다.<br><br> 
