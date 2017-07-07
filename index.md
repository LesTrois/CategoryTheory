# Teoria de Categorización
## Nociones básicas

### Olog

Es el concepto fundamental que se considera al hablar de __Teoria de la Categorización__ pues se trabaja con relaciones de conjuntos, los cuales son considerados __Tipos__.

#### Tipos
Estos `tipos`  si bien no representa a solo a un objeto, lo que hace es englobar a estas unidades representandolas como una clasa  Clase y de las cuales se relacionan con otros Tipos por las caracteristicas que poseen ellas, además de que tambien establecen relacion entre ellas por las similitudes que presentan.

## Base de Datos

Una __Base de datos__ es un conjunto de información organizado y ordenados en tablas, donde las __tablas__ son un conjunto de Columnas o campos y un conjunto de __Filas__ u objetos , quienes han sido juntados debido a las caracteristicas similares que presentan que nos hace relacionarlo con el concepto abstracto `Tipo`.


```python
import pandas as pd
from blaze import data,by,join,merge ,concat
```


```python
crime = data('crime.csv')
type(crime)
```




    blaze.interactive._Data



## Tabla de Crimenes


```python
crime.head()
```




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cdatetime</th>
      <th>address</th>
      <th>district</th>
      <th>beat</th>
      <th>grid</th>
      <th>crimedescr</th>
      <th>ucr_ncic_code</th>
      <th>latitude</th>
      <th>longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2006-01-01</td>
      <td>3108 OCCIDENTAL DR</td>
      <td>3</td>
      <td>3C</td>
      <td>1115</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.550420</td>
      <td>-121.391416</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2006-01-01</td>
      <td>2082 EXPEDITION WAY</td>
      <td>5</td>
      <td>5A</td>
      <td>1512</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>2204</td>
      <td>38.473501</td>
      <td>-121.490186</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2006-01-01</td>
      <td>4 PALEN CT</td>
      <td>2</td>
      <td>2A</td>
      <td>212</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.657846</td>
      <td>-121.462101</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2006-01-01</td>
      <td>22 BECKFORD CT</td>
      <td>6</td>
      <td>6C</td>
      <td>1443</td>
      <td>476 PC PASS FICTICIOUS CHECK</td>
      <td>2501</td>
      <td>38.506774</td>
      <td>-121.426951</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2006-01-01</td>
      <td>3421 AUBURN BLVD</td>
      <td>2</td>
      <td>2A</td>
      <td>508</td>
      <td>459 PC  BURGLARY-UNSPECIFIED</td>
      <td>2299</td>
      <td>38.637448</td>
      <td>-121.384613</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2006-01-01</td>
      <td>5301 BONNIEMAE WAY</td>
      <td>6</td>
      <td>6B</td>
      <td>1084</td>
      <td>530.5 PC USE PERSONAL ID INFO</td>
      <td>2604</td>
      <td>38.526979</td>
      <td>-121.451338</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2006-01-01</td>
      <td>2217 16TH AVE</td>
      <td>4</td>
      <td>4A</td>
      <td>957</td>
      <td>459 PC  BURGLARY VEHICLE</td>
      <td>2299</td>
      <td>38.537173</td>
      <td>-121.487577</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2006-01-01</td>
      <td>3547 P ST</td>
      <td>3</td>
      <td>3C</td>
      <td>853</td>
      <td>484 PC   PETTY THEFT/INSIDE</td>
      <td>2308</td>
      <td>38.564335</td>
      <td>-121.461883</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2006-01-01</td>
      <td>3421 AUBURN BLVD</td>
      <td>2</td>
      <td>2A</td>
      <td>508</td>
      <td>459 PC  BURGLARY BUSINESS</td>
      <td>2203</td>
      <td>38.637448</td>
      <td>-121.384613</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2006-01-01</td>
      <td>1326 HELMSMAN WAY</td>
      <td>1</td>
      <td>1B</td>
      <td>444</td>
      <td>1708 US   THEFT OF MAIL</td>
      <td>2310</td>
      <td>38.609602</td>
      <td>-121.491838</td>
    </tr>
  </tbody>
