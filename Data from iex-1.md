

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
|                          |    2018-09-30        |     2017-09-30     |     2016-09-30      |    2015-09-30             | 
|-------------------------|-----------------------|-----------------------|-----------------------|-----------------------| 
| currentCash             |  $25,913,000,000.00   |  $20,289,000,000.00   |  $20,484,000,000.00   |  $21,120,000,000.00   | 
| shortTermInvestments    |  $40,388,000,000.00   |  $53,892,000,000.00   |  $46,671,000,000.00   |  $20,481,000,000.00   | 
| receivables             |  $23,186,000,000.00   |  $17,874,000,000.00   |  $15,754,000,000.00   |  $16,849,000,000.00   | 
| inventory               |  $3,956,000,000.00    |  $4,855,000,000.00    |  $2,132,000,000.00    |  $2,349,000,000.00    | 
| otherCurrentAssets      |  $12,087,000,000.00   |  $13,936,000,000.00   |  $8,283,000,000.00    |  $15,085,000,000.00   | 
| currentAssets           |  $131,339,000,000.00  |  $128,645,000,000.00  |  $106,869,000,000.00  |  $89,378,000,000.00   | 
| longTermInvestments     |  $170,799,000,000.00  |  $194,714,000,000.00  |  $170,430,000,000.00  |  $164,065,000,000.00  | 
| propertyPlantEquipment  |  $41,304,000,000.00   |  $33,783,000,000.00   |  $27,010,000,000.00   |  $22,471,000,000.00   | 
| goodwill                |                       |  $5,717,000,000.00    |  $5,414,000,000.00    |  $5,116,000,000.00    | 
| intangibleAssets        |                       |  $2,298,000,000.00    |  $3,206,000,000.00    |  $3,893,000,000.00    | 
| otherAssets             |  $22,283,000,000.00   |  $10,162,000,000.00   |  $8,757,000,000.00    |  $5,556,000,000.00    | 
| totalAssets             |  $365,725,000,000.00  |  $375,319,000,000.00  |  $321,686,000,000.00  |  $290,479,000,000.00  | 
| accountsPayable         |  $55,888,000,000.00   |  $49,049,000,000.00   |  $37,294,000,000.00   |  $35,490,000,000.00   | 
| currentLongTermDebt     |  $8,784,000,000.00    |  $6,496,000,000.00    |  $3,500,000,000.00    |  $2,500,000,000.00    | 
| otherCurrentLiabilities |  $40,230,000,000.00   |  $33,292,000,000.00   |  $30,107,000,000.00   |  $34,121,000,000.00   | 
| totalCurrentLiabilities |  $116,866,000,000.00  |  $100,814,000,000.00  |  $79,006,000,000.00   |  $80,610,000,000.00   | 
| longTermDebt            |  $93,735,000,000.00   |  $97,207,000,000.00   |  $75,427,000,000.00   |  $53,463,000,000.00   | 
| otherLiabilities        |  $4,268,000,000.00    |  $3,340,000,000.00    |  $4,285,000,000.00    |  $4,789,000,000.00    | 
| minorityInterest        |  $-                   |  $-                   |  $-                   |  $-                   | 
| totalLiabilities        |  $258,578,000,000.00  |  $241,272,000,000.00  |  $193,437,000,000.00  |  $171,124,000,000.00  | 
| commonStock             |  $40,201,000,000.00   |  $35,867,000,000.00   |  $31,251,000,000.00   |  $27,416,000,000.00   | 
| retainedEarnings        |  $70,400,000,000.00   |  $98,330,000,000.00   |  $96,364,000,000.00   |  $92,284,000,000.00   | 
| treasuryStock           |                       |                       |                       |                       | 
| capitalSurplus          |                       |                       |                       |                       | 
| shareholderEquity       |  $107,147,000,000.00  |  $134,047,000,000.00  |  $128,249,000,000.00  |  $119,355,000,000.00  | 
| netTangibleAssets       |  $107,147,000,000.00  |  $115,006,000,000.00  |  $108,409,000,000.00  |  $100,898,000,000.00  | 

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
