# 無料・商用利用可なオープンソースの大規模言語モデル Dolly 2.0(dolly-v2-12b) を Windowsで試してみた

- **Windows** 環境で [Dolly 2.0](https://huggingface.co/databricks/dolly-v2-12b) を試す方法

  - Linux 環境(Ubuntu 22) で試す方法は [こちら](https://qiita.com/riversun/items/7c45580f1a098b041528)

# 実験環境

- OS: **Windows 11**　(WSL2 などは使わないスッピンの Windows で OK)
- GPU: **RTX 3090**
- Python: **Anaconda3 py310_2023.03-0(64-bit)**


## STEP 1: Anaconda 仮想環境を作る

dolly-v2 を試すために **env-dolly-v2** という名前で Anaconda 仮想環境を作り python 3.10.10 をインストールする

**conda を最新版にしておく**

```
conda update -n base -c defaults conda --yes
```

**env-dolly-v2** という仮想環境を作り、 python をインストールする

```
conda create --yes -n env-dolly-v2
conda activate env-dolly-v2
conda install python=3.10.10 --yes
```

**pipを最新にしておく**

```
python -m pip install --upgrade pip
```

## STEP 2: 必要パッケージのインストール

以下のように、必要なパッケージをインストールしていく。

```
pip install appdirs Click~=7.0 protobuf~=3.19.0 psutil PyYAML packaging fsspec huggingface-hub pandas tqdm entrypoints jsonschema toolz attrs six dill~=0.3.0
pip install beautifulsoup4
pip install gdown
pip install wandb
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu117
pip install accelerate transformers
pip install fastapi uvicorn
```


## STEP 3: ソースコードを記述する

ソースコードをクローンする

```
https://github.com/riversun/dolly-v2-on-windows-ja.git
```

## STEP 4: チャットサーバーを起動する

```
cd dolly-v2-on-windows
python main.py
```


## STEP 5: Dolly 2.0 とお話しする

サーバーが起動した後、ブラウザで http://localhost:8001 にアクセスすると、チャットウィンドウが開くので Dolly 2.0 を試すことができる!


# Appendix

## conda コマンド一覧

**仮想環境一覧**

```
conda-env list
```

**仮想環境の deactivate**


```
conda deactivate
```

**仮想環境の削除**


```
conda remove -n env-dolly-v2 --all --yes
```
