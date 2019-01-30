
# qiita_make_drill

下記のQiita コメントの参考用：

[プログラミング未経験者がPython覚えて子ども用計算ドリルを作る](https://qiita.com/sotogawa/items/14ecbf090ae05a8eddb7)


```python

"""計算練習ドリルを作成（新規ブック作成版）
"""

import random
import openpyxl

wb = openpyxl.Workbook()  #新規ワークブックを作成
sheet = wb.active
list_ = [[a, b] for a in range(1, 10) for b in range(1, 10)]
random.shuffle(list_)

for n, v in enumerate(list_):
	x, y = n // 6, n % 6    # 座標変換1 (碁盤タイプ） 
	r, c = x+3 , y*6+1      # 座標変換２【(r,c】各計算式左上座標）
	sheet.cell(row=r, column=c, value=v[0])
	sheet.cell(row=r, column=c + 1, value='+')
	sheet.cell(row=r, column=c + 2, value=v[1])
	sheet.cell(row=r, column=c + 3, value='=')
	print(n,(x,y),(r,c),v)  #参考に座標変換内容表示
wb.save('output.xlsx')
```




![drill_img](https://github.com/zaq9/qiita_make_drill/blob/master/drill_img.JPG)

