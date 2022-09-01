# 概要
RAPとは、リアルタイムでPOSを監視する端末のこと。  
そんなRAPについて得た知見をまとめる。

# RAPの起動方法


# RAPのバージョン
現在のアプリケーションプール内のマネージド アプリケーションに使用される.NET Framework のバージョンが**4.0**でしか動かないらしい。

なのでRAPが動かない場合、以下を実行するようにバッチファイルを作成するなりすれば解決する。
```
c:\windows\system32\inetsrv\appcmd set apppool "DefaultAppPool" /managedRuntimeVersion:v4.0
```
