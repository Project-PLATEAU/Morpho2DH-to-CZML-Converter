# Morpho2DH to CZMLコンバータ 

![概要](SampleImage.PNG) 

## 1. 概要 
本リポジトリでは、2023年度のProject PLATEAUが開発した「Morpho2DH to CZMLコンバータ」のソースコードを公開しています。
「Morpho2DH to CZMLコンバータ」は、[「家屋倒壊判定モジュール」](https://github.com/Project-PLATEAU/Building-collapse-detector)の出力結果をWebGIS上でアニメーション可視化するためのコンバータです。

## 2. 「Morpho2DH to CZMLコンバータ」について 
「Morpho2DH to CZMLコンバータ」は、土石流シミュレーションシステムiRIC Morpho2DHの改変プログラム[「家屋倒壊判定モジュール」](https://github.com/Project-PLATEAU/Building-collapse-detector)を用いて出力した土石流シミュレーションデータ（CSV形式）を、WebGISであるTerria Map上で可視化するため、タイムスタンプ付きのCZMLに変換するためのコンバータです。  

本システムの詳細については[技術検証レポート](https://www.mlit.go.jp/plateau/file/libraries/doc/plateau_tech_doc_0072_ver01.pdf)を参照してください。

## 3. 利用手順 
本システムの構築手順及び利用手順については[利用チュートリアル](https://project-plateau.github.io/Morpho2DH-to-CZML-Converter/)を参照してください。

## 4. システム概要 
・Morpho2DHより出力された時刻ごと水理量・変化した地形データ・家屋倒壊判定結果（それぞれCSVファイル）を、Terria Map上でタイムスタンプに従ったアニメーション表示ができるよう、CZML形式に変換します。  
  
・変換対象となるデータは、Morpho2DHのFortranサブルーチン「Building-collapse-detector」を呼び出して実行された土石流シミュレーションの出力結果である、時刻ごと水理量（流体力）・変化した地形データ（流動深）・建物メッシュごと倒壊判定結果（建物倒壊情報）・建物ごと倒壊判定結果（建物倒壊フラグ）の、CSVファイルです。  
  
・上記データを対象に、可視化コンバータでは以下を行うことができます。  
&nbsp;&nbsp;&nbsp;&nbsp;流動深をcsvからczmlに変換します。  
&nbsp;&nbsp;&nbsp;&nbsp;流体力をcsvからczmlに変換します。  
&nbsp;&nbsp;&nbsp;&nbsp;建物倒壊情報をcsvからczmlに変換します。  
&nbsp;&nbsp;&nbsp;&nbsp;建物倒壊フラグをcsvからczmlに変換します。  

## 5. 利用技術

| 種別              | 名称   | バージョン | 内容 |
| ----------------- | --------|-------------|-----------------------------|
| ライブラリ      | [pyproj](https://pyproj4.github.io/pyproj/stable/) | 3.6.0 | 地図投影と座標変換ライブラリ |
|       | [czml](https://github.com/cleder/czml) | 0.3.3 | czml読み書きライブラリ |

## 6. 動作環境 <!-- 動作環境についての仕様を記載ください。 -->
| 項目               | 最小動作環境                                                                                                                                                                                                                                                                                                                                    | 推奨動作環境                   | 
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ | 
| OS                 | Microsoft Windows 10 または 11                                                                                                                                                                                                                                                                                                                  |  同左 | 
| CPU                | Intel Core i5以上                                                                                                                                                                                                                                                                                                                               | Intel Core i7以上              | 
| メモリ             | 8GB以上                                                                                                                                                                                                                                                                                                                                         | 16GB以上                        | 
| グラフィックカード             | Intel(R) HD Graphics 520以上                                                                                                                                                                                                                                                                                                                                         | NVIDIA GeForce RTX 2080以上                        | 
| ディスプレイ解像度 | 1024×768以上                                                                                                                                                                                                                                                                                                                                    |  1920x1080以上                   | 

## 7. 本リポジトリのフォルダ構成
| フォルダ名 |　詳細 |
|-|-|
| JavaScript code.txt | Cesium実行用のJavaScriptコードです |
| czml_from_bldg_iRIC.py | 建物崩壊フラグをcsvからczmlに変換します |
| czml_from_csv_collapse.py | 建物崩壊情報をcsvからczmlに変換します |
| czml_from_csv_depth.py | 流動深をcsvからczmlに変換します |
| czml_from_csv_fbuilding.py | 流体力をcsvからczmlに変換します |
| log_lonlat_JS生成_テンプレ.xlsx | 緯度経度からJavaScriptコードを生成します |
| lonlat_from_czml.py | czmlから緯度経度を抽出します |
| rename.py | ファイル名を標準化します |

## 8. ライセンス 

- ソースコード及び関連ドキュメントの著作権は国土交通省に帰属します。
- 本ドキュメントは[Project PLATEAUのサイトポリシー](https://www.mlit.go.jp/plateau/site-policy/)（CCBY4.0及び政府標準利用規約2.0）に従い提供されています。

## 9. 注意事項 

- 本リポジトリは参考資料として提供しているものです。動作保証は行っていません。
- 本リポジトリについては予告なく変更又は削除をする可能性があります。
- 本リポジトリの利用により生じた損失及び損害等について、国土交通省はいかなる責任も負わないものとします。

## 10. 参考資料 
- 技術検証レポート: https://www.mlit.go.jp/plateau/file/libraries/doc/plateau_tech_doc_0072_ver01.pdf
- PLATEAU WebサイトのUse caseページ「精緻な土砂災害シミュレーション」: https://www.mlit.go.jp/plateau/use-case/uc23-02/
