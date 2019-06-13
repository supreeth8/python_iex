

```python
import pandas as pd
import requests as req
```


```python
r = req.get('https://cloud.iexapis.com/stable/'+
            'stock/aapl/balance-sheet/4?token=pk_39f74abd1d694902a09c3e8fc811870e&period=annual')
```


```python
data = r.json()
# print(data)
df = pd.DataFrame()
for index in range(len(data['balancesheet'])):
#     print(index)
    if df.empty:
        df = pd.DataFrame.from_dict(data['balancesheet'][index],orient='index')
    else:
        df[index] = pd.DataFrame.from_dict(data['balancesheet'][index],orient='index')
df.columns = df.iloc[0].values
df.to_excel('raw_balanceSheet.xlsx')
display(df)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>2018-09-30</th>
      <th>2017-09-30</th>
      <th>2016-09-30</th>
      <th>2015-09-30</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>reportDate</th>
      <td>2018-09-30</td>
      <td>2017-09-30</td>
      <td>2016-09-30</td>
      <td>2015-09-30</td>
    </tr>
    <tr>
      <th>currentCash</th>
      <td>25913000000</td>
      <td>20289000000</td>
      <td>20484000000</td>
      <td>21120000000</td>
    </tr>
    <tr>
      <th>shortTermInvestments</th>
      <td>40388000000</td>
      <td>53892000000</td>
      <td>46671000000</td>
      <td>20481000000</td>
    </tr>
    <tr>
      <th>receivables</th>
      <td>23186000000</td>
      <td>17874000000</td>
      <td>15754000000</td>
      <td>16849000000</td>
    </tr>
    <tr>
      <th>inventory</th>
      <td>3956000000</td>
      <td>4855000000</td>
      <td>2132000000</td>
      <td>2349000000</td>
    </tr>
    <tr>
      <th>otherCurrentAssets</th>
      <td>12087000000</td>
      <td>13936000000</td>
      <td>8283000000</td>
      <td>15085000000</td>
    </tr>
    <tr>
      <th>currentAssets</th>
      <td>131339000000</td>
      <td>128645000000</td>
      <td>106869000000</td>
      <td>89378000000</td>
    </tr>
    <tr>
      <th>longTermInvestments</th>
      <td>170799000000</td>
      <td>194714000000</td>
      <td>170430000000</td>
      <td>164065000000</td>
    </tr>
    <tr>
      <th>propertyPlantEquipment</th>
      <td>41304000000</td>
      <td>33783000000</td>
      <td>27010000000</td>
      <td>22471000000</td>
    </tr>
    <tr>
      <th>goodwill</th>
      <td>None</td>
      <td>5717000000</td>
      <td>5414000000</td>
      <td>5116000000</td>
    </tr>
    <tr>
      <th>intangibleAssets</th>
      <td>None</td>
      <td>2298000000</td>
      <td>3206000000</td>
      <td>3893000000</td>
    </tr>
    <tr>
      <th>otherAssets</th>
      <td>22283000000</td>
      <td>10162000000</td>
      <td>8757000000</td>
      <td>5556000000</td>
    </tr>
    <tr>
      <th>totalAssets</th>
      <td>365725000000</td>
      <td>375319000000</td>
      <td>321686000000</td>
      <td>290479000000</td>
    </tr>
    <tr>
      <th>accountsPayable</th>
      <td>55888000000</td>
      <td>49049000000</td>
      <td>37294000000</td>
      <td>35490000000</td>
    </tr>
    <tr>
      <th>currentLongTermDebt</th>
      <td>8784000000</td>
      <td>6496000000</td>
      <td>3500000000</td>
      <td>2500000000</td>
    </tr>
    <tr>
      <th>otherCurrentLiabilities</th>
      <td>40230000000</td>
      <td>33292000000</td>
      <td>30107000000</td>
      <td>34121000000</td>
    </tr>
    <tr>
      <th>totalCurrentLiabilities</th>
      <td>116866000000</td>
      <td>100814000000</td>
      <td>79006000000</td>
      <td>80610000000</td>
    </tr>
    <tr>
      <th>longTermDebt</th>
      <td>93735000000</td>
      <td>97207000000</td>
      <td>75427000000</td>
      <td>53463000000</td>
    </tr>
    <tr>
      <th>otherLiabilities</th>
      <td>4268000000</td>
      <td>3340000000</td>
      <td>4285000000</td>
      <td>4789000000</td>
    </tr>
    <tr>
      <th>minorityInterest</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>totalLiabilities</th>
      <td>258578000000</td>
      <td>241272000000</td>
      <td>193437000000</td>
      <td>171124000000</td>
    </tr>
    <tr>
      <th>commonStock</th>
      <td>40201000000</td>
      <td>35867000000</td>
      <td>31251000000</td>
      <td>27416000000</td>
    </tr>
    <tr>
      <th>retainedEarnings</th>
      <td>70400000000</td>
      <td>98330000000</td>
      <td>96364000000</td>
      <td>92284000000</td>
    </tr>
    <tr>
      <th>treasuryStock</th>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>capitalSurplus</th>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>shareholderEquity</th>
      <td>107147000000</td>
      <td>134047000000</td>
      <td>128249000000</td>
      <td>119355000000</td>
    </tr>
    <tr>
      <th>netTangibleAssets</th>
      <td>107147000000</td>
      <td>115006000000</td>
      <td>108409000000</td>
      <td>100898000000</td>
    </tr>
  </tbody>
</table>
</div>



```python
df_copy = df.iloc[1:,:]
df_copy
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>2018-09-30</th>
      <th>2017-09-30</th>
      <th>2016-09-30</th>
      <th>2015-09-30</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>currentCash</th>
      <td>25913000000</td>
      <td>20289000000</td>
      <td>20484000000</td>
      <td>21120000000</td>
    </tr>
    <tr>
      <th>shortTermInvestments</th>
      <td>40388000000</td>
      <td>53892000000</td>
      <td>46671000000</td>
      <td>20481000000</td>
    </tr>
    <tr>
      <th>receivables</th>
      <td>23186000000</td>
      <td>17874000000</td>
      <td>15754000000</td>
      <td>16849000000</td>
    </tr>
    <tr>
      <th>inventory</th>
      <td>3956000000</td>
      <td>4855000000</td>
      <td>2132000000</td>
      <td>2349000000</td>
    </tr>
    <tr>
      <th>otherCurrentAssets</th>
      <td>12087000000</td>
      <td>13936000000</td>
      <td>8283000000</td>
      <td>15085000000</td>
    </tr>
    <tr>
      <th>currentAssets</th>
      <td>131339000000</td>
      <td>128645000000</td>
      <td>106869000000</td>
      <td>89378000000</td>
    </tr>
    <tr>
      <th>longTermInvestments</th>
      <td>170799000000</td>
      <td>194714000000</td>
      <td>170430000000</td>
      <td>164065000000</td>
    </tr>
    <tr>
      <th>propertyPlantEquipment</th>
      <td>41304000000</td>
      <td>33783000000</td>
      <td>27010000000</td>
      <td>22471000000</td>
    </tr>
    <tr>
      <th>goodwill</th>
      <td>None</td>
      <td>5717000000</td>
      <td>5414000000</td>
      <td>5116000000</td>
    </tr>
    <tr>
      <th>intangibleAssets</th>
      <td>None</td>
      <td>2298000000</td>
      <td>3206000000</td>
      <td>3893000000</td>
    </tr>
    <tr>
      <th>otherAssets</th>
      <td>22283000000</td>
      <td>10162000000</td>
      <td>8757000000</td>
      <td>5556000000</td>
    </tr>
    <tr>
      <th>totalAssets</th>
      <td>365725000000</td>
      <td>375319000000</td>
      <td>321686000000</td>
      <td>290479000000</td>
    </tr>
    <tr>
      <th>accountsPayable</th>
      <td>55888000000</td>
      <td>49049000000</td>
      <td>37294000000</td>
      <td>35490000000</td>
    </tr>
    <tr>
      <th>currentLongTermDebt</th>
      <td>8784000000</td>
      <td>6496000000</td>
      <td>3500000000</td>
      <td>2500000000</td>
    </tr>
    <tr>
      <th>otherCurrentLiabilities</th>
      <td>40230000000</td>
      <td>33292000000</td>
      <td>30107000000</td>
      <td>34121000000</td>
    </tr>
    <tr>
      <th>totalCurrentLiabilities</th>
      <td>116866000000</td>
      <td>100814000000</td>
      <td>79006000000</td>
      <td>80610000000</td>
    </tr>
    <tr>
      <th>longTermDebt</th>
      <td>93735000000</td>
      <td>97207000000</td>
      <td>75427000000</td>
      <td>53463000000</td>
    </tr>
    <tr>
      <th>otherLiabilities</th>
      <td>4268000000</td>
      <td>3340000000</td>
      <td>4285000000</td>
      <td>4789000000</td>
    </tr>
    <tr>
      <th>minorityInterest</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>totalLiabilities</th>
      <td>258578000000</td>
      <td>241272000000</td>
      <td>193437000000</td>
      <td>171124000000</td>
    </tr>
    <tr>
      <th>commonStock</th>
      <td>40201000000</td>
      <td>35867000000</td>
      <td>31251000000</td>
      <td>27416000000</td>
    </tr>
    <tr>
      <th>retainedEarnings</th>
      <td>70400000000</td>
      <td>98330000000</td>
      <td>96364000000</td>
      <td>92284000000</td>
    </tr>
    <tr>
      <th>treasuryStock</th>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>capitalSurplus</th>
      <td>None</td>
      <td>None</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>shareholderEquity</th>
      <td>107147000000</td>
      <td>134047000000</td>
      <td>128249000000</td>
      <td>119355000000</td>
    </tr>
    <tr>
      <th>netTangibleAssets</th>
      <td>107147000000</td>
      <td>115006000000</td>
      <td>108409000000</td>
      <td>100898000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_copy = df_copy.dropna()
