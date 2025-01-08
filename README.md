# KVcache

## 安装步骤

### 解压文件

```bash
unzip vlm-kvcache.zip -d ./
cd vlm-kvcache
```
### 安装 LLaVA
```bash
conda create -n KVcache python=3.10 -y
conda activate KVcache
cd LLaVA
pip install --upgrade pip  # 启用 PEP 660 支持
pip install -e .
cd ..
```
### 安装 Lmms
```bash
cd lmms-eval
pip install -e .
cd ..
```
### 安装 FlashAttention
```bash
pip install flash_attn-2.7.1.post4+cu12torch2.1cxx11abiFALSE-cp310-cp310-linux_x86_64.whl
```
### 替换当前 Conda 环境中的 Transformers
1.找到 Transformers 路径
```bash
pip show transformers

输出示例：
Location: /data/luzeyi/.conda/envs/KVcache/lib/python3.10/site-packages
```
2.删除 Conda 版本
```bash
rm -rf /data/luzeyi/.conda/envs/KVcache/lib/python3.10/site-packages/transformers
```
3.替换
```bash
cp -r ./transformers /data/luzeyi/.conda/envs/KVcache/lib/python3.10/site-packages/transformers
```
4.安装替换版本
```bash
pip install transformers==4.47.1
```

### 执行可执行文件
```bash
cd lmms-eval/sh
# 执行可执行文件，后一个参数为 GPU 序号
./winking10%coco_cap16.sh 2
```
文件命名说明
*文件名格式为 [方法+保留kv百分比+测试数据集+保留头个数]

