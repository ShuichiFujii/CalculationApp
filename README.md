# 計算器（cal_app）

![Python](https://img.shields.io/badge/Python-3.x-blue)
![CLI](https://img.shields.io/badge/interface-CLI-lightgrey)
![Test](https://img.shields.io/badge/test-unittest-green)
![Status](https://img.shields.io/badge/status-in_progress-yellow)

## Overview

Python で実装した CLI ベースの電卓アプリです。

入力された数式をそのまま計算するのではなく、字句解析・構文解析・評価という流れに分けて処理しています。  
また、抽象構文木を用いて数式を扱うことで、計算処理の流れを理解しやすい構成にしています。

## Demo

![demo](docs/calculation_demo.gif)

## Features

- CLI 上で数式を入力して計算できる
- 四則演算に対応
- 抽象構文木（AST）を用いて数式を評価
- 字句解析・構文解析・評価の処理を分離
- `exit` または `quit` を入力すると終了できる
- unittest によるテストを用意

## Tech Stack

- Python 3.12.7

## Setup

```bash
git clone https://github.com/ShuichiFujii/cal_app.git
cd cal_app
```

外部ライブラリは現在使用していません。

## Usage

```bash
python3 -m api.main
```

数式を入力して計算します。

```bash
Enter an expression: 1 + 2 * 3
Answer >>> 7
```

終了する場合は、次を入力します。

```bash
exit
```

## Tests

以下のコマンドでテストを実行できます。

```bash
python3 -m unittest tests.testcase
```

## Project Structure

```text
cal_app/
├── api/
│   └── main.py          # CLI のエントリーポイント
├── app/
│   ├── engine.py        # 数式評価全体を扱う処理
│   ├── lexer.py         # 入力された数式をトークンに分割
│   ├── parser.py        # トークン列を解析して AST を構築
│   └── evaluator.py     # AST を評価して計算結果を返す
├── tests/
│   └── testcase.py      # unittest によるテスト
└── README.md
```

## Design / Implementation Notes

このプロジェクトでは、電卓の処理を複数の役割に分けて実装しています。

主な処理の流れは以下の通りです。

1. 入力された数式を受け取る
2. lexer で数式をトークンに分割する
3. parser でトークン列を解析し、AST を構築する
4. evaluator で AST を評価する
5. 計算結果を CLI に表示する

各処理を分けることで、数式がどのように解釈され、どのように計算されるのかを追いやすくしています。  
また、処理ごとの責務を分離することで、テストや機能追加がしやすい構成にしています。

## Future Improvements

- 不正な数式に対するエラーメッセージを改善する
- 小数の計算に対応する（誤差の処理の考慮）
- 累乗などの演算子を追加する
- テストケースを増やす
- GitHub Actions を導入し、テストを自動実行する

## Author

- [Shuichi Fujii](https://github.com/ShuichiFujii)
- [Qiita](https://qiita.com/embermaverick05)
