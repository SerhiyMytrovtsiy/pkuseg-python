# pkuseg-python��һ����׼ȷ�ȵ����ķִʹ��߰�
pkuseg-python�����ã�֧�ֶ�����ִʣ��ڲ�ͬ����������϶��������˷ִʵ�׼ȷ�ʡ�

## Ŀ¼
* [��Ҫ����](#��Ҫ����)
* [����Ͱ�װ](#����Ͱ�װ)
* [����ִʹ��߰������ܶԱ�](#����ִʹ��߰������ܶԱ�)
* [ʹ�÷�ʽ](#ʹ�÷�ʽ)
* [�������](#�������)
* [��������ʵ��](#��������ʵ��)
* [����](#����)

## ��Ҫ����

pkuseg���ɱ�����ѧ���Լ��������ѧϰ�о��������Ƴ���һ��ȫ�µ����ķִʹ��߰���pkuseg�������¼����ص㣺

1. �߷ִ�׼ȷ�ʡ�����������ķִʹ��߰������ǵĹ��߰��ڲ�ͬ����������϶��������˷ִʵ�׼ȷ�ȡ��������ǵĲ��Խ����pkuseg�ֱ���ʾ�����ݼ���MSRA��CTB8���Ͻ�����79.33%��63.67%�ķִʴ����ʡ�
2. ������ִʡ�����ѵ���˶��ֲ�ͬ����ķִ�ģ�͡����ݴ��ִʵ������ص㣬�û��������ɵ�ѡ��ͬ��ģ�͡�
3. ֧���û���ѵ��ģ�͡�֧���û�ʹ��ȫ�µı�ע���ݽ���ѵ����

## ����Ͱ�װ
1. ͨ��pip����(�Դ�ģ���ļ�)
	```
	pip install pkuseg
	֮��ͨ��import pkuseg������
	```
2. ��github����(��Ҫ����ģ���ļ�����[Ԥѵ��ģ��](#Ԥѵ��ģ��))
	```
	��pkuseg�ļ��ŵ�Ŀ¼�£�ͨ��import pkusegʹ��
	ģ����Ҫ���ػ��Լ�ѵ����
	```

## ����ִʹ��߰������ܶԱ�
����ѡ��THULAC����ͷִʵȹ��ڴ���ִʹ��߰���pkuseg�����ܱȽϡ�����ѡ��Linux��Ϊ���Ի���������������(MSRA)�ͻ�����ı�(CTB8)�����϶Բ�ͬ���߰�������׼ȷ�ʲ��ԡ�����ʹ���˵ڶ�����ʺ���ִ���������ṩ�ķִ����۽ű������������£�


|MSRA | F-score| Error Rate |
|:------------|------------:|------------:|
| jieba |81.45 | 18.55
| THULAC | 85.48 |  14.52
| pkuseg | **96.75 (+13.18%)**| **3.25 (-77.62%)**


|CTB8 | F-score | Error Rate|
|:------------|------------:|------------:|
|jieba|79.58|20.42
|THULAC|87.77|12.23
|pkuseg| **95.64 (+8.97%)**|**4.36 (-64.35%)**


## ʹ�÷�ʽ
1. ����ʾ��
	```
	����ʾ��1		ʹ��Ĭ��ģ�ͼ�Ĭ�ϴʵ�ִ�
	import pkuseg
	seg = pkuseg.pkuseg()				#��Ĭ�����ü���ģ��
	text = seg.cut('�Ұ������찲��')	#���зִ�
	print(text)
	```
	```
	����ʾ��2		�����û��Զ���ʵ�
	import pkuseg
	lexicon = ['������ѧ', '�����찲��']	#ϣ���ִ�ʱ�û��ʵ��еĴʹ̶����ֿ�
	seg = pkuseg.pkuseg(user_dict=lexicon)	#����ģ�ͣ������û��ʵ�
	text = seg.cut('�Ұ������찲��')		#���зִ�
	print(text)
	```
	```
	����ʾ��3
	import pkuseg
	seg = pkuseg.pkuseg(model_name='./ctb8')	#�����û��Ѿ����غ���ctb8��ģ�Ͳ�������'./ctb8'Ŀ¼�£�ͨ������model_name���ظ�ģ��
	text = seg.cut('�Ұ������찲��')			#���зִ�
	print(text)
	```
	```
	����ʾ��4
	import pkuseg
	pkuseg.test('input.txt', 'output.txt', nthread=20)	#��input.txt���ļ��ִ������output.txt�У�ʹ��Ĭ��ģ�ͺʹʵ䣬��20������
	```
	```
	����ʾ��5
	import pkuseg
	pkuseg.train('msr_training.utf8', 'msr_test_gold.utf8', './models', nthread=20)	#ѵ���ļ�Ϊ'msr_training.utf8'�������ļ�Ϊ'msr_test_gold.utf8'��ģ�ʹ浽'./models'Ŀ¼�£���20������ѵ��ģ��
	```
2. ����˵��
	```
	pkuseg.pkuseg(model_name='msra', user_dict='safe_lexicon')
	model_name		ģ��·����Ĭ����'msra'��ʾ����Ԥѵ���õ�ģ��(����pip���ص��û�)���û��������Լ����ػ�ѵ����ģ�����ڵ�·����model_name='./models'��
	user_dict		�����û��ʵ䡣Ĭ��Ϊ'safe_lexicon'��ʾ�����ṩ��һ�����Ĵʵ�(��pip)���û����Դ���һ�����������Զ��嵥�ʵĵ�������
	```
	```
	pkuseg.test(readFile, outputFile, model_name='msra', user_dict='safe_lexicon', nthread=10)
	readFile		�����ļ�·��
	outputFile		����ļ�·��
	model_name		ͬpkuseg.pkuseg
	user_dict		ͬpkuseg.pkuseg
	nthread			����ʱ���Ľ�����
	```
	```
	pkuseg.train(trainFile, testFile, savedir, nthread=10)
	trainFile		ѵ���ļ�·��
	testFile		�����ļ�·��
	savedir			ѵ��ģ�͵ı���·��
	nthread			ѵ��ʱ���Ľ�����
	```


### Ԥѵ��ģ��
�ִ�ģʽ�£��û���Ҫ����Ԥѵ���õ�ģ�͡������ṩ�������ڲ�ͬ����������ѵ���õ���ģ�ͣ����ݾ�����Ҫ���û�����ѡ��ͬ��Ԥѵ��ģ�͡������Ƕ�Ԥѵ��ģ�͵�˵����

MSRA: ��MSRA���������ϣ���ѵ����ģ�͡��°汾������õ��Ǵ�ģ�͡�[���ص�ַ](https://pan.baidu.com/s/1twci0QVBeWXUg06dK47tiA)

CTB8: ��CTB8�������ı��������ı��Ļ�������ϣ���ѵ����ģ�͡�[���ص�ַ](https://pan.baidu.com/s/1DCjDOxB0HD2NmP9w1jm8MA)

WEIBO: ��΢���������ı����ϣ���ѵ����ģ�͡�[���ص�ַ](https://pan.baidu.com/s/1QHoK2ahpZnNmX6X7Y9iCgQ)

���У�MSRA������[�ڶ�����ʺ���ִ��������](http://sighan.cs.uchicago.edu/bakeoff2005/)�ṩ��CTB8������[LDC](https://catalog.ldc.upenn.edu/ldc2013t21)�ṩ��WEIBO������[NLPCC](http://tcci.ccf.org.cn/conference/2016/pages/page05_CFPTasks.html)�ִʱ����ṩ��


## ��ԴЭ��
1. pkuseg����������ѧ���о�������ҵ�Լ����������о�Ŀ����ѿ���Դ���롣
2. ���л���������⽫pkuseg������ҵĿ�ģ��뷢�ʼ���xusun@pku.edu.cnǢ̸�������Э�顣
3. ��ӭ�Ըù��߰�����κα�������ͽ��飬�뷢�ʼ���jingjingxu@pku.edu.cn��

## �������
��ʹ�ô˹��߰����������������£�
* Xu Sun, Houfeng Wang, Wenjie Li. Fast Online Training with Frequency-Adaptive Learning Rates for Chinese Word Segmentation and New Word Detection. ACL. 253�C262. 2012 

```
@inproceedings{DBLP:conf/acl/SunWL12,
author = {Xu Sun and Houfeng Wang and Wenjie Li},
title = {Fast Online Training with Frequency-Adaptive Learning Rates for Chinese Word Segmentation and New Word Detection},
booktitle = {The 50th Annual Meeting of the Association for Computational Linguistics, Proceedings of the Conference, July 8-14, 2012, Jeju Island, Korea- Volume 1: Long Papers},
pages = {253--262},
year = {2012}}
```


* Jingjing Xu, Xu Sun. Dependency-based Gated Recursive Neural Network for Chinese Word Segmentation. ACL 2016: 567-572
```
@inproceedings{DBLP:conf/acl/XuS16,
author = {Jingjing Xu and Xu Sun},
title = {Dependency-based Gated Recursive Neural Network for Chinese Word Segmentation},
booktitle = {Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics, {ACL} 2016, August 7-12, 2016, Berlin, Germany, Volume 2: Short Papers},
year = {2016}}
```

## ��������ʵ��
pkuseg��C#�棩��
https://github.com/lancopku/PKUSeg-csharp

## ����

Ruixuan Luo ���������,  Jingjing Xu��������,  Xu Sun ������
