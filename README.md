# Analisis Data Penjualan Pizza

## Deskripsi

Dalam proyek ini, kita akan melakukan analisis pada data penjualan pizza menggunakan Python dan beberapa pustaka populer.

## Kode untuk Memuat dan Menampilkan Data

Berikut adalah kode untuk memuat data dari file CSV dan menampilkan lima baris pertama:

```python
# Library yang dibutuhkan
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Memuat data dari file CSV
df = pd.read_csv('E:/semester 3/IPUSD/archive/pizza_sales.csv')

# Menampilkan lima baris pertama dari DataFrame
df.head()
```
<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pizza_id</th>
      <th>order_id</th>
      <th>pizza_name_id</th>
      <th>quantity</th>
      <th>order_date</th>
      <th>order_time</th>
      <th>unit_price</th>
      <th>total_price</th>
      <th>pizza_size</th>
      <th>pizza_category</th>
      <th>pizza_ingredients</th>
      <th>pizza_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>hawaiian_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:38:36</td>
      <td>13.25</td>
      <td>13.25</td>
      <td>M</td>
      <td>Classic</td>
      <td>Sliced Ham, Pineapple, Mozzarella Cheese</td>
      <td>The Hawaiian Pizza</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>2.0</td>
      <td>classic_dlx_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Classic</td>
      <td>Pepperoni, Mushrooms, Red Onions, Red Peppers,...</td>
      <td>The Classic Deluxe Pizza</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>five_cheese_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>18.50</td>
      <td>18.50</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Mozzarella Cheese, Provolone Cheese, Smoked Go...</td>
      <td>The Five Cheese Pizza</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>2.0</td>
      <td>ital_supr_l</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Calabrese Salami, Capocollo, Tomatoes, Red Oni...</td>
      <td>The Italian Supreme Pizza</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>2.0</td>
      <td>mexicana_m</td>
      <td>1.0</td>
      <td>1/1/2015</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Veggie</td>
      <td>Tomatoes, Red Peppers, Jalapeno Peppers, Red O...</td>
      <td>The Mexicana Pizza</td>
    </tr>
  </tbody>
</table>
</div>

# Tampilkan 5 baris pertama data
```python
df.head()
```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>pizza_id</th>
      <th>order_id</th>
      <th>pizza_name_id</th>
      <th>quantity</th>
      <th>order_date</th>
      <th>order_time</th>
      <th>unit_price</th>
      <th>total_price</th>
      <th>pizza_size</th>
      <th>pizza_category</th>
      <th>pizza_ingredients</th>
      <th>pizza_name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>hawaiian_m</td>
      <td>1.0</td>
      <td>2015-01-01</td>
      <td>11:38:36</td>
      <td>13.25</td>
      <td>13.25</td>
      <td>M</td>
      <td>Classic</td>
      <td>Sliced Ham, Pineapple, Mozzarella Cheese</td>
      <td>The Hawaiian Pizza</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>2.0</td>
      <td>classic_dlx_m</td>
      <td>1.0</td>
      <td>2015-01-01</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Classic</td>
      <td>Pepperoni, Mushrooms, Red Onions, Red Peppers,...</td>
      <td>The Classic Deluxe Pizza</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>five_cheese_l</td>
      <td>1.0</td>
      <td>2015-01-01</td>
      <td>11:57:40</td>
      <td>18.50</td>
      <td>18.50</td>
      <td>L</td>
      <td>Veggie</td>
      <td>Mozzarella Cheese, Provolone Cheese, Smoked Go...</td>
      <td>The Five Cheese Pizza</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>2.0</td>
      <td>ital_supr_l</td>
      <td>1.0</td>
      <td>2015-01-01</td>
      <td>11:57:40</td>
      <td>20.75</td>
      <td>20.75</td>
      <td>L</td>
      <td>Supreme</td>
      <td>Calabrese Salami, Capocollo, Tomatoes, Red Oni...</td>
      <td>The Italian Supreme Pizza</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>2.0</td>
      <td>mexicana_m</td>
      <td>1.0</td>
      <td>2015-01-01</td>
      <td>11:57:40</td>
      <td>16.00</td>
      <td>16.00</td>
      <td>M</td>
      <td>Veggie</td>
      <td>Tomatoes, Red Peppers, Jalapeno Peppers, Red O...</td>
      <td>The Mexicana Pizza</td>
    </tr>
  </tbody>
</table>
</div>

# Mengonversi kolom order_date ke format datetime dengan penanganan kesalahan
```python
df['order_date'] = pd.to_datetime(df['order_date'], format='%d/%m/%Y', errors='coerce')
```
```python
# Cek apakah ada nilai yang menjadi NaT
print(f"Jumlah nilai NaT dalam order_date: {df['order_date'].isna().sum()}")
```
Jumlah nilai NaT dalam order_date: 29033
# Memisahkan data berdasarkan kategori pizza
```python
classic_prices = df[df['pizza_category'] == 'Classic']['total_price']
veggie_prices = df[df['pizza_category'] == 'Veggie']['total_price']
```
# Menghitung statistik dasar
```pyhton
mean_classic = classic_prices.mean()
mean_veggie = veggie_prices.mean()
std_classic = classic_prices.std()
std_veggie = veggie_prices.std()
```
# Uji t untuk membandingkan rata-rata
```python
t_stat, p_value = stats.ttest_ind(classic_prices, veggie_prices)
```
# Menampilkan hasil analisis statistik
```python
print("Statistik Pizza Classic:")
print(f"Rata-rata: {mean_classic}, Standar Deviasi: {std_classic}")
print("\nStatistik Pizza Veggie:")
print(f"Rata-rata: {mean_veggie}, Standar Deviasi: {std_veggie}")
print("\nHasil Uji t:")
print(f"T-statistik: {t_stat}, P-value: {p_value}")
```
Statistik Pizza Classic:
Rata-rata: 15.093840455449618, Standar Deviasi: 4.519287728971544

Statistik Pizza Veggie:
Rata-rata: 16.91767403266661, Standar Deviasi: 3.8534821751461728

Hasil Uji t:
T-statistik: -34.45212078967407, P-value: 2.1675051843498843e-254








