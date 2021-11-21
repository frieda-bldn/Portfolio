### Plotting in Python - Seaborn

1. Download of all necessary libraries
2. Loading data of the csv file via list comprehension and reading it into the dataframe df
3. Using the panda method .describe()


```python
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
import glob
```


```python
df = pd.concat([pd.read_csv(f) for f in glob.glob('Lessons/10 - Vizualization/data/ldt_s??_data.csv')], ignore_index=True)
df.describe()
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
      <th>RT</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>250.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.693857</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.155706</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.290267</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.587107</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.695936</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.801115</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.109028</td>
    </tr>
  </tbody>
</table>
</div>



4. Using seaborns .displot() function to create a histogram and plot the corresponding probabilities


```python
sns.displot(data=df, x='RT',
           bins=25,
           color='red')
plt.show()

sns.displot(data=df, x='RT',
           stat='probability')
plt.show()
```




    
![png](Github%20Portfolio_files/Github%20Portfolio_5_0.png)
    






    
![png](Github%20Portfolio_files/Github%20Portfolio_5_1.png)
    



5. Grouping data by condition


```python
sns.displot(kind='kde',
           data=df,
           x='RT', hue='condition',
           palette='colorblind')
plt.show()
```




    
![png](Github%20Portfolio_files/Github%20Portfolio_7_0.png)
    



6. Drawing box plots and violine plots


```python
sns.catplot(kind='box',
           data=df,
           x='condition', y='RT')
plt.show()

sns.catplot(kind='violin',
           data=df,
           x='condition', y='RT')
plt.show()
```




    
![png](Github%20Portfolio_files/Github%20Portfolio_9_0.png)
    






    
![png](Github%20Portfolio_files/Github%20Portfolio_9_1.png)
    



7. Strip vs. swarm plots, where the latter ones illustrate the distribution laterally in a more observable way


```python
sns.catplot(kind='strip',
           data=df,
           x='condition', y='RT')
plt.show()

sns.catplot(kind='swarm',
           data=df,
           x='condition', y='RT')
plt.show()
```




    
![png](Github%20Portfolio_files/Github%20Portfolio_11_0.png)
    






    
![png](Github%20Portfolio_files/Github%20Portfolio_11_1.png)
    



8. Bar plots focus on conditions rather than distributions, and point/line plots are appropriate for comparing means or related conditions


```python
sns.catplot(kind='bar',
           data=df,
           x='condition', y='RT')
plt.show()

sns.catplot(kind='point', join=False, hue='condition',
           data=df,
           x='condition', y='RT')
plt.show()
```




    
![png](Github%20Portfolio_files/Github%20Portfolio_13_0.png)
    






    
![png](Github%20Portfolio_files/Github%20Portfolio_13_1.png)
    




```python

```
