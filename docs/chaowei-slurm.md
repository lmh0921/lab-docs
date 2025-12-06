我们的超微服务器slurm示例

```sh
#!/bin/bash
#SBATCH -J demo-v100-1gpu             # 作业名
#SBATCH -p v100                        # 分区
#SBATCH --gres=gpu:v100:1              # 申请 1 张 V100
#SBATCH -c 4                           # CPU 核
#SBATCH --mem=16G                      # 内存
#SBATCH -t 02:00:00                    # 运行时间
#SBATCH -o %x-%j.out              # 日志输出到 logs/作业名-作业号.out
```

文件名：run_v100_2gpu_ddp.sh

```sh
#!/bin/bash
#SBATCH -J demo-v100-2gpu-ddp
#SBATCH -p v100
#SBATCH --gres=gpu:v100:2          # 2 张 V100
#SBATCH -N 1                        # 单机
#SBATCH --ntasks=2                  # 2 个任务（每任务占 1 张卡）
#SBATCH -c 4                        # 每任务 4 CPU
#SBATCH --mem=32G
#SBATCH -t 04:00:00
#SBATCH -o %x-%j.out
```

3) 单卡 2080Ti（推理/小训练）

文件名：run_rtx_1gpu.sh

```sh
#!/bin/bash
#SBATCH -J demo-rtx-1gpu
#SBATCH -p rtx
#SBATCH --gres=gpu:2080ti:1
#SBATCH -c 4
#SBATCH --mem=12G
#SBATCH -t 01:00:00
#SBATCH -o %x-%j.out
```