```


```python
df_copy.to_excel("ouput.xlsx")
```


```python
df.copy(lambda x: '{0:.2f}'.format(x/1e9))
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>2018-09-30</th>
      <th>2017-09-30</th>
      <th>2016-09-30</th>
      <th>2015-09-30</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>currentCash</th>
      <td>25913000000</td>
      <td>20289000000</td>
      <td>20484000000</td>
      <td>21120000000</td>
    </tr>
    <tr>
      <th>shortTermInvestments</th>
      <td>40388000000</td>
      <td>53892000000</td>
      <td>46671000000</td>
      <td>20481000000</td>
    </tr>
    <tr>
      <th>receivables</th>
      <td>23186000000</td>
      <td>17874000000</td>
      <td>15754000000</td>
      <td>16849000000</td>
    </tr>
    <tr>
      <th>inventory</th>
      <td>3956000000</td>
      <td>4855000000</td>
      <td>2132000000</td>
      <td>2349000000</td>
    </tr>
    <tr>
      <th>otherCurrentAssets</th>
      <td>12087000000</td>
      <td>13936000000</td>
      <td>8283000000</td>
      <td>15085000000</td>
    </tr>
    <tr>
      <th>currentAssets</th>
      <td>131339000000</td>
      <td>128645000000</td>
      <td>106869000000</td>
      <td>89378000000</td>
    </tr>
    <tr>
      <th>longTermInvestments</th>
      <td>170799000000</td>
      <td>194714000000</td>
      <td>170430000000</td>
      <td>164065000000</td>
    </tr>
    <tr>
      <th>propertyPlantEquipment</th>
      <td>41304000000</td>
      <td>33783000000</td>
      <td>27010000000</td>
      <td>22471000000</td>
    </tr>
    <tr>
      <th>otherAssets</th>
      <td>22283000000</td>
      <td>10162000000</td>
      <td>8757000000</td>
      <td>5556000000</td>
    </tr>
    <tr>
      <th>totalAssets</th>
      <td>365725000000</td>
      <td>375319000000</td>
      <td>321686000000</td>
      <td>290479000000</td>
    </tr>
    <tr>
      <th>accountsPayable</th>
      <td>55888000000</td>
      <td>49049000000</td>
      <td>37294000000</td>
      <td>35490000000</td>
    </tr>
    <tr>
      <th>currentLongTermDebt</th>
      <td>8784000000</td>
      <td>6496000000</td>
      <td>3500000000</td>
      <td>2500000000</td>
    </tr>
    <tr>
      <th>otherCurrentLiabilities</th>
      <td>40230000000</td>
      <td>33292000000</td>
      <td>30107000000</td>
      <td>34121000000</td>
    </tr>
    <tr>
      <th>totalCurrentLiabilities</th>
      <td>116866000000</td>
      <td>100814000000</td>
      <td>79006000000</td>
      <td>80610000000</td>
    </tr>
    <tr>
      <th>longTermDebt</th>
      <td>93735000000</td>
      <td>97207000000</td>
      <td>75427000000</td>
      <td>53463000000</td>
    </tr>
    <tr>
      <th>otherLiabilities</th>
      <td>4268000000</td>
      <td>3340000000</td>
      <td>4285000000</td>
      <td>4789000000</td>
    </tr>
    <tr>
      <th>minorityInterest</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>totalLiabilities</th>
      <td>258578000000</td>
      <td>241272000000</td>
      <td>193437000000</td>
      <td>171124000000</td>
    </tr>
    <tr>
      <th>commonStock</th>
      <td>40201000000</td>
      <td>35867000000</td>
      <td>31251000000</td>
      <td>27416000000</td>
    </tr>
    <tr>
      <th>retainedEarnings</th>
      <td>70400000000</td>
      <td>98330000000</td>
      <td>96364000000</td>
      <td>92284000000</td>
    </tr>
    <tr>
      <th>shareholderEquity</th>
      <td>107147000000</td>
      <td>134047000000</td>
      <td>128249000000</td>
      <td>119355000000</td>
    </tr>
    <tr>
      <th>netTangibleAssets</th>
      <td>107147000000</td>
      <td>115006000000</td>
      <td>108409000000</td>
      <td>100898000000</td>
    </tr>
  </tbody>
</table>
</div>



```python

```
