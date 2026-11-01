# 第2回 解答

## 演習

- 使ったモデル・設定（`result.json` の `config` から）：{
    "base_model": "Qwen/Qwen3.5-0.8B",
    "revision": "2fc06364715b967f1860aea9cf38778875588b17",
    "seed": 42,
    "num_train_epochs": 20,
    "warmup_steps": 6,
    "lr": 0.0002,
    "lora_r": 16,
    "lora_alpha": 32,
    "max_seq_len": 512,
    "max_new_tokens": 96,
    "gen": {
      "do_sample": false
    }}
- 自分で学習を実行したか（`executed_training_myself`）：はい（実行できた範囲：一通り　）
- 学習前：`format_rate` =　0.09523809523809523 / `content_rate` =　0.0
- 学習後：`format_rate` =　1.0 / `content_rate` =　0.9047619047619048
- 退行した質問：なし
- 学習後に残った失敗と、その型（根拠なしの質問に断定した / 根拠ありの質問に確認要求で逃げた / 形式の崩れ）：内容の不一致が２件、根拠なしの質問に断定した
- 知識を問う質問（セクション 6）の結果（学習前の分類 → 学習後の分類）と気づいたこと：学習前では全件がformat_errorとなっているが、学習後ではneeds_reviewに改善されたものとassertedで断定する2つに分かれた
- 学習で変わったこと・変わらなかったこと：format_rate,content_rateが大幅に改善。

## 宿題

- 取り組んだレベル：基礎
- 変えた設定やデータ：num_train_epochsを20から50に変更
- 結果（比較表や数字）：format_rate,content_rateに変化なし。最終lossは0.013814から0.010845と良化、学習時間は251秒から626秒と長くなった。
- ファインチューニングが向く場面・向かない場面についての考察：format_rate,content_rate共に改善傾向にあるが、特にformat_rateが1.0となったことから、形式を遵守させたい場合にファインチューニングが向いていると考えられる。一部の質問では、学習後に根拠なし断定をしていることから、根拠データが不足している場合にはファインチューニングが向かないと考えられる。