</table>



## Operación de selección 
En el tabla consultaremos los crimenes que ocurrieron en el distrito 5.


```python
cd5=crime[crime.district==5]
cd5
```




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>cdatetime</th>
      <th>address</th>
      <th>district</th>
      <th>beat</th>
      <th>grid</th>
      <th>crimedescr</th>
      <th>ucr_ncic_code</th>
      <th>latitude</th>
      <th>longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>2006-01-01 00:00:00</td>
      <td>2082 EXPEDITION WAY</td>
      <td>5</td>
      <td>5A</td>
      <td>1512</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>2204</td>
      <td>38.473501</td>
      <td>-121.490186</td>
    </tr>
    <tr>
      <th>20</th>
      <td>2006-01-01 00:01:00</td>
      <td>5551 REXLEIGH CT</td>
      <td>5</td>
      <td>5C</td>
      <td>1661</td>
      <td>459 PC  BURGLARY VEHICLE</td>
      <td>2299</td>
      <td>38.446592</td>
      <td>-121.442378</td>
    </tr>
    <tr>
      <th>24</th>
      <td>2006-01-01 00:01:00</td>
      <td>15 BASIN CT</td>
      <td>5</td>
      <td>5C</td>
      <td>1654</td>
      <td>TRAFFIC - I RPT</td>
      <td>7000</td>
      <td>38.442815</td>
      <td>-121.409524</td>
    </tr>
    <tr>
      <th>26</th>
      <td>2006-01-01 00:01:00</td>
      <td>4280 DEER HILL DR</td>
      <td>5</td>
      <td>5B</td>
      <td>1616</td>
      <td>484G(B) PC ACCESS CARD FRAUD</td>
      <td>2605</td>
      <td>38.471219</td>
      <td>-121.454739</td>
    </tr>
    <tr>
      <th>28</th>
      <td>2006-01-01 00:01:00</td>
      <td>1816 FLORIN RD</td>
      <td>5</td>
      <td>5A</td>
      <td>1361</td>
      <td>HARASSMENT - I RPT</td>
      <td>7000</td>
      <td>38.495353</td>
      <td>-121.496560</td>
    </tr>
    <tr>
      <th>52</th>
      <td>2006-01-01 00:30:00</td>
      <td>6571 WEATHERFORD WAY</td>
      <td>5</td>
      <td>5C</td>
      <td>1635</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.466373</td>
      <td>-121.426527</td>
    </tr>
    <tr>
      <th>57</th>
      <td>2006-01-01 00:39:00</td>
      <td>7811 DEER MEADOW DR</td>
      <td>5</td>
      <td>5B</td>
      <td>1616</td>
      <td>246 PC SHOOT OCCUP DWELL/VEH</td>
      <td>5213</td>
      <td>38.474000</td>
      <td>-121.458193</td>
    </tr>
    <tr>
      <th>66</th>
      <td>2006-01-01 01:06:00</td>
      <td>4740 BECKET WAY</td>
      <td>5</td>
      <td>5B</td>
      <td>1631</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>2204</td>
      <td>38.465181</td>
      <td>-121.446165</td>
    </tr>
    <tr>
      <th>67</th>
      <td>2006-01-01 01:30:00</td>
      <td>CALVINE RD / CENTER PKWY</td>
      <td>5</td>
      <td>5C</td>
      <td>1645</td>
      <td>243(D) PC BATT/CIVILIAN W/INJ</td>
      <td>1315</td>
      <td>38.449721</td>
      <td>-121.425872</td>
    </tr>
    <tr>
      <th>68</th>
      <td>2006-01-01 01:30:00</td>
      <td>6625 VALLEY HI DR</td>
      <td>5</td>
      <td>5C</td>
      <td>1623</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.471437</td>
      <td>-121.427615</td>
    </tr>
    <tr>
      <th>70</th>
      <td>2006-01-01 02:00:00</td>
      <td>2500 FLORIN RD</td>
      <td>5</td>
      <td>5A</td>
      <td>1363</td>
      <td>487(A) PC GRAND THEFT</td>
      <td>2303</td>
      <td>38.495710</td>
      <td>-121.477826</td>
    </tr>
  </tbody>
