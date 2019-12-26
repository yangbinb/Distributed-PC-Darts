# Distributed-PC-Darts
Distributed implementation of [PC-Darts](https://github.com/yuhuixu1993/PC-DARTS).This code is based on the implementation of [PC-Darts](https://github.com/yuhuixu1993/PC-DARTS), it is able to searching and training on multi-nodes&amp;multi-gpus with the method of distributed data parallel. Only the distributed search and retrain on Cifar10 implemented, you can modify it for your own datasets.

## Usage
### Distributed search on CIFAR10

1.one node two gpus

run on node0:

    python3 train_search_distributed.py --master_ip 127.0.0.1 --port 12345 --local_rank 0 --world_size 2 --gpu 0

run on node0:

    python3 train_search_distributed.py --master_ip 127.0.0.1 --port 12345 --local_rank 1 --world_size 2 --gpu 1

2.two nodes four gpus

run on node0:

    python3 train_search_distributed.py --master_ip x.x.x.x --port 12345 --local_rank 0 --world_size 4 --gpu 0

run on node0:

    python3 train_search_distributed.py --master_ip x.x.x.x --port 12345 --local_rank 1 --world_size 4 --gpu 1

run on node1:

    python3 train_search_distributed.py --master_ip x.x.x.x --port 12345 --local_rank 2 --world_size 4 --gpu 0

run on node1:

    python3 train_search_distributed.py --master_ip x.x.x.x --port 12345 --local_rank 3 --world_size 4 --gpu 1

### Distributed train on CIFAR10

1.one node two gpus

run on node0:

    python3 train_distributed.py --master_ip 127.0.0.1 --port 1234 --local_rank 0 --world_size 2 --gpu 0

run on node0:

    python3 train_distributed.py --master_ip 127.0.0.1 --port 1234 --local_rank 1 --world_size 2 --gpu 1

2.two nodes four gpus

run on node0:

    python3 train_distributed.py --master_ip x.x.x.x --port 1234 --local_rank 0 --world_size 4 --gpu 0

run on node0

    python3 train_distributed.py --master_ip x.x.x.x --port 1234 --local_rank 1 --world_size 4 --gpu 1

run on node1:

    python3 train_distributed.py --master_ip x.x.x.x --port 1234 --local_rank 2 --world_size 4 --gpu 0

run on node1:
       
    python3 train_distributed.py --master_ip x.x.x.x --port 1234 --local_rank 3 --world_size 4 --gpu 1

Replace x.x.x.x above with your master ip,for example, ip of node0, be sure the ip is right and accessible. You can also change the port with some other unused. Each command line start a process, 'world_size' stands for the number of processes,each process use one gpu.Run all the command line one-by-one, after all the processes on every node started, the distributed searching/training would begin. Models in every process would be saved normally, searching/training finished, you can choose the best one.

## Requirement

Python 3.6.7

Pytorch 1.1.0

## Related work

[PC-Darts](https://github.com/yuhuixu1993/PC-DARTS)
## Citation
    @inproceedings{
    xu2020pcdarts,
    title={{\{}PC{\}}-{\{}DARTS{\}}: Partial Channel Connections for Memory-Efficient Architecture Search},
    author={Yuhui Xu and Lingxi Xie and Xiaopeng Zhang and Xin Chen and Guo-Jun Qi and Qi Tian and Hongkai Xiong},
    booktitle={International Conference on Learning Representations},
    year={2020},
    url={https://openreview.net/forum?id=BJlS634tPr}
    }

