# Scrape the web with Python, BeautifulSoup, Pandas and Selenium
## Youtube: https://www.youtube.com/watch?v=yMEMUf3vEvc


```
!pip install kora
from kora.selenium import wd
```

    Requirement already satisfied: kora in /usr/local/lib/python3.6/dist-packages (0.9.13)
    Requirement already satisfied: fastcore in /usr/local/lib/python3.6/dist-packages (from kora) (1.3.13)
    Requirement already satisfied: ipython in /usr/local/lib/python3.6/dist-packages (from kora) (5.5.0)
    Requirement already satisfied: packaging in /usr/local/lib/python3.6/dist-packages (from fastcore->kora) (20.8)
    Requirement already satisfied: pip in /usr/local/lib/python3.6/dist-packages (from fastcore->kora) (19.3.1)
    Requirement already satisfied: prompt-toolkit<2.0.0,>=1.0.4 in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (1.0.18)
    Requirement already satisfied: traitlets>=4.2 in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (4.3.3)
    Requirement already satisfied: pygments in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (2.6.1)
    Requirement already satisfied: pickleshare in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (0.7.5)
    Requirement already satisfied: simplegeneric>0.8 in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (0.8.1)
    Requirement already satisfied: decorator in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (4.4.2)
    Requirement already satisfied: pexpect; sys_platform != "win32" in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (4.8.0)
    Requirement already satisfied: setuptools>=18.5 in /usr/local/lib/python3.6/dist-packages (from ipython->kora) (50.3.2)
    Requirement already satisfied: pyparsing>=2.0.2 in /usr/local/lib/python3.6/dist-packages (from packaging->fastcore->kora) (2.4.7)
    Requirement already satisfied: six>=1.9.0 in /usr/local/lib/python3.6/dist-packages (from prompt-toolkit<2.0.0,>=1.0.4->ipython->kora) (1.15.0)
    Requirement already satisfied: wcwidth in /usr/local/lib/python3.6/dist-packages (from prompt-toolkit<2.0.0,>=1.0.4->ipython->kora) (0.2.5)
    Requirement already satisfied: ipython-genutils in /usr/local/lib/python3.6/dist-packages (from traitlets>=4.2->ipython->kora) (0.2.0)
    Requirement already satisfied: ptyprocess>=0.5 in /usr/local/lib/python3.6/dist-packages (from pexpect; sys_platform != "win32"->ipython->kora) (0.6.0)



```
url = "https://catalogo.museivaticani.va/opere/"

wd.get(url)
wd.implicitly_wait(30)

search_field = wd.find_element_by_id("id_ac_descrizione")
search_field.send_keys("Nativita")
searchButton = wd.find_element_by_id("sc_b_pesq_bot")
searchButton.click()
table = wd.find_element_by_class_name("scGridTabela")
wd.save_screenshot("screenshot.png")
```




    True



## Read Panda Dataframe from HTML


```
import pandas as pd

df = pd.read_html(wd.page_source, attrs= { 'class': 'scGridTabela'})
df[0]
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>Immagine</td>
      <td>Autore</td>
      <td>Descrizione/Titolo</td>
      <td>Datazione</td>
      <td>Materia</td>
      <td>Inventario</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>Scuola Senese</td>
      <td>Scomparto di predella con Storie della Vergine...</td>
      <td>prima metà sec. XV</td>
      <td>tempera su tavola, cornice dorata</td>
      <td>MV_40237_0_0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mariotto di Nardo (Firenze 1365 ca. - 1424/1427)</td>
      <td>Scomparto di predella con Storie della Vergine...</td>
      <td>1385 ca.</td>
      <td>tempera e oro su tavola di pioppo</td>
      <td>MV_40102_0_0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>66</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>67</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>Raffaellino del Colle (Sansepolcro, fine sec. ...</td>
      <td>Natività con adorazione dei Magi</td>
      <td>secondo terzo sec. XVI</td>
      <td>olio su tavola trasportata su tela, cornice in...</td>
      <td>MV_41138_0_0</td>
    </tr>
    <tr>
      <th>68</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>69</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>Raffaellino del Colle (Sansepolcro, fine sec. ...</td>
      <td>Cartone preparatorio: Natività con adorazione ...</td>
      <td>secondo terzo sec. XVI</td>
      <td>matita e carboncino con lumeggiature a biacca ...</td>
      <td>MV_56507_0_0</td>
    </tr>
    <tr>
      <th>70</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>71 rows × 7 columns</p>
</div>



## Parse table and create Panda Dataframe using BeautifulSoap



```
from bs4 import BeautifulSoup

soup = BeautifulSoup(wd.page_source)

table = soup.find("table",{"class": "scGridTabela"})

table_processed = []

for row in table.findAll("tr")[1:]:
  row_processed = []
  cells = row.findAll("td")
  if len(cells) > 3:
    img_url = "https://catalogo.museivaticani.va/" + cells[3].find("img")["src"]
    row_processed.append(img_url)
    img_origin = "https://catalogo.museivaticani.va/opere/"
    row_processed.append(img_origin)
    table_processed.append(row_processed)
  

columns = ["ImageUrl","Origin"]

df = pd.DataFrame.from_records(table_processed, columns= columns)

df
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
      <th>ImageUrl</th>
      <th>Origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>5</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>6</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>7</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>8</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>9</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>10</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>11</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>12</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>13</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>14</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>15</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>16</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>17</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>18</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>19</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>20</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>21</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>22</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>23</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>24</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>25</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>26</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>27</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>28</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>29</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>30</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>31</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>32</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>33</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>34</th>
      <td>https://catalogo.museivaticani.va//_lib/tmp/sc...</td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
  </tbody>
</table>
</div>



## Visualise Panda Dataframe by converting to HTML


```
def url_to_image_html(imageUrl):
  return f"<img src='{imageUrl}' width='120'/>"



from IPython.core.display import HTML
HTML(df.to_html(escape=False, formatters=dict(ImageUrl=url_to_image_html)))
```




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ImageUrl</th>
      <th>Origin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>1</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>2</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>3</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>4</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>5</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>6</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>7</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>8</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>9</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>10</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>11</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>12</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>13</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>14</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>15</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>16</th>
      <td><img src='hhttps://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>17</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>18</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>19</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>20</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>21</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>22</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>23</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>24</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>25</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>26</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>27</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>28</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>29</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>30</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>31</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>32</th>
      <td><img src='hhttps://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>33</th>
      <td><img src='https://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
    <tr>
      <th>34</th>
      <td><img src='hhttps://dummyimage.com/600x400/000/fff' width='120'/></td>
      <td>https://catalogo.museivaticani.va/opere/</td>
    </tr>
  </tbody>
</table>



## Convert Panda DataFrame to CSV


```
df.to_csv("results.csv")
```
