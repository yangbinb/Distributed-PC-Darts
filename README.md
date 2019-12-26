# Distributed-PC-Darts
Distributed implementation of PC-Darts.This code is based on the implementation of PC-Darts, it is able to searching and training on multi-nodes&amp;multi-gpu with the method of distributed data parallel.I only realized distributed search and retrain on Cifar10,you can modify it for your own datasets.

## Usage
Distributed search on CIFAR10

1.one node two gpus

node0:

''' 
    python3 train_search_distributed.py --master_ip 127.0.0.1 --port 12345 --local_rank 0 --world_size 2 --gpu 0
'''

node0:

'''
    python3 train_search_distributed.py --master_ip 127.0.0.1 --port 12345 --local_rank 1 --world_size 2 --gpu 1
'''

2.two nodes four gpus

node0:

'''
python3 train_search_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 0 --world_size 4 --gpu 0
'''

node0:

'''
python3 train_search_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 1 --world_size 4 --gpu 1
'''

node1:

'''
python3 train_search_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 2 --world_size 4 --gpu 0
'''

node1:

'''
python3 train_search_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 3 --world_size 4 --gpu 1
'''

Distributed train on CIFAR10

1.one node two gpus

node0:

'''
python3 train_distributed.py --master_ip 127.0.0.1 --port 12345 --local_rank 0 --world_size 2 --gpu 0
'''

node0:

'''
python3 train_distributed.py --master_ip 127.0.0.1 --port 12345 --local_rank 1 --world_size 2 --gpu 1
'''

2.two nodes four gpus

node0:

'''
python3 train_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 0 --world_size 4 --gpu 0
'''

node0:

'''
python3 train_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 1 --world_size 4 --gpu 1
'''

node1:

'''
python3 train_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 2 --world_size 4 --gpu 0
'''

node1:

'''
python3 train_distributed.py --master_ip xxx.xxx.xxx.xxx --port 12345 --local_rank 3 --world_size 4 --gpu 1
'''

xxx.xxx.xxx.xxx is your master ip,for example ip of node0.Models of every process would be saved normally, you can choose the best one.

## Requirement

Python 3.6.7

Pytorch 1.1.0

## Related work

PC-Darts(https://github.com/yuhuixu1993/PC-DARTS)

## Reference

@inproceedings{
xu2020pcdarts,
title={{\{}PC{\}}-{\{}DARTS{\}}: Partial Channel Connections for Memory-Efficient Architecture Search},
author={Yuhui Xu and Lingxi Xie and Xiaopeng Zhang and Xin Chen and Guo-Jun Qi and Qi Tian and Hongkai Xiong},
booktitle={International Conference on Learning Representations},
year={2020},
url={https://openreview.net/forum?id=BJlS634tPr}
}