</table>



## Proyección


```python
crime[['address','crimedescr','latitude','longitude']].head()
```




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>address</th>
      <th>crimedescr</th>
      <th>latitude</th>
      <th>longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3108 OCCIDENTAL DR</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>38.550420</td>
      <td>-121.391416</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2082 EXPEDITION WAY</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>38.473501</td>
      <td>-121.490186</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4 PALEN CT</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>38.657846</td>
      <td>-121.462101</td>
    </tr>
    <tr>
      <th>3</th>
      <td>22 BECKFORD CT</td>
      <td>476 PC PASS FICTICIOUS CHECK</td>
      <td>38.506774</td>
      <td>-121.426951</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3421 AUBURN BLVD</td>
      <td>459 PC  BURGLARY-UNSPECIFIED</td>
      <td>38.637448</td>
      <td>-121.384613</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5301 BONNIEMAE WAY</td>
      <td>530.5 PC USE PERSONAL ID INFO</td>
      <td>38.526979</td>
      <td>-121.451338</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2217 16TH AVE</td>
      <td>459 PC  BURGLARY VEHICLE</td>
      <td>38.537173</td>
      <td>-121.487577</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3547 P ST</td>
      <td>484 PC   PETTY THEFT/INSIDE</td>
      <td>38.564335</td>
      <td>-121.461883</td>
    </tr>
    <tr>
      <th>8</th>
      <td>3421 AUBURN BLVD</td>
      <td>459 PC  BURGLARY BUSINESS</td>
      <td>38.637448</td>
      <td>-121.384613</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1326 HELMSMAN WAY</td>
      <td>1708 US   THEFT OF MAIL</td>
      <td>38.609602</td>
      <td>-121.491838</td>
    </tr>
  </tbody>
</table>



## Group by


```python
by(crime.district,latitude=crime.latitude.mean())
```




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>district</th>
      <th>latitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>38.633072</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>38.623198</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>38.573090</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>38.523797</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>38.473954</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>38.533416</td>
    </tr>
  </tbody>
</table>



## Join


