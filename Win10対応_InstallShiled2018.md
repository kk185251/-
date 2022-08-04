---
title: "Spart Win10対応におけるパッケージ作成(Install Sheild2018版)"
tags: "Win10対応"
---

# はじめに

InstallShield2018を利用する。基本的に、筆者が担当したデイトナのプロジェクトを前提として進めるため、フォルダパスなどは違う可能性がある。そこは、自分の担当しているプロジェクトに置き換えて見進めてほしい。  
また、Customize PackageとGeneral Packageの2つを対象としている。2つのパッケージで違う設定の仕方がある場合は、その旨を記載するので安心してほしい。

# 作成方法

## Install Shield2018を立ち上げるまで
客先のパッケージ作成環境まで入る。

以下のネットワークパスに接続する。
    \\153.59.51.164
    \\153...169?

パスワードは  
User/mono, Password/password

客先のパッケージ作成環境のフォルダに移動する。  
Win10用パッケージ作成環境用のフォルダを新規作成する。

Windowsメニューの「すべてのプログラム」からInstallShieldフォルダのInstallShield2018を起動する。

## Install Shield2018

Project Tasksのcreate new projectを選択する。

CommonタブのInstallScript Projectを選択する。

プロジェクト名を決定する。名前は、顧客先名の方が良いかもしれない。(同プロジェクトの他がどのような名称になっているのか参考にして決めると統一するので良い)

LocationのBrowseボタンを押下する。
作成したセットアップ(.ism)をどこに配置するのか決定する。(ここも、他のパッケージがどこに配置されているのか確認して配置場所を決めた方が良い)

左下の「Create ~ 」にチェックを付ける。

他客先と同様に新規作成したフォルダの直下に入れる。

OKを選択する。

下側に、いくつか項目が並んでいる。

Application Informationを選択する。

Installtion Interview　  
全てのチェックボタンを「No」にする。

Build Install  
single executableにのみチェックをつける

Install Designer  
General info  
設定が合っているか確認する。  
TargetDir 展開先のpathである。
値を変更する
```
SPART
変更後：C:\opos\Application\SS

Mex SPART
変更後：C:\software\ncr\res
```
「executable file」の設定値は削除する。

保存する。

「product code」があるが、これはユニークIDである。
つまり、他プロジェクトとはproduct codeはかぶってはいけない。かぶらないようにする。(しかし、基本的に新しくプロジェクトを作成したなら一意なIDであると思う)

エクスプローラの同プロジェクトのWin10用ではないパッケージ作成環境から、DATAフォルダをコピーする  

ディレクトリ階層はWin10を統一すること。その方が管理しやすいし楽なので

立ちあがっていないなら作成したプロジェクト(.ism)を起動する。

project assistantタブの「Application Files」の「Application Target Folder」を選択する。

Win10用のパッケージにコピーしてきたDataフォルダ内の各フォルダをDrag&Dropする。  
丁寧に安全に設定したいため、1個ずつ行うこと。  
更新しないと、追加したのが画面上に反映されないため、右クリックから「Reflesh」をクリックすると、更新される。

**ここから先は丁寧にやらないとパッケージ作成して、仮想環境に展開後、SPartの起動に失敗するため注意する。**  

Installtion Designerタブを選択する。  
Orgenizationのsetup designより、default feature、defaultComponentをまずは削除する。

先ほど「Apprication Target Folder」に追加したフォルダが「Files」という名称で作成されているため、この名前を追加したフォルダ名と一緒にする。

### Dataフォルダの設定
まず、同客先の前パッケージのsetup.rulを開く。

設定対象のフォルダ名で名前検索(Ctrl + F)をする。svTargetがあり"INCLUDE_SUBDIR"があると、Always、SELFREGがあると、self-registerにYesと設定する。

設定で帰るのは、Overwriteとself-registoryである。Overwriteは、どのように上書きするか設定するプロパティであり、基本"Always"で設定する。Alwaysは同日付で強制的に上書きする意味を持つ。
selfregesterは基本serverフォルダやprogramフォルダのdll、exeの実行ファイルで設定することが多い。レジストリ登録するかの設定。

setup.rulのsvTargetの格納先によって、Destinationが変わるため、ここはよく見て設定しないといけない。
例
svTarget => C\\OPOS\\
TargetDisk => C:\\OPOS\\Application\\SS\\

Application Data\\File&Folders\\Application Target Folder\\
フォルダ直下に何もなければそのフォルダを消す。もしある場合は、Desinationの設定が違う可能性がある。
ただし、Application Target FolderはC:\\OPOS\\であるため、OPOS直下に配置場所を設定しているフォルダは削除しなくてもよい

この作業をData内のすべてのフォルダで設定する。

System ConfigurationのProgram menu\\NCRは削除してよい。

ModifysetupINI.basのpackage name = Media..\\Disk Images\\Disk1\\setup_out.INIのApp nameが合っているか。setup_in.txtともあっているか。違う場合は、合わせる。
ProductIDはInstallShieldのGeneralInformationのproduct codeの数字列だけコピペする。

ScriptFilesフォルダは他客先からコピーする。(Setup.rulがロジックが微妙に違うため)  
setup.rulを確認する。  
基本的に前パッケージのsetup.rulを正しい前提としているため、足りない記述は追記する。しかし、前のパッケージのInstallShieldはInstall Shield2015と違うバージョンであるため、コードの記述は異なっている。であるため、必ず見るべきポイントは、パラメータ定義(#define ~)がすべてそろっているか、レジストリ登録するコードの記述に足りないところはないか、CreateDir関数は合っているのか確認する。

setup.rulを右クリックし、"compile"を選択。エラーも出ないならOK。

project AssistantのBuild Installtionで、Single～のみチェックし、Build Installtionをクリック。

Media\\Release\\Releaseは削除する。
SINGLE\_....IMAGEがあるため、これからパッケージをビルドしたい場合は、BuildタブのSINGLE_IMAGEでビルドする。

Support Files/Billboards\\Advanced Files\\Disk1\\に、NewNCR.bmp、VERSION.INIを追加する。追加するファイル元は、Support files\\Disk1\\からコピーする。

Media\\Release\\Single_IMAGEの「evnet」タブ、Execude bat pathには、posbuild_option.batまでのパスを設定する。

BUILDタブのSINGLE_IMGE(F7)を選択すると、パッケージが作成できる。

Customize pkgは、修正分のパッケージのみで作成されている。これは、SDM(Software Download Manager、社内用語)配信で店舗のPOSに展開されるため、できるだけデータサイズを小さくする目的がある。

General pkgは、OPOSのベースとなるデータであり、作成したらよほどのことがない限り基本は変えない。OPOSの基本モジュールのパッケージである。

# 起動確認

GeneralPackageを当てる。再起動する。POSアプリを起動させ、レジストリ登録を行う。

CustmizePackageを当てる。再起動する。エラーが出なければOK。でたらLogを見て原因を特定する。
