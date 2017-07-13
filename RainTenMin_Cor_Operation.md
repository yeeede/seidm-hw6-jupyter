
# SEIDM


```python
%matplotlib inline

import os
import pandas
import random
```


```python
input_csv = 'RainTenMin_20170712135025.csv'
full_df = pandas.read_csv(input_csv, sep=',', skipinitialspace=True)
```

### Radom Selection


```python
num_lines_full_df = sum(1 for l in open(input_csv))
skip_idx = random.sample(range(1, num_lines_full_df), int(num_lines_full_df * 0.99))
```


```python
sample_df = pandas.read_csv(input_csv, skiprows=skip_idx, sep=',', skipinitialspace=True)

sample_df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SiteId</th>
      <th>SiteName</th>
      <th>County</th>
      <th>Township</th>
      <th>TWD67Lon</th>
      <th>TWD67Lat</th>
      <th>Rainfall10min</th>
      <th>Rainfall1hr</th>
      <th>Rainfall3hr</th>
      <th>Rainfall6hr</th>
      <th>Rainfall12hr</th>
      <th>Rainfall24hr</th>
      <th>Now</th>
      <th>Unit</th>
      <th>PublishTime</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C0R620</td>
      <td>墾雷</td>
      <td>屏東縣</td>
      <td>恆春鎮</td>
      <td>120.8472</td>
      <td>21.9027</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.5</td>
      <td>1.5</td>
      <td>1.5</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>C0K470</td>
      <td>林內</td>
      <td>雲林縣</td>
      <td>林內鄉</td>
      <td>120.6015</td>
      <td>23.7504</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>10.5</td>
      <td>0.0</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01H780</td>
      <td>內茅埔(2</td>
      <td>南投縣</td>
      <td>信義鄉</td>
      <td>120.8437</td>
      <td>23.6924</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>水利署第四河川局</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>88O950</td>
      <td>羌黃坑</td>
      <td>臺南市</td>
      <td>南化區</td>
      <td>120.5289</td>
      <td>23.0739</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>18.5</td>
      <td>0.0</td>
      <td>農委會水土保持局</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>A1A9W0</td>
      <td>陽明高中</td>
      <td>臺北市</td>
      <td>士林區</td>
      <td>121.5085</td>
      <td>25.0943</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>臺北市水利處</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>C1T850</td>
      <td>吉安</td>
      <td>花蓮縣</td>
      <td>吉安鄉</td>
      <td>121.5547</td>
      <td>23.9753</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>6</th>
      <td>C1H860</td>
      <td>瑞岩</td>
      <td>南投縣</td>
      <td>仁愛鄉</td>
      <td>121.1750</td>
      <td>24.1256</td>
      <td>0</td>
      <td>2.5</td>
      <td>2.5</td>
      <td>2.5</td>
      <td>2.5</td>
      <td>2.5</td>
      <td>2.5</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>C1O870</td>
      <td>大棟山</td>
      <td>臺南市</td>
      <td>白河區</td>
      <td>120.5142</td>
      <td>23.3133</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.5</td>
      <td>0.0</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
  </tbody>
</table>
</div>



### Save DataFrame to CSV


```python
cor_df = full_df[['SiteId', 'SiteName', 'TWD67Lon', 'TWD67Lat']]
```


```python
output_csv = 'RainTenMin_Cor.csv'
cor_df.to_csv(output_csv, index=False, sep=',', encoding='utf-8')
```


```python

```