```python
join(crime,cd5,'address')
```




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>address</th>
      <th>cdatetime_left</th>
      <th>district_left</th>
      <th>beat_left</th>
      <th>grid_left</th>
      <th>crimedescr_left</th>
      <th>ucr_ncic_code_left</th>
      <th>latitude_left</th>
      <th>longitude_left</th>
      <th>cdatetime_right</th>
      <th>district_right</th>
      <th>beat_right</th>
      <th>grid_right</th>
      <th>crimedescr_right</th>
      <th>ucr_ncic_code_right</th>
      <th>latitude_right</th>
      <th>longitude_right</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2082 EXPEDITION WAY</td>
      <td>2006-01-01 00:00:00</td>
      <td>5</td>
      <td>5A</td>
      <td>1512</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>2204</td>
      <td>38.473501</td>
      <td>-121.490186</td>
      <td>2006-01-01 00:00:00</td>
      <td>5</td>
      <td>5A</td>
      <td>1512</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>2204</td>
      <td>38.473501</td>
      <td>-121.490186</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5551 REXLEIGH CT</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1661</td>
      <td>459 PC  BURGLARY VEHICLE</td>
      <td>2299</td>
      <td>38.446592</td>
      <td>-121.442378</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1661</td>
      <td>459 PC  BURGLARY VEHICLE</td>
      <td>2299</td>
      <td>38.446592</td>
      <td>-121.442378</td>
    </tr>
    <tr>
      <th>2</th>
      <td>15 BASIN CT</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1654</td>
      <td>TRAFFIC - I RPT</td>
      <td>7000</td>
      <td>38.442815</td>
      <td>-121.409524</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1654</td>
      <td>TRAFFIC - I RPT</td>
      <td>7000</td>
      <td>38.442815</td>
      <td>-121.409524</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4280 DEER HILL DR</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5B</td>
      <td>1616</td>
      <td>484G(B) PC ACCESS CARD FRAUD</td>
      <td>2605</td>
      <td>38.471219</td>
      <td>-121.454739</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5B</td>
      <td>1616</td>
      <td>484G(B) PC ACCESS CARD FRAUD</td>
      <td>2605</td>
      <td>38.471219</td>
      <td>-121.454739</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1816 FLORIN RD</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5A</td>
      <td>1361</td>
      <td>HARASSMENT - I RPT</td>
      <td>7000</td>
      <td>38.495353</td>
      <td>-121.496560</td>
      <td>2006-01-01 00:01:00</td>
      <td>5</td>
      <td>5A</td>
      <td>1361</td>
      <td>HARASSMENT - I RPT</td>
      <td>7000</td>
      <td>38.495353</td>
      <td>-121.496560</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6571 WEATHERFORD WAY</td>
      <td>2006-01-01 00:30:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1635</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.466373</td>
      <td>-121.426527</td>
      <td>2006-01-01 00:30:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1635</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.466373</td>
      <td>-121.426527</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7811 DEER MEADOW DR</td>
      <td>2006-01-01 00:39:00</td>
      <td>5</td>
      <td>5B</td>
      <td>1616</td>
      <td>246 PC SHOOT OCCUP DWELL/VEH</td>
      <td>5213</td>
      <td>38.474000</td>
      <td>-121.458193</td>
      <td>2006-01-01 00:39:00</td>
      <td>5</td>
      <td>5B</td>
      <td>1616</td>
      <td>246 PC SHOOT OCCUP DWELL/VEH</td>
      <td>5213</td>
      <td>38.474000</td>
      <td>-121.458193</td>
    </tr>
    <tr>
      <th>7</th>
      <td>4740 BECKET WAY</td>
      <td>2006-01-01 01:06:00</td>
      <td>5</td>
      <td>5B</td>
      <td>1631</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>2204</td>
      <td>38.465181</td>
      <td>-121.446165</td>
      <td>2006-01-01 01:06:00</td>
      <td>5</td>
      <td>5B</td>
      <td>1631</td>
      <td>459 PC  BURGLARY RESIDENCE</td>
      <td>2204</td>
      <td>38.465181</td>
      <td>-121.446165</td>
    </tr>
    <tr>
      <th>8</th>
      <td>CALVINE RD / CENTER PKWY</td>
      <td>2006-01-01 01:30:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1645</td>
      <td>243(D) PC BATT/CIVILIAN W/INJ</td>
      <td>1315</td>
      <td>38.449721</td>
      <td>-121.425872</td>
      <td>2006-01-01 01:30:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1645</td>
      <td>243(D) PC BATT/CIVILIAN W/INJ</td>
      <td>1315</td>
      <td>38.449721</td>
      <td>-121.425872</td>
    </tr>
    <tr>
      <th>9</th>
      <td>6625 VALLEY HI DR</td>
      <td>2006-01-01 01:30:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1623</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.471437</td>
      <td>-121.427615</td>
      <td>2006-01-01 01:30:00</td>
      <td>5</td>
      <td>5C</td>
      <td>1623</td>
      <td>10851(A)VC TAKE VEH W/O OWNER</td>
      <td>2404</td>
      <td>38.471437</td>
      <td>-121.427615</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2500 FLORIN RD</td>
      <td>2006-01-01 02:00:00</td>
      <td>5</td>
      <td>5A</td>
      <td>1363</td>
      <td>487(A) PC GRAND THEFT</td>
      <td>2303</td>
      <td>38.495710</td>
      <td>-121.477826</td>
      <td>2006-01-01 02:00:00</td>
      <td>5</td>
      <td>5A</td>
      <td>1363</td>
      <td>487(A) PC GRAND THEFT</td>
      <td>2303</td>
      <td>38.495710</td>
      <td>-121.477826</td>
    </tr>
  </tbody>
</table>



You can use the [editor on GitHub](https://github.com/LesTrois/CategoryTheory/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/LesTrois/CategoryTheory/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
