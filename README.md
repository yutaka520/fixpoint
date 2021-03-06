# フィックスポイント課題
 
フィックスポイントのプログラミング試験回答のソースコードをここにおきます。

# フォルダ構成
 
フォルダ構成は以下のようになっています。
```bash
└── opt
    ├── data
    │   ├── __pycache__
    │   │   └── data_handler.cpython-37.pyc
    │   ├── data_handler.py
    │   └── serverlog.txt
    ├── question1
    │   └── output_log.py
    ├── question2
    │   ├── output_log.py
    │   └── run.sh
    ├── question3
    │   ├── output_log.py
    │   └── run.sh
    └── question4
        ├── output_log.py
        └── run.sh
```

全ての課題に共通な監視ログデータ
```bash
opt/data/serverlog.txt
```

全ての課題に共通で使用するプログラム
```bash
opt/data/data_handler.py
```

# Requirement
 
実行したdockerのバージョンは以下である。
 
* engine 19.03.12
* compose 1.27.2

# 使い方

まず、以下のコマンドでgithubからソースコードをダウンロードします。
```bash
git clone https://github.com/yutaka520/fixpoint.git
```

ダウンロードしたフォルダに移動し、以下のコマンドでdocker仮想環境を立ち上げます。
```bash
docker-compose up -d --build
```

docker仮想環境に入ります。
```bash
docker-compose exec python3 bash
```

それぞれの課題の実行までの手順は以下のようになります。
## 課題1の場合
```bash
cd /root/opt/question1/
python output_log.py
```
## 課題2の場合
```bash
cd /root/opt/question2/
bash run.sh
```
## 課題3の場合
```bash
cd /root/opt/question3/
bash run.sh
```
## 課題4の場合
```bash
cd /root/opt/question4/
bash run.sh
```
使用後は、exitで仮想環境を抜け、以下のコマンドで終了します。
```bash
docker-compose down
```

# 実行結果
それぞれの課題の実行結果は以下のようになった
## 課題1

```bash
ipアドレス: 10.20.30.1
故障期間
2020年10月19日 13時33分24秒 ~ 2020年10月19日 13時33分26秒
2020年10月19日 13時33分27秒 ~ 2020年10月19日 13時33分28秒
2020年10月19日 13時33分32秒 ~ 

ipアドレス: 10.20.30.2
故障期間
2020年10月19日 13時33分29秒 ~ 2020年10月19日 13時33分30秒
2020年10月19日 13時33分31秒 ~ 2020年10月19日 13時33分34秒
2020年10月19日 13時33分35秒 ~ 2020年10月19日 13時33分39秒

ipアドレス: 192.168.1.1
故障期間
なし

ipアドレス: 192.168.1.2
故障期間
なし
```

## 課題2

```bash
ipアドレス: 10.20.30.1
故障期間
2020年10月19日 13時33分32秒 ~ 

ipアドレス: 10.20.30.2
故障期間
2020年10月19日 13時33分31秒 ~ 2020年10月19日 13時33分34秒
2020年10月19日 13時33分35秒 ~ 2020年10月19日 13時33分39秒

ipアドレス: 192.168.1.1
故障期間
なし

ipアドレス: 192.168.1.2
故障期間
なし
```

## 課題3

```bash
ipアドレス: 10.20.30.1
故障期間
2020年10月19日 13時33分32秒 ~ 

過負荷期間
2020年10月19日 13時31分24秒 ~ 2020年10月19日 13時33分26秒
2020年10月19日 13時31分24秒 ~ 

ipアドレス: 10.20.30.2
故障期間
2020年10月19日 13時33分31秒 ~ 2020年10月19日 13時33分34秒
2020年10月19日 13時33分35秒 ~ 2020年10月19日 13時33分39秒

過負荷期間
2020年10月19日 13時33分25秒 ~ 2020年10月19日 13時33分30秒
2020年10月19日 13時33分25秒 ~ 2020年10月19日 13時33分34秒
2020年10月19日 13時33分25秒 ~ 2020年10月19日 13時33分39秒

ipアドレス: 192.168.1.1
故障期間
なし

過負荷期間
2020年10月19日 13時31分34秒 ~ 

ipアドレス: 192.168.1.2
故障期間
なし

過負荷期間
2020年10月19日 13時31分35秒 ~ 
```

## 課題4

```bash
サブネット
サブネットアドレス: 10.20.0.0
故障期間
2020年10月19日 13時33分35秒 ~ 2020年10月19日 13時33分39秒

サブネットアドレス: 192.168.1.0
故障期間
なし

ipアドレス: 10.20.30.1
故障期間
なし

過負荷期間
2020年10月19日 13時31分24秒 ~ 2020年10月19日 13時33分26秒

ipアドレス: 10.20.30.2
故障期間
2020年10月19日 13時33分31秒 ~ 2020年10月19日 13時33分34秒

過負荷期間
2020年10月19日 13時33分25秒 ~ 2020年10月19日 13時33分30秒
2020年10月19日 13時33分25秒 ~ 2020年10月19日 13時33分34秒

ipアドレス: 192.168.1.1
故障期間
なし

過負荷期間
2020年10月19日 13時31分34秒 ~ 

ipアドレス: 192.168.1.2
故障期間
なし

過負荷期間
2020年10月19日 13時31分35秒 ~ 
```

# 課題仕様について
課題4では、サブネット故障出力についての出力が課題になっていたが、サブネットの故障期間中である、サブネット内ipアドレス毎の不具合は出力する必要性を感じなかったため、除外して出力するようにした。  
  
例) サブネットが10:00 - 10:01まで壊れていた場合  
そのサブネットに属するipアドレスの10:00 - 10:01までのログは除外し、各ip毎のエラーログを出力した。
  
サーバが故障している期間も過負荷としてカウントしている。
