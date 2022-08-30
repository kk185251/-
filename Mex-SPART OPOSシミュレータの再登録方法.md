# 概要
SPART Mexのシミュレータを登録し実行する方法についてまとめる。
さらに間違えてシミュレータを閉じてしまいアプリを起動してもシミュレータが実行されないケースについて、シミュレータの再登録方法をまとめる。

# 前提
`c:\opos\plus`配下 にシミュレータ用モジュールがないこと。

# シミュレータの登録方法
## シミュレータを開発環境に置く
人のところからコピーする。

## c:\opos\cco にコモンコントロールがインストールされてない場合
http://monroecs.com/oposccos_current.htm
から最新版をダウンロードしてc:\oposの下に展開する。  
展開後、zipに添付されているregister.batを管理者権限のコマンドプロンプトから実行する。
ここでExplorerでダブルクリックしても無意味。

```
cd \opos\展開ディレクトリ
register.bat
```

## uiagent.iniを修正
1. c:\software\ncr\res\para\uiagent.iniをエディタ-で開く
2. [device]を編集する
[device] 構成セクションに、`deviceN=デバイスID;OPOS CO名;OPOS SO名;スクリプト名`で記述する。
※先頭が;や#の行はコメント
デバイスIDは以下のいずれか。
printer1
scanner1
drawer1
cashchanger1

MSRは話が面倒なので自力更生できる人のみ利用可

OPOS.CO名は、既存のコメント行から必要なものを設定する。
OPOS.SO名は、以下のいずれか。
NCRSim.ReceiptPrinter
NCRSim.Scanner
NCRSim.Drawer
NCRSim.CashChanger
スクリプト名は、既存のコメント行から必要なものを設定する。
ただし、Scannerは、scanner.jsを利用する（HWScanner.jsはダメ）

# シミュレータの再登方法
## モジュールをレジストリ登録をする
### Win + Rで「ファイル名を指定して実行」を実行する
管理者権限でなければ、やったフリのみとなるので注意。  
Explorerでシミュレータモジュールをダブルクリックしても無意味。

### レジストリ登録する
(c:\opos\plus\simulators以下にシミュレータが配置されている前提で進める。)

#### GUIを登録
GUIで使うためのモジュールをレジストリ登録する。  
```regsvr32 c:\opos\plus\simulators\FrmGUI.ocx```
#### プリンタを使う場合
プリンターシミュレータ「SimPrinter.exe」をレジストリ登録する。  
```c:\opos\plus\simulators\SimPrinter.exe /Regserver```
#### スキャナを使う場合
スキャナシミュレータ「ScanSim.exe」をレジストリ登録する。  
```c:\opos\plus\simulators\ScanSim.exe /Regserver```
#### ドロアーを使う場合
ドロアーシミュレータ「SimConsole.exe」をレジストリ登録する。  
```c:\opos\plus\simulators\SimConsole.exe /RegServer```
#### 釣銭機を使う場合
釣銭機シミュレータ「SimCashChanger.dll」をレジストリ登録する。
```regsvr32 c:\opos\plus\simulators\SimCashChanger.dll```


### レジストリからキーを削除する
対象のレジストリキー「InprocHandler32」を削除する。  
無いものもあるので、その場合は無視する。

|レジストリキー|シミュレータ|
|-|-|
|[HKEY_CLASSES_ROOT\CLSID\{3268B39A-D17B-11D0-BB3A-00A0249EABBE}\InprocHandler32] | Sim.ReceiptPrinter|
|[HKEY_CLASSES_ROOT\CLSID\{77195382-8864-11D0-9250-000039253C03}\InprocHandler32] | Sim.Scanner|
|[HKEY_CLASSES_ROOT\CLSID\{C698E8A6-8B87-11D0-9256-000039253C03}\InprocHandler32] |Sim.CustDisplay|
|[HKEY_CLASSES_ROOT\CLSID\{75D37853-A4A7-11D0-9271-000039253C03}\InprocHandler32]  |Sim.MSR|
|[HKEY_CLASSES_ROOT\CLSID\{3268B39C-D17B-11D0-BB3A-00A0249EABBE}\InprocHandler32]  |Sim.SlipPrinter|
|[HKEY_CLASSES_ROOT\CLSID\{71C82F4C-8BCA-11D0-9257-000039253C03}\InprocHandler32] |Sim.KeyLock|
|[HKEY_CLASSES_ROOT\CLSID\{3268B39E-D17B-11D0-BB3A-00A0249EABBE}\InprocHandler32] |Sim.JournalPrinter|
|[HKEY_CLASSES_ROOT\CLSID\{71C82F49-8BCA-11D0-9257-000039253C03}\InprocHandler32]|SimConsole|
|[HKEY_CLASSES_ROOT\CLSID\{580F2F6C-912F-11D0-925C-000039253C03}\InprocHandler32]  |Sim.CoinDispenser|

## アプリ再起動してシミュレータが起動されるか確認
「Spart Mex Agent」を起動して、シミュレータが起動すればOK。  
起動されていなければ、もう一度レジストリ登録する所から始める。  
(うろ覚え程度の知識なのでもしかしたら、レジストリ登録するモジュールが違っていたり、削除したいレジストリキーが違う場合もあるのでそれはすみません。)

