# Tiff4LabVIEW

## 概要
通常のLabVIEWではTIFFファイルを読み書きすることができず、「[NI画像入力ソフトウェア (IMAQ-Vision)](http://sine.ni.com/nips/cds/view/p/lang/ja/nid/12892)」を用いることでそれが可能になります。

しかし、「IMAQ-Vision」のTIFF対応は、
- 1bit白黒形式およびIEEE float形式の画像に未対応
- マルチページTIFFに未対応

と機能に不満があります。そこで、これらに対応した（IMAQ-Visionに依らない）ライブラリ「Tiff4LabVIEW」を開発しました。

## 環境
LabVIEW2015SP1、.NET Framework4.0以上

## インストール
「Tiff.llb」をダウンロードし、適当なフォルダに保存するだけです。

## 使い方
### isTiff.vi
ファイルがTIFFファイルかどうかを判定します。

ファイル先頭4バイトが「0x49 0x49 0x2A 0x00」か「0x4D 0x4D 0x00 0x2A」であればTIFFファイルと判断しています。

### Read TIFF File.vi
TIFFファイルから画像データを読み込みます。

マルチページTIFFに対応し、「ポジション」に与えた位置（ゼロ基点）のページの画像データを返します。
総ページ数を超える値もしくは負値を与えた場合には最後のページ画像を返します。
対応する画像形式は以下の6つです。
- 1bit白黒
- 8bitグレースケール
- 8bitカラーマップ
- 16bitグレースケール
- 24bitRGB
- 32bit IEEE float

16bitグレースケールと32bit IEEE floatでは、出力される画像データは独自拡張されたものとなっており、2Dピクチャに接続しても画像表示されません。

## ライセンス
このLLBおよびVIはMITライセンスに則り公開されています（LICENSE.txt参照）。
