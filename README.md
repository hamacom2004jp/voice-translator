# Voice Translator App

PCのスピーカーの音声を翻訳するアプリケーションです。
顔認識モデルのダウンロードのためにインターネットに接続しますが、それ以降はローカルで動作しデータのアップロードなどは行いません。


## 動作確認OS
- `Windows 10 Pro`
- `Windows 11 Pro`

## ビルド方法

### SoundCardのビルド
```
git clone https://github.com/bastibe/SoundCard.git
cd SoundCard
python -m venv .venv
.venv\Scripts\activate
python.exe -m pip install --upgrade pip setuptools wheel
python setup.py bdist_wheel
```
- setup.pyのビルドで以下のエラーが発生する場合は、setup.pyを修正してあげる必要があります。
- エラー：```UnicodeDecodeError: 'cp932' codec can't decode byte 0x97 in position 3341: illegal multibyte sequence```
- 修正前:```long_description=open('README.rst').read(),```
- 修正後:```long_description=open('README.rst', encoding="utf-8").read(),```
- ```dist/SoundCard-0.4.2-py3-none-any.whl```ファイルをvoice-translatorのビルド環境構築にコピーする

### voice-translatorのビルド環境構築
```
git clone https://github.com/hamacom2004jp/voice-translator.git
cd voice-translator
python -m venv .venv
.venv\Scripts\activate
python.exe -m pip install --upgrade pip
pip install -r requirements.txt
pip install SoundCard-0.4.2-py3-none-any.whl
```

#### 開発環境でのvoice-translatorの実行方法
```
cd voice-translator
.venv\Scripts\activate
python -m voicetranslator
```


# Lisence

This project is licensed under the MIT License, see the LICENSE.txt file for details
