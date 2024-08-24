### uv を触ってみた

- M1 Mac
- Sonoma 14.6.1

- [uv の公式ドキュメント](https://docs.astral.sh/uv/#highlights)

```sh
# install
brew install uv

# version 確認
uv --version

# プロジェクトファイル作成に必要な設定ファイル作成
touch pyproject.toml

cat <<EOF > pyproject.toml
[project]
name = "example"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.12"
dependencies = []
EOF

# 初期プロジェクトファイル作成
uv init example

# プロジェクトフォルダに移動
cd example

# 仮想環境の作成
uv venv --python 3.12.5

# 仮想環境のアクティベート
source .venv/bin/activate

# ライブラリの追加
uv add numpy

# サンプルコードの実行
uv run src/example/sample.py
```

```python: sample.py
import numpy as np

if __name__ == "__main__":
    sample_num = np.random.randint(1, 10)
    print(f"{sample_num} samples are generated.")
```

### existed という既存のディレクトリの環境を uv で作る
```sh
# 既存の　existed フォルダに、Python のバージョンを指定して仮想環境を作る
uv init --virtual .venv --name existed --python 3.12.5

# Python のバージョン確認
uv run python --version

# ライブラリのインストール
uv add -r requirements.txt

# ファイルの実行
uv run sample.py
```
