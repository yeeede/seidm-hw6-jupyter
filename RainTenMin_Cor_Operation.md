
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
      <td>C0R260</td>
      <td>春日</td>
      <td>屏東縣</td>
      <td>春日鄉</td>
      <td>120.6203</td>
      <td>22.3722</td>
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
      <th>1</th>
      <td>C0V350</td>
      <td>溪埔</td>
      <td>高雄市</td>
      <td>大樹區</td>
      <td>120.4386</td>
      <td>22.7403</td>
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
      <th>2</th>
      <td>C0R510</td>
      <td>萬丹</td>
      <td>屏東縣</td>
      <td>萬丹鄉</td>
      <td>120.4824</td>
      <td>22.5896</td>
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
      <th>3</th>
      <td>C0V750</td>
      <td>路竹</td>
      <td>高雄市</td>
      <td>路竹區</td>
      <td>120.2514</td>
      <td>22.8566</td>
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
      <th>4</th>
      <td>A1AC70</td>
      <td>挹翠</td>
      <td>臺北市</td>
      <td>信義區</td>
      <td>121.5662</td>
      <td>25.0189</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>臺北市大地工程處(信義挹翠山莊)</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>L1A800</td>
      <td>碧湖</td>
      <td>新北市</td>
      <td>坪林區</td>
      <td>121.7375</td>
      <td>24.8944</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.5</td>
      <td>0.0</td>
      <td>翡翠水庫</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>6</th>
      <td>C1I440</td>
      <td>新高口</td>
      <td>南投縣</td>
      <td>信義鄉</td>
      <td>120.8707</td>
      <td>23.4805</td>
      <td>0</td>
      <td>0.5</td>
      <td>0.5</td>
      <td>0.5</td>
      <td>0.5</td>
      <td>16.0</td>
      <td>0.5</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>C1H9B1</td>
      <td>阿眉</td>
      <td>南投縣</td>
      <td>仁愛鄉</td>
      <td>120.9861</td>
      <td>24.1278</td>
      <td>0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.0</td>
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
cor_df.to_csv(output_csv, sep=',', encoding='utf-8')
```


```python

```
