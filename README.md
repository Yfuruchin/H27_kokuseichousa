# H27(2015)国勢調査における丁目ポリゴン
- e-Statより北海道全域の境界データのShapeファイルをGeoJSONで提供する
    
<img src="https://i.gyazo.com/b18d75f3f5ea57d886e77fc26e00598a.jpg" width="640">
<img src="https://i.gyazo.com/cacfaba82f18488dc277d87ba3ab3919.png" width="640">

## 出典
- [政府統計の総合窓口(e-Stat)境界データ(北海道)](https://www.e-stat.go.jp/gis/statmap-search?page=1&type=2&aggregateUnitForBoundary=A&toukeiCode=00200521&toukeiYear=2015&serveyId=A002005212015&prefCode=01&coordsys=1&format=shape)

## ライセンス    
- CC BY 4.0 国際と互換性あり
- その他ライセンスに関しては[こちらを参照](https://www.e-stat.go.jp/terms-of-use)

## データについて
- e-Statの「境界データ」とは町丁・字等別の境界を示す
- 文字コードはマスターのShift-JISをUTF-8に変換した
- 投影法は世界測地系緯度経度(WGS84, EPSG:3857)
- 元データの段階でトポロジーが壊れている場合があります。空間解析等に用いる場合は一旦クリーニングなどをしたほうがよいかもしれません

## ファイルは[こちら](https://www.dropbox.com/s/a6avpo8a5ixlprx/H27_hokkaido_estats.geojson?dl=0)
-   Githubの25MB制限のため、とりあえずここにおいてます

## その他諸元

- 以下情報は[注意事項](https://www.e-stat.go.jp/sites/default/files/pdf/gis/notes/00200521.pdf)・[定義書](https://www.e-stat.go.jp/gis/statmap-search/data?datatype=2&serveyId=A002005212015&downloadType=1)よりコピー

### 注意事項

1. 国勢調査の町丁・字等境界データは、地方公共団体が調査を実施する際に設定した調査区の境界を基に作成しているため、住居表示等で用いられている実際の町丁・字の境界と一致しない場合があります。また、町丁・字の名称についても、一致しない場合があります。

2. 一つの市区町村内に同一の町丁・字番号を持つ境域が複数存在する場合があり、このような場合には、重複フラグを付与し、識別できるようにしています。

3. 町丁・字等の面積は、町丁・字等の境界データの図郭により算出したものであり、市区町村内のすべての町丁・字等の総計は、国土地理院等の公式な面積と一致しません。

4. 都道府県の境界線は、接合処理を行っていないため、都道府県をまたがって市区町村を接合した場合には、都道府県の境界線にずれが生じる場合があります。

5. 他県の飛び地の境域が市区町村に含まれる場合は、当該飛び地の境域情報も含まれます。また、水面調査区(※)がある場合には、同様に水面調査区の情報も含まれます。※ 水面調査区とは、重要港湾等の港湾区域並びに漁港及び河川の河口等の水域で水上生活者のいる区域をいいます。（定義書「HCODE」(分類コード)=8154 水面調査区）

### データ定義

No.   | フィールド名  | 項目内容           | 備考    
----- | ---------- | ----------------- | -------------------------------------------
1     | KEY_CODE   | 図形と集計データのリンクコード   | KEN+KEYCODE2                               
2     | PREF       | 都道府県番号            |                                            
3     | CITY       | 市区町村番号            |                                            
4     | S_AREA     | 町字コード+丁目、字などの番号   | KIHON1+KIHON2                              
5     | PREF_NAME  | 都道府県名             | １）                                         
6     | CITY_NAME  | 区町村名              | １）　　CSS_NAME（ない場合はGST_NAME)                
7     | S_NAME     | 町丁・字等名称           | １）                                         
8     | KIGO_E     | 特殊記号E（町丁・字等重複フラグ） | ５）                                         
9     | HCODE      | 分類コード             | ２）                                         
10    | AREA       | 面積(㎡)             |                                            
11    | PERIMETER  | 周辺長（ｍ）            |                                            
12    | H27KAxx_   | 内部ID              |                                            
13    | H27KAxx_ID | 外部ID              |                                            
14    | KEN        | 都道府県番号            | 町丁・字等番号                                    
15    | KEN_NAME   | 都道府県名             | １）                                         
16    | SITYO_NAME | 支庁・振興局名           | １）                                         
17    | GST_NAME   | 郡市・特別区・政令指定都市名    | １）                                         
18    | CSS_NAME   | 区町村名              | １）                                         
19    | KIHON1     | 町字コード             |                                            
20    | DUMMY1     | ダミー（"-"）          |                                            
21    | KIHON2     | 丁目、字などの番号         |                                            
22    | KEYCODE1   | マッチング番号           | CITY+KIHON1+KIHON2                         
23    | KEYCODE2   | 町丁・字等別結果マッチング番号   |                                            
24    | AREA_MAX_F | 面積最大フラグ           | ３）                                         
25    | KIGO_D     | 特殊記号D（飛び地、抜け地フラグ） | ４）                                         
26    | N_KEN      | 抜け地県番号            |                                            
27    | N_CITY     | 抜け地市区町村番号         |                                            
28    | KIGO_I     | 特殊記号I（島フラグ）       | ６）                                         
29    | MOJI       | 町丁・字等名称           | １）                                         
30    | KBSUM      | 基本単位区（調査区）数       | ７）                                         
31    | JINKO      | 人口                | KIGO_Eが付与されている場合は、E1に代表してセットし、En（n≧2）は0（ゼロ）
32    | SETAI      | 世帯数               | KIGO_Eが付与されている場合は、E1に代表してセットし、En（n≧2）は0（ゼロ）
33    | X_CODE     | 図形中心点Ｘ座標（10進経度）   |                                            
34    | Y_CODE     | 図形中心点Ｙ座標（10進緯度）   |                                            
35    | KCODE1     | 町丁・字等番号           | KIHON1+DUMMY1+KIHON2                       


1. 文字コード：シフトＪＩＳ(**※本リポジトリのデータはUTF-8に変換済み**)。左詰め

2. 分類コード（HCODE）

    「8101」：町丁・字等

    「8154」：水面調査区

3. 面積最大フラグ（AREA_MAX_F）

「M」：一つの市区町村内に同一の町丁・字等番号を持つ境界が複数存在した場合、一番広い面積を持つ境界に付与。又は、同一の町丁・字等番号を持つ境界がない場合に付与

4. 特殊記号D

    「D」：飛び地
    「D1」：抜け地（飛び地）

5. 特殊記号E

「En」(n≧1)：一つの市区町村内に同一の町丁・字等番号を持つ境界が複数存在した場合、原則として、境界ごとに足し上げた基本単位区（調査区）の人口が多い順にE1から付与。足し上げた基本単位区（調査区）の人口が同じ境界が複数ある場合は、面積の広い順に付与。
ただし、島と島以外（以下「陸地」という。）がある場合は、陸地部分を優先して付与

6. 特殊記号I
「Ｉ」：島（原則として、当該町丁・字等別境界内の基本単位区（調査区）全てにIフラグが付与されている場合）　

7. 当該町丁・字等の中の基本単位区（調査区）の数。（1対１の場合は１）。KIGO_Eが付与されている場合は、E1に代表してセットし、En（n≧2）は0（ゼロ）

※　平面直角座標で複数の系にまたがる次の４都道県は、それぞれ、北海道は12系、東京都は９系、鹿児島県は２系、沖縄県は15系としている。

