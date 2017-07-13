
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
      <td>O1D590</td>
      <td>成德中學</td>
      <td>新竹市</td>
      <td>北區</td>
      <td>120.9445</td>
      <td>24.7916</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>水利署第二河川局</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01H680</td>
      <td>北山(2)</td>
      <td>南投縣</td>
      <td>國姓鄉</td>
      <td>120.8847</td>
      <td>23.9873</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>水利署第三河川局</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01AG00</td>
      <td>社后橋</td>
      <td>新北市</td>
      <td>汐止區</td>
      <td>121.6336</td>
      <td>25.0630</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>水利署第十河川局</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>A1A9V0</td>
      <td>北投國小</td>
      <td>臺北市</td>
      <td>北投區</td>
      <td>121.4907</td>
      <td>25.1357</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>臺北市水利處</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C1E461</td>
      <td>松安</td>
      <td>苗栗縣</td>
      <td>泰安鄉</td>
      <td>120.9778</td>
      <td>24.3994</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>5</th>
      <td>C0D430</td>
      <td>峨眉</td>
      <td>新竹縣</td>
      <td>峨眉鄉</td>
      <td>121.0091</td>
      <td>24.6924</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>9</td>
      <td>0</td>
      <td>局屬無人測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>6</th>
      <td>467620</td>
      <td>蘭嶼</td>
      <td>臺東縣</td>
      <td>蘭嶼鄉</td>
      <td>121.5503</td>
      <td>22.0388</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>局屬氣象測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
    <tr>
      <th>7</th>
      <td>466990</td>
      <td>花蓮</td>
      <td>花蓮縣</td>
      <td>花蓮市</td>
      <td>121.6051</td>
      <td>23.9769</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>局屬氣象測站</td>
      <td>2017-07-12 13:40:00</td>
    </tr>
  </tbody>
</table>
</div>



### Save DataFrame to CSV


```python
cor_df = full_df[['SiteName', 'SiteId', 'County', 'TWD67Lon', 'TWD67Lat']]

output_csv = 'RainTenMin_Cor.csv'
```


```python
cor_df.index += 1
cor_df.to_csv(output_csv, sep=',', encoding='utf-8')
# cor_df.to_csv(output_csv, index=False, sep=',', encoding='utf-8')
```


```python

```
