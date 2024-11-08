```python
import pandas as pd
import matplotlib.pyplot as plt
import plotly.express as px
import numpy as np

```


```python

#get df
dataf = pd.read_csv("https://query.data.world/s/atsel7i6wsljadsc5nbul2skjl6f2d?dws=00000")

#grab every country by the same year
df2010 = dataf[dataf["year"] == 2010]

#get new df with columns name and religious generalizations for the year 2000
religiongenpct_columns = [col for col in df2010.columns if col == ("chrstgenpct") or col == ("islmgenpct") or col == ("budgenpct") or col==("hindgenpct") or col==("sikhgenpct") or col==("judgenpct") or col==("confgenpct") or col==("othrgenpct") or col==("nonreligpct") or col==("sumreligpct")]
new_dfgenpct = df2010[["name"] + religiongenpct_columns]
new_dfgenpct.reset_index(drop=True, inplace=True)
new_dfgenpct
```





  <div id="df-89edaf01-4897-458e-8fd1-657d8222f20d" class="colab-df-container">
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
      <th>name</th>
      <th>chrstgenpct</th>
      <th>judgenpct</th>
      <th>islmgenpct</th>
      <th>budgenpct</th>
      <th>hindgenpct</th>
      <th>sikhgenpct</th>
      <th>confgenpct</th>
      <th>nonreligpct</th>
      <th>othrgenpct</th>
      <th>sumreligpct</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USA</td>
      <td>0.7454</td>
      <td>0.0190</td>
      <td>0.0090</td>
      <td>0.0109</td>
      <td>0.0057</td>
      <td>0.0013</td>
      <td>0.0003</td>
      <td>0.1900</td>
      <td>0.0025</td>
      <td>0.9975</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CAN</td>
      <td>0.7661</td>
      <td>0.0099</td>
      <td>0.0194</td>
      <td>0.0194</td>
      <td>0.0080</td>
      <td>0.0080</td>
      <td>0.0001</td>
      <td>0.1643</td>
      <td>0.0010</td>
      <td>0.9990</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BHM</td>
      <td>0.9660</td>
      <td>0.0010</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0290</td>
      <td>0.0005</td>
      <td>0.9995</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CUB</td>
      <td>0.6589</td>
      <td>0.0001</td>
      <td>0.0007</td>
      <td>0.0000</td>
      <td>0.0022</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1315</td>
      <td>0.0000</td>
      <td>1.2935</td>
    </tr>
    <tr>
      <th>4</th>
      <td>HAI</td>
      <td>0.8200</td>
      <td>0.0000</td>
      <td>0.0002</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1000</td>
      <td>0.0000</td>
      <td>1.3711</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>189</th>
      <td>NAU</td>
      <td>0.9699</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0301</td>
      <td>0.9699</td>
    </tr>
    <tr>
      <th>190</th>
      <td>MSI</td>
      <td>0.9341</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0220</td>
      <td>0.0017</td>
      <td>0.9983</td>
    </tr>
    <tr>
      <th>191</th>
      <td>PAL</td>
      <td>0.8606</td>
      <td>0.0000</td>
      <td>0.0220</td>
      <td>0.0085</td>
      <td>0.0013</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0153</td>
      <td>0.0010</td>
      <td>0.9990</td>
    </tr>
    <tr>
      <th>192</th>
      <td>FSM</td>
      <td>0.8651</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0059</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0315</td>
      <td>0.0197</td>
      <td>0.9803</td>
    </tr>
    <tr>
      <th>193</th>
      <td>WSM</td>
      <td>0.9538</td>
      <td>0.0000</td>
      <td>0.0003</td>
      <td>0.0001</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0146</td>
      <td>0.0258</td>
      <td>0.9742</td>
    </tr>
  </tbody>
</table>
<p>194 rows × 11 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-89edaf01-4897-458e-8fd1-657d8222f20d')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-89edaf01-4897-458e-8fd1-657d8222f20d button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-89edaf01-4897-458e-8fd1-657d8222f20d');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-979653e6-8aa9-4d42-baa2-cb2285ba4bc3">
  <button class="colab-df-quickchart" onclick="quickchart('df-979653e6-8aa9-4d42-baa2-cb2285ba4bc3')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-979653e6-8aa9-4d42-baa2-cb2285ba4bc3 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

  <div id="id_e8b4e7f7-4a5b-49eb-8b2e-b9e6cb9c11f0">
    <style>
      .colab-df-generate {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
      }

      .colab-df-generate:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
      }

      [theme=dark] .colab-df-generate {
        background-color: #3B4455;
        fill: #D2E3FC;
      }

      [theme=dark] .colab-df-generate:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
      }
    </style>
    <button class="colab-df-generate" onclick="generateWithVariable('new_dfgenpct')"
            title="Generate code using this dataframe."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M7,19H8.4L18.45,9,17,7.55,7,17.6ZM5,21V16.75L18.45,3.32a2,2,0,0,1,2.83,0l1.4,1.43a1.91,1.91,0,0,1,.58,1.4,1.91,1.91,0,0,1-.58,1.4L9.25,21ZM18.45,9,17,7.55Zm-12,3A5.31,5.31,0,0,0,4.9,8.1,5.31,5.31,0,0,0,1,6.5,5.31,5.31,0,0,0,4.9,4.9,5.31,5.31,0,0,0,6.5,1,5.31,5.31,0,0,0,8.1,4.9,5.31,5.31,0,0,0,12,6.5,5.46,5.46,0,0,0,6.5,12Z"/>
  </svg>
    </button>
    <script>
      (() => {
      const buttonEl =
        document.querySelector('#id_e8b4e7f7-4a5b-49eb-8b2e-b9e6cb9c11f0 button.colab-df-generate');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      buttonEl.onclick = () => {
        google.colab.notebook.generateWithVariable('new_dfgenpct');
      }
      })();
    </script>
  </div>

    </div>
  </div>





```python
gdppercapdf = pd.read_csv("https://pastebin.com/raw/2GAsbJTS")
gdppercapdf.rename(columns={'Country Code': 'name'}, inplace=True)
gdppercapdf
```





  <div id="df-a5989345-4162-42c7-a2f8-f15d7a3e5587" class="colab-df-container">
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
      <th>name</th>
      <th>1995</th>
      <th>2000</th>
      <th>2005</th>
      <th>2010</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AFG</td>
      <td>0.000000</td>
      <td>180.188369</td>
      <td>254.115276</td>
      <td>562.499222</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ALB</td>
      <td>750.604449</td>
      <td>1126.683340</td>
      <td>2673.787816</td>
      <td>4094.349686</td>
    </tr>
    <tr>
      <th>2</th>
      <td>DZA</td>
      <td>1466.544680</td>
      <td>1780.376063</td>
      <td>3248.099814</td>
      <td>4958.259379</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ASM</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>8733.014287</td>
      <td>10446.863206</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AND</td>
      <td>18731.650185</td>
      <td>21674.299722</td>
      <td>39599.680444</td>
      <td>48237.891174</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>212</th>
      <td>VIR</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>40828.746093</td>
      <td>39905.128418</td>
    </tr>
    <tr>
      <th>213</th>
      <td>PSE</td>
      <td>1326.562857</td>
      <td>1476.171850</td>
      <td>1543.701414</td>
      <td>2557.075624</td>
    </tr>
    <tr>
      <th>214</th>
      <td>YEM</td>
      <td>794.639278</td>
      <td>519.591639</td>
      <td>784.757981</td>
      <td>1249.063085</td>
    </tr>
    <tr>
      <th>215</th>
      <td>ZMB</td>
      <td>438.383721</td>
      <td>364.026145</td>
      <td>720.446505</td>
      <td>1469.361450</td>
    </tr>
    <tr>
      <th>216</th>
      <td>ZWE</td>
      <td>646.829560</td>
      <td>565.284390</td>
      <td>470.783761</td>
      <td>937.840340</td>
    </tr>
  </tbody>
</table>
<p>217 rows × 5 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-a5989345-4162-42c7-a2f8-f15d7a3e5587')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-a5989345-4162-42c7-a2f8-f15d7a3e5587 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-a5989345-4162-42c7-a2f8-f15d7a3e5587');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-2c8415b6-831c-41ac-9868-3e1749ad7c97">
  <button class="colab-df-quickchart" onclick="quickchart('df-2c8415b6-831c-41ac-9868-3e1749ad7c97')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-2c8415b6-831c-41ac-9868-3e1749ad7c97 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

  <div id="id_40871a65-9022-4a99-b5a2-44a0c2dd075c">
    <style>
      .colab-df-generate {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
      }

      .colab-df-generate:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
      }

      [theme=dark] .colab-df-generate {
        background-color: #3B4455;
        fill: #D2E3FC;
      }

      [theme=dark] .colab-df-generate:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
      }
    </style>
    <button class="colab-df-generate" onclick="generateWithVariable('gdppercapdf')"
            title="Generate code using this dataframe."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M7,19H8.4L18.45,9,17,7.55,7,17.6ZM5,21V16.75L18.45,3.32a2,2,0,0,1,2.83,0l1.4,1.43a1.91,1.91,0,0,1,.58,1.4,1.91,1.91,0,0,1-.58,1.4L9.25,21ZM18.45,9,17,7.55Zm-12,3A5.31,5.31,0,0,0,4.9,8.1,5.31,5.31,0,0,0,1,6.5,5.31,5.31,0,0,0,4.9,4.9,5.31,5.31,0,0,0,6.5,1,5.31,5.31,0,0,0,8.1,4.9,5.31,5.31,0,0,0,12,6.5,5.46,5.46,0,0,0,6.5,12Z"/>
  </svg>
    </button>
    <script>
      (() => {
      const buttonEl =
        document.querySelector('#id_40871a65-9022-4a99-b5a2-44a0c2dd075c button.colab-df-generate');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      buttonEl.onclick = () => {
        google.colab.notebook.generateWithVariable('gdppercapdf');
      }
      })();
    </script>
  </div>

    </div>
  </div>





```python
# prompt: assign gdppercap values to the corresponding country code for the column for year 2010

#get df
dataf = pd.read_csv("https://query.data.world/s/atsel7i6wsljadsc5nbul2skjl6f2d?dws=00000")

#grab every country by the same year
df2010 = dataf[dataf["year"] == 2010]

#get new df with columns name and religious generalizations for the year 2000
religiongenpct_columns = [col for col in df2010.columns if col == ("chrstgenpct") or col == ("islmgenpct") or col == ("budgenpct") or col==("hindgenpct") or col==("sikhgenpct") or col==("judgenpct") or col==("confgenpct") or col==("othrgenpct") or col==("nonreligpct") or col==("sumreligpct")]
new_dfgenpct = df2010[["name"] + religiongenpct_columns]
new_dfgenpct.reset_index(drop=True, inplace=True)
new_dfgenpct
gdppercapdf = pd.read_csv("https://pastebin.com/raw/2GAsbJTS")
gdppercapdf.rename(columns={'Country Code': 'name'}, inplace=True)

# Merge the DataFrames based on the 'name' column
merged_df = pd.merge(new_dfgenpct, gdppercapdf[['name', '2010']], on='name', how='left')

# Now, the '2010' column in merged_df contains the GDP per capita for the year 2010
# for each country that exists in both DataFrames.

merged_df
```





  <div id="df-77321271-cbf2-4b37-9ae3-ca03275788f5" class="colab-df-container">
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
      <th>name</th>
      <th>chrstgenpct</th>
      <th>judgenpct</th>
      <th>islmgenpct</th>
      <th>budgenpct</th>
      <th>hindgenpct</th>
      <th>sikhgenpct</th>
      <th>confgenpct</th>
      <th>nonreligpct</th>
      <th>othrgenpct</th>
      <th>sumreligpct</th>
      <th>2010</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USA</td>
      <td>0.7454</td>
      <td>0.0190</td>
      <td>0.0090</td>
      <td>0.0109</td>
      <td>0.0057</td>
      <td>0.0013</td>
      <td>0.0003</td>
      <td>0.1900</td>
      <td>0.0025</td>
      <td>0.9975</td>
      <td>48650.664323</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CAN</td>
      <td>0.7661</td>
      <td>0.0099</td>
      <td>0.0194</td>
      <td>0.0194</td>
      <td>0.0080</td>
      <td>0.0080</td>
      <td>0.0001</td>
      <td>0.1643</td>
      <td>0.0010</td>
      <td>0.9990</td>
      <td>47560.666601</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BHM</td>
      <td>0.9660</td>
      <td>0.0010</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0290</td>
      <td>0.0005</td>
      <td>0.9995</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CUB</td>
      <td>0.6589</td>
      <td>0.0001</td>
      <td>0.0007</td>
      <td>0.0000</td>
      <td>0.0022</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1315</td>
      <td>0.0000</td>
      <td>1.2935</td>
      <td>5275.532601</td>
    </tr>
    <tr>
      <th>4</th>
      <td>HAI</td>
      <td>0.8200</td>
      <td>0.0000</td>
      <td>0.0002</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1000</td>
      <td>0.0000</td>
      <td>1.3711</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>189</th>
      <td>NAU</td>
      <td>0.9699</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0301</td>
      <td>0.9699</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>190</th>
      <td>MSI</td>
      <td>0.9341</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0220</td>
      <td>0.0017</td>
      <td>0.9983</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>191</th>
      <td>PAL</td>
      <td>0.8606</td>
      <td>0.0000</td>
      <td>0.0220</td>
      <td>0.0085</td>
      <td>0.0013</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0153</td>
      <td>0.0010</td>
      <td>0.9990</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>192</th>
      <td>FSM</td>
      <td>0.8651</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0059</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0315</td>
      <td>0.0197</td>
      <td>0.9803</td>
      <td>2760.011340</td>
    </tr>
    <tr>
      <th>193</th>
      <td>WSM</td>
      <td>0.9538</td>
      <td>0.0000</td>
      <td>0.0003</td>
      <td>0.0001</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0146</td>
      <td>0.0258</td>
      <td>0.9742</td>
      <td>3494.395225</td>
    </tr>
  </tbody>
</table>
<p>194 rows × 12 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-77321271-cbf2-4b37-9ae3-ca03275788f5')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-77321271-cbf2-4b37-9ae3-ca03275788f5 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-77321271-cbf2-4b37-9ae3-ca03275788f5');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-13b39ecc-f0dc-4901-98b7-f6ab85797329">
  <button class="colab-df-quickchart" onclick="quickchart('df-13b39ecc-f0dc-4901-98b7-f6ab85797329')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-13b39ecc-f0dc-4901-98b7-f6ab85797329 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

  <div id="id_e4f0e156-03fa-41df-881f-1a24780a615c">
    <style>
      .colab-df-generate {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
      }

      .colab-df-generate:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
      }

      [theme=dark] .colab-df-generate {
        background-color: #3B4455;
        fill: #D2E3FC;
      }

      [theme=dark] .colab-df-generate:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
      }
    </style>
    <button class="colab-df-generate" onclick="generateWithVariable('merged_df')"
            title="Generate code using this dataframe."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M7,19H8.4L18.45,9,17,7.55,7,17.6ZM5,21V16.75L18.45,3.32a2,2,0,0,1,2.83,0l1.4,1.43a1.91,1.91,0,0,1,.58,1.4,1.91,1.91,0,0,1-.58,1.4L9.25,21ZM18.45,9,17,7.55Zm-12,3A5.31,5.31,0,0,0,4.9,8.1,5.31,5.31,0,0,0,1,6.5,5.31,5.31,0,0,0,4.9,4.9,5.31,5.31,0,0,0,6.5,1,5.31,5.31,0,0,0,8.1,4.9,5.31,5.31,0,0,0,12,6.5,5.46,5.46,0,0,0,6.5,12Z"/>
  </svg>
    </button>
    <script>
      (() => {
      const buttonEl =
        document.querySelector('#id_e4f0e156-03fa-41df-881f-1a24780a615c button.colab-df-generate');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      buttonEl.onclick = () => {
        google.colab.notebook.generateWithVariable('merged_df');
      }
      })();
    </script>
  </div>

    </div>
  </div>





```python
# prompt: turn the NaN in the 2010 column into nulls


# ... (Your existing code) ...

# Merge the DataFrames based on the 'name' column
merged_df = pd.merge(new_dfgenpct, gdppercapdf[['name', '2010']], on='name', how='left')

merged_df.rename(columns={'2010': 'GDP/Cap for 2010'}, inplace=True)
# Replace NaN values in the '2010' column with None
merged_df['GDP/Cap for 2010'] = merged_df['GDP/Cap for 2010'].fillna(0)

merged_df
```





  <div id="df-69cc19a9-0a5d-4a70-9748-86fcbe94c020" class="colab-df-container">
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
      <th>name</th>
      <th>chrstgenpct</th>
      <th>judgenpct</th>
      <th>islmgenpct</th>
      <th>budgenpct</th>
      <th>hindgenpct</th>
      <th>sikhgenpct</th>
      <th>confgenpct</th>
      <th>nonreligpct</th>
      <th>othrgenpct</th>
      <th>sumreligpct</th>
      <th>GDP/Cap for 2010</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USA</td>
      <td>0.7454</td>
      <td>0.0190</td>
      <td>0.0090</td>
      <td>0.0109</td>
      <td>0.0057</td>
      <td>0.0013</td>
      <td>0.0003</td>
      <td>0.1900</td>
      <td>0.0025</td>
      <td>0.9975</td>
      <td>48650.664323</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CAN</td>
      <td>0.7661</td>
      <td>0.0099</td>
      <td>0.0194</td>
      <td>0.0194</td>
      <td>0.0080</td>
      <td>0.0080</td>
      <td>0.0001</td>
      <td>0.1643</td>
      <td>0.0010</td>
      <td>0.9990</td>
      <td>47560.666601</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BHM</td>
      <td>0.9660</td>
      <td>0.0010</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0290</td>
      <td>0.0005</td>
      <td>0.9995</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CUB</td>
      <td>0.6589</td>
      <td>0.0001</td>
      <td>0.0007</td>
      <td>0.0000</td>
      <td>0.0022</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1315</td>
      <td>0.0000</td>
      <td>1.2935</td>
      <td>5275.532601</td>
    </tr>
    <tr>
      <th>4</th>
      <td>HAI</td>
      <td>0.8200</td>
      <td>0.0000</td>
      <td>0.0002</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1000</td>
      <td>0.0000</td>
      <td>1.3711</td>
      <td>0.000000</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>189</th>
      <td>NAU</td>
      <td>0.9699</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0301</td>
      <td>0.9699</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>190</th>
      <td>MSI</td>
      <td>0.9341</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0220</td>
      <td>0.0017</td>
      <td>0.9983</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>191</th>
      <td>PAL</td>
      <td>0.8606</td>
      <td>0.0000</td>
      <td>0.0220</td>
      <td>0.0085</td>
      <td>0.0013</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0153</td>
      <td>0.0010</td>
      <td>0.9990</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>192</th>
      <td>FSM</td>
      <td>0.8651</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0059</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0315</td>
      <td>0.0197</td>
      <td>0.9803</td>
      <td>2760.011340</td>
    </tr>
    <tr>
      <th>193</th>
      <td>WSM</td>
      <td>0.9538</td>
      <td>0.0000</td>
      <td>0.0003</td>
      <td>0.0001</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0146</td>
      <td>0.0258</td>
      <td>0.9742</td>
      <td>3494.395225</td>
    </tr>
  </tbody>
</table>
<p>194 rows × 12 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-69cc19a9-0a5d-4a70-9748-86fcbe94c020')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-69cc19a9-0a5d-4a70-9748-86fcbe94c020 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-69cc19a9-0a5d-4a70-9748-86fcbe94c020');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-6d6457c9-1009-4d23-a77b-f7725c622657">
  <button class="colab-df-quickchart" onclick="quickchart('df-6d6457c9-1009-4d23-a77b-f7725c622657')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-6d6457c9-1009-4d23-a77b-f7725c622657 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

  <div id="id_389d6015-270d-4455-ba5f-fa333170ac2a">
    <style>
      .colab-df-generate {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
      }

      .colab-df-generate:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
      }

      [theme=dark] .colab-df-generate {
        background-color: #3B4455;
        fill: #D2E3FC;
      }

      [theme=dark] .colab-df-generate:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
      }
    </style>
    <button class="colab-df-generate" onclick="generateWithVariable('merged_df')"
            title="Generate code using this dataframe."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M7,19H8.4L18.45,9,17,7.55,7,17.6ZM5,21V16.75L18.45,3.32a2,2,0,0,1,2.83,0l1.4,1.43a1.91,1.91,0,0,1,.58,1.4,1.91,1.91,0,0,1-.58,1.4L9.25,21ZM18.45,9,17,7.55Zm-12,3A5.31,5.31,0,0,0,4.9,8.1,5.31,5.31,0,0,0,1,6.5,5.31,5.31,0,0,0,4.9,4.9,5.31,5.31,0,0,0,6.5,1,5.31,5.31,0,0,0,8.1,4.9,5.31,5.31,0,0,0,12,6.5,5.46,5.46,0,0,0,6.5,12Z"/>
  </svg>
    </button>
    <script>
      (() => {
      const buttonEl =
        document.querySelector('#id_389d6015-270d-4455-ba5f-fa333170ac2a button.colab-df-generate');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      buttonEl.onclick = () => {
        google.colab.notebook.generateWithVariable('merged_df');
      }
      })();
    </script>
  </div>

    </div>
  </div>





```python
# prompt: write a piece of code to fix the countries in merged_df with sum of the religious percentages column, denoted by "sumreligct", greater than 1 and make them equal to the sum of each of the religious affiliation percentages

# ... (Your existing code) ...

# Iterate through the rows of the DataFrame
for index, row in merged_df.iterrows():
  if row['sumreligpct'] > 1:
    # Calculate the sum of religious affiliation percentages
    religious_percentages = [
        row['chrstgenpct'], row['islmgenpct'], row['budgenpct'],
        row['hindgenpct'], row['sikhgenpct'], row['judgenpct'],
        row['confgenpct'], row['othrgenpct']
    ]

    # Replace NaN values with 0 if present in the religious_percentages
    religious_percentages = [0 if pd.isnull(x) else x for x in religious_percentages]

    # Recalculate sumreligpct with the existing percentages
    sum_religious_percentages = sum(religious_percentages)

    # Update the sumreligpct value if it is greater than 1
    if sum_religious_percentages < 1:
      merged_df.at[index, 'sumreligpct'] = sum_religious_percentages

# ... (Rest of your code) ...
```


```python
merged_df = merged_df.dropna(subset=['GDP/Cap for 2010'])
```


```python
# Assuming you have your merged_df DataFrame as shown in your previous code

# Create the dot plot
plt.figure(figsize=(10, 6))  # Adjust figure size as needed
plt.scatter(merged_df['GDP/Cap for 2010'], merged_df['chrstgenpct'], s=10)  # s controls the size of the dots

# Customize the plot
plt.xlabel('GDP per Capita for 2010')
plt.ylabel('Christian Population Percentage')
plt.title('GDP per Capita vs. Christian Population Percentage (2010)')

# You might want to rotate x-axis labels for better readability if they are long
# plt.xticks(rotation=45, ha='right')

plt.show()
```


    
![png](Work_for_HTML_part_files/Work_for_HTML_part_7_0.png)
    



```python
# prompt: make a dot plot (using plotly) of merged_df with "GDP/Cap for 2010" on the x axis and "percent religious" on the y with different colors of dots representing the different general percentages for the different religions

# Assuming 'merged_df' is your DataFrame with the necessary columns

fig = px.scatter(merged_df, x="GDP/Cap for 2010", y="sumreligpct",
                 color="chrstgenpct",  # Replace with the column representing different religion percentages
                 hover_data=['name'])
fig.update_layout(
    title="GDP per Capita vs. Percentage of Population Religious",
    xaxis_title="GDP/Cap for 2010",
    yaxis_title="Percent Religious"
)
fig.show()
```


<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax && window.MathJax.Hub && window.MathJax.Hub.Config) {window.MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="c8399333-c3d0-4da2-a8b3-d9070b316520" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("c8399333-c3d0-4da2-a8b3-d9070b316520")) {                    Plotly.newPlot(                        "c8399333-c3d0-4da2-a8b3-d9070b316520",                        [{"customdata":[["USA"],["CAN"],["BHM"],["CUB"],["HAI"],["DOM"],["JAM"],["TRI"],["BAR"],["DMA"],["GRN"],["SLU"],["SVG"],["AAB"],["SKN"],["MEX"],["BLZ"],["GUA"],["HON"],["SAL"],["NIC"],["COS"],["PAN"],["COL"],["VEN"],["GUY"],["SUR"],["ECU"],["PER"],["BRA"],["BOL"],["PAR"],["CHL"],["ARG"],["URU"],["UKG"],["IRE"],["NTH"],["BEL"],["LUX"],["FRN"],["MNC"],["LIE"],["SWZ"],["SPN"],["AND"],["POR"],["GMY"],["POL"],["AUS"],["HUN"],["CZR"],["SLO"],["ITA"],["SNM"],["MLT"],["ALB"],["MNG"],["MAC"],["CRO"],["YUG"],["BOS"],["KOS"],["SLV"],["GRC"],["CYP"],["BUL"],["MLD"],["ROM"],["RUS"],["EST"],["LAT"],["LIT"],["UKR"],["BLR"],["ARM"],["GRG"],["AZE"],["FIN"],["SWD"],["NOR"],["DEN"],["ICE"],["CAP"],["STP"],["GNB"],["EQG"],["GAM"],["MLI"],["SEN"],["BEN"],["MAA"],["NIR"],["CDI"],["GUI"],["BFO"],["LBR"],["SIE"],["GHA"],["TOG"],["CAO"],["NIG"],["GAB"],["CEN"],["CHA"],["CON"],["DRC"],["UGA"],["KEN"],["TAZ"],["BUI"],["RWA"],["SOM"],["DJI"],["ETH"],["ERI"],["ANG"],["MZM"],["ZAM"],["ZIM"],["MAW"],["SAF"],["NAM"],["LES"],["BOT"],["SWA"],["MAG"],["COM"],["MAS"],["SEY"],["MOR"],["ALG"],["TUN"],["LIB"],["SUD"],["IRN"],["TUR"],["IRQ"],["EGY"],["SYR"],["LEB"],["JOR"],["ISR"],["SAU"],["YEM"],["KUW"],["BAH"],["QAT"],["UAE"],["OMA"],["AFG"],["TKM"],["TAJ"],["KYR"],["UZB"],["KZK"],["CHN"],["MON"],["TAW"],["PRK"],["ROK"],["JPN"],["IND"],["BHU"],["PAK"],["BNG"],["MYA"],["SRI"],["MAD"],["NEP"],["THI"],["CAM"],["LAO"],["DRV"],["MAL"],["SIN"],["BRU"],["PHI"],["INS"],["ETM"],["AUL"],["PNG"],["NEW"],["VAN"],["SOL"],["KIR"],["TUV"],["FIJ"],["TON"],["NAU"],["MSI"],["PAL"],["FSM"],["WSM"]],"hovertemplate":"GDP\u002fCap for 2010=%{x}\u003cbr\u003esumreligpct=%{y}\u003cbr\u003ename=%{customdata[0]}\u003cbr\u003echrstgenpct=%{marker.color}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":[0.7454,0.7661,0.966,0.6589,0.82,0.87,0.6881,0.5588,0.6434,0.92,0.87,0.9218,0.899,0.914,0.8979,0.9686,0.7365,0.95,0.89,0.861,0.9005,0.8822,0.9793,0.9701,0.95,0.5575,0.48,0.903,0.938,0.8823,0.9426,0.951,0.9128,0.8515,0.8183,0.6263,0.9299,0.5794,0.692,0.9106,0.7019,0.802,0.8678,0.8056,0.8056,0.907,0.8573,0.7078,0.9046,0.73,0.6736,0.2138,0.7548,0.7939,0.8631,0.9727,0.2144,0.7593,0.6374,0.9137,0.9122,0.52,0.0369,0.67,0.9438,0.7453,0.8227,0.8213,0.9751,0.7423,0.2837,0.7902,0.8296,0.852,0.5684,0.951,0.798,0.0241,0.794,0.7606,0.8401,0.8172,0.9155,0.9478,0.9441,0.1088,0.892,0.0435,0.03,0.0349,0.4,0.0026,0.039,0.375,0.08,0.2935,0.85,0.1905,0.7034,0.48,0.4952,0.42,0.7472,0.492,0.34,0.8063,0.9302,0.833,0.8063,0.4777,0.889,0.8945,0.0005,0.0139,0.6156,0.575,0.8912,0.4734,0.87,0.8188,0.7228,0.8094,0.87,0.9418,0.692,0.7843,0.5858,0.0013,0.3252,0.9365,0.01,0.008,0.0035,0.03,0.0715,0.0016,0.0042,0.0189,0.1212,0.0752,0.407,0.03,0.02,0.03,0.0,0.0,0.098,0.1445,0.0714,0.0334,0.0003,0.09,0.0202,0.1007,0.05,0.29,0.058,0.0194,0.0541,0.0166,0.2859,0.0196,0.0234,0.0122,0.017,0.002,0.0776,0.0726,0.0045,0.0142,0.006,0.0037,0.015,0.091,0.0826,0.1821,0.03,0.9174,0.106,0.98,0.6145,0.96,0.5407,0.85,0.9,0.96,0.9699,0.64,0.9421,0.9699,0.9341,0.8606,0.8651,0.9538],"coloraxis":"coloraxis","symbol":"circle"},"mode":"markers","name":"","orientation":"v","showlegend":false,"x":[48650.6643227232,47560.6666009406,0.0,5275.53260105122,0.0,5509.56803417837,4835.79108651148,0.0,0.0,7182.40020254419,0.0,0.0,0.0,0.0,0.0,9823.16407459477,5399.06209583265,0.0,0.0,0.0,1495.72918990272,0.0,8124.55830734871,6392.75802564031,13692.9149666211,4589.87249766592,7999.50739437676,4546.57877452911,5047.2046433225,11249.2918904352,1922.05857050664,0.0,12764.5931178671,10385.9644319555,0.0,0.0,0.0,0.0,44184.946353964,110885.991378721,0.0,0.0,141466.827324144,4035.53448063299,0.0,48237.8911738235,0.0,0.0,12504.2501856093,52147.0241942843,13217.5045951108,0.0,0.0,36035.6449950691,0.0,21798.9142935915,4094.34968570481,2660.28817507398,50676.3870819204,0.0,0.0,0.0,0.0,3017.3073947577,26716.6488260274,31105.02734375,0.0,0.0,0.0,10674.990234375,14663.0446126465,0.0,0.0,3078.41479492188,6034.67885177216,3143.0294799683,0.0,5843.5337683582,46505.3031791811,0.0,88163.2085931423,0.0,0.0,0.0,1043.28142666295,599.859967945903,0.0,0.0,688.327865858558,1286.60496647046,1009.48949478478,0.0,0.0,0.0,0.0,0.0,497.020365397034,0.0,1258.96419689048,0.0,0.0,0.0,8399.59734808121,0.0,0.0,0.0,0.0,824.73767112214,1093.63962367926,0.0,0.0,594.115673355408,223.487606875311,1227.82085311429,335.438495270931,504.972460176652,0.0,0.0,0.0,0.0,0.0,0.0,5445.42006302741,0.0,0.0,0.0,0.0,1384.06328257479,0.0,0.0,0.0,0.0,4241.01190951928,0.0,0.0,6458.57395613765,10622.7020439723,4430.42624189518,2509.77203417522,2748.32269383475,0.0,3914.70123105389,31266.6053174383,17958.9444813361,1249.06308529856,0.0,0.0,73021.3097525035,0.0,0.0,562.499221552971,4286.88050515414,0.0,0.0,1742.34925645077,0.0,4550.47394356715,0.0,0.0,0.0,0.0,44968.1562349739,1350.63447029137,0.0,1011.59718017727,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1127.83482203842,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1879.24055902232,0.0,0.0,0.0,1528.89975749675,3043.16668029498,0.0,3416.11069898939,0.0,0.0,0.0,2760.0113395546,3494.39522455198],"xaxis":"x","y":[0.9975,0.999,0.9995,0.6619,0.8201999999999999,0.99,0.894,0.9277,0.8611,0.98,0.9268,0.9848,0.9237,0.973,0.999,0.997,0.8998,0.9964,0.9901,0.9762,0.9908,0.9916,0.9945,0.9959,0.9984,0.9963,1.0,0.9912,0.9807,0.9937,0.9989,0.9898,0.9833,0.9945,0.9948,0.9649,0.9971,0.9992,0.9407,0.9846,0.9965,0.9541,0.9827,0.9901,0.9965,0.9991,0.9417,0.9929,0.9848,0.9327,0.9468,0.9721,0.89,0.9945,0.9784,0.9984,0.9973,0.9957,0.9984,0.985,0.9961,0.9996,0.9989,0.9401,0.9944,0.9802,0.9991,0.9997,0.9958,0.9998,0.982,0.9939,0.9843,0.9991,0.9827,0.9991,0.9923,0.9943,0.9668,0.9827,0.9754,0.9598,0.9622,0.999,0.9977,0.9994,0.9886,0.9978,0.9999,0.9975,0.9823,0.979,0.9959,0.9979,0.9987,0.9997,0.9999,0.9946,0.9924,0.9968,0.9983,0.9982,0.9975,0.9967,0.997,0.9583,0.9998,0.9989,0.9989,0.9952,0.9991,0.9867,0.9975,0.9998,0.9993,0.997,0.9956,0.9956,0.9987,0.9951,0.9996,0.9914,0.9983,0.9966,0.9834,0.9968,0.9998,0.9998,0.9996,0.9989,0.9993,0.998,0.9937,0.9995,0.9915,0.9993,0.9952,0.9799,0.9955,0.9918,0.9954,1.0,0.9958,0.9982,0.99,0.9595,0.994,0.9185,0.9959,0.9677,0.9986,0.9904,0.9468,0.921,0.998,0.9987,0.9973,0.9963,0.9916,0.9962,0.9865,0.7129,0.9996,0.9989,0.9993,0.9996,0.9986,0.9963,0.9887,0.9996,0.9963,0.9964,0.9993,0.9997,0.9989,0.9986,0.9976,0.9976,0.9985,0.9985,0.9954,0.9965,0.9996,0.9802,0.9656,0.9901,0.9929,0.9996,0.9841,0.9699,0.9983,0.999,0.9803,0.9742],"yaxis":"y","type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"GDP\u002fCap for 2010"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Percent Religious"}},"coloraxis":{"colorbar":{"title":{"text":"chrstgenpct"}},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"legend":{"tracegroupgap":0},"margin":{"t":60},"title":{"text":"GDP per Capita vs. Percentage of Population Religious"}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('c8399333-c3d0-4da2-a8b3-d9070b316520');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>



```python
# prompt: take the previous visualization but make the gdp per capita data into the log of that

# Take the log of GDP per capita data
merged_df['Log GDP/Cap for 2010'] = np.log(merged_df['GDP/Cap for 2010'] + 1)  # Add 1 to avoid log(0)


# Assuming you have your merged_df DataFrame as shown in your previous code

# Create the dot plot
plt.figure(figsize=(10, 6))  # Adjust figure size as needed
plt.scatter(merged_df['Log GDP/Cap for 2010'], merged_df['chrstgenpct'], s=10)  # s controls the size of the dots

# Customize the plot
plt.xlabel('Log GDP per Capita for 2010')
plt.ylabel('Christian Population Percentage')
plt.title('Log GDP per Capita vs. Christian Population Percentage (2010)')

# You might want to rotate x-axis labels for better readability if they are long
# plt.xticks(rotation=45, ha='right')

plt.show()


# Assuming 'merged_df' is your DataFrame with the necessary columns

fig = px.scatter(merged_df, x="Log GDP/Cap for 2010", y="sumreligpct",
                 color="chrstgenpct",  # Replace with the column representing different religion percentages
                 hover_data=['name'])
fig.update_layout(
    title="Log GDP per Capita vs. Percentage of Population Religious",
    xaxis_title="Log GDP/Cap for 2010",
    yaxis_title="Percent Religious"
)
fig.show()
```


    
![png](Work_for_HTML_part_files/Work_for_HTML_part_9_0.png)
    



<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax && window.MathJax.Hub && window.MathJax.Hub.Config) {window.MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="81208101-890d-4d02-9906-1ccc03c12811" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("81208101-890d-4d02-9906-1ccc03c12811")) {                    Plotly.newPlot(                        "81208101-890d-4d02-9906-1ccc03c12811",                        [{"customdata":[["USA"],["CAN"],["BHM"],["CUB"],["HAI"],["DOM"],["JAM"],["TRI"],["BAR"],["DMA"],["GRN"],["SLU"],["SVG"],["AAB"],["SKN"],["MEX"],["BLZ"],["GUA"],["HON"],["SAL"],["NIC"],["COS"],["PAN"],["COL"],["VEN"],["GUY"],["SUR"],["ECU"],["PER"],["BRA"],["BOL"],["PAR"],["CHL"],["ARG"],["URU"],["UKG"],["IRE"],["NTH"],["BEL"],["LUX"],["FRN"],["MNC"],["LIE"],["SWZ"],["SPN"],["AND"],["POR"],["GMY"],["POL"],["AUS"],["HUN"],["CZR"],["SLO"],["ITA"],["SNM"],["MLT"],["ALB"],["MNG"],["MAC"],["CRO"],["YUG"],["BOS"],["KOS"],["SLV"],["GRC"],["CYP"],["BUL"],["MLD"],["ROM"],["RUS"],["EST"],["LAT"],["LIT"],["UKR"],["BLR"],["ARM"],["GRG"],["AZE"],["FIN"],["SWD"],["NOR"],["DEN"],["ICE"],["CAP"],["STP"],["GNB"],["EQG"],["GAM"],["MLI"],["SEN"],["BEN"],["MAA"],["NIR"],["CDI"],["GUI"],["BFO"],["LBR"],["SIE"],["GHA"],["TOG"],["CAO"],["NIG"],["GAB"],["CEN"],["CHA"],["CON"],["DRC"],["UGA"],["KEN"],["TAZ"],["BUI"],["RWA"],["SOM"],["DJI"],["ETH"],["ERI"],["ANG"],["MZM"],["ZAM"],["ZIM"],["MAW"],["SAF"],["NAM"],["LES"],["BOT"],["SWA"],["MAG"],["COM"],["MAS"],["SEY"],["MOR"],["ALG"],["TUN"],["LIB"],["SUD"],["IRN"],["TUR"],["IRQ"],["EGY"],["SYR"],["LEB"],["JOR"],["ISR"],["SAU"],["YEM"],["KUW"],["BAH"],["QAT"],["UAE"],["OMA"],["AFG"],["TKM"],["TAJ"],["KYR"],["UZB"],["KZK"],["CHN"],["MON"],["TAW"],["PRK"],["ROK"],["JPN"],["IND"],["BHU"],["PAK"],["BNG"],["MYA"],["SRI"],["MAD"],["NEP"],["THI"],["CAM"],["LAO"],["DRV"],["MAL"],["SIN"],["BRU"],["PHI"],["INS"],["ETM"],["AUL"],["PNG"],["NEW"],["VAN"],["SOL"],["KIR"],["TUV"],["FIJ"],["TON"],["NAU"],["MSI"],["PAL"],["FSM"],["WSM"]],"hovertemplate":"Log GDP\u002fCap for 2010=%{x}\u003cbr\u003esumreligpct=%{y}\u003cbr\u003ename=%{customdata[0]}\u003cbr\u003echrstgenpct=%{marker.color}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":[0.7454,0.7661,0.966,0.6589,0.82,0.87,0.6881,0.5588,0.6434,0.92,0.87,0.9218,0.899,0.914,0.8979,0.9686,0.7365,0.95,0.89,0.861,0.9005,0.8822,0.9793,0.9701,0.95,0.5575,0.48,0.903,0.938,0.8823,0.9426,0.951,0.9128,0.8515,0.8183,0.6263,0.9299,0.5794,0.692,0.9106,0.7019,0.802,0.8678,0.8056,0.8056,0.907,0.8573,0.7078,0.9046,0.73,0.6736,0.2138,0.7548,0.7939,0.8631,0.9727,0.2144,0.7593,0.6374,0.9137,0.9122,0.52,0.0369,0.67,0.9438,0.7453,0.8227,0.8213,0.9751,0.7423,0.2837,0.7902,0.8296,0.852,0.5684,0.951,0.798,0.0241,0.794,0.7606,0.8401,0.8172,0.9155,0.9478,0.9441,0.1088,0.892,0.0435,0.03,0.0349,0.4,0.0026,0.039,0.375,0.08,0.2935,0.85,0.1905,0.7034,0.48,0.4952,0.42,0.7472,0.492,0.34,0.8063,0.9302,0.833,0.8063,0.4777,0.889,0.8945,0.0005,0.0139,0.6156,0.575,0.8912,0.4734,0.87,0.8188,0.7228,0.8094,0.87,0.9418,0.692,0.7843,0.5858,0.0013,0.3252,0.9365,0.01,0.008,0.0035,0.03,0.0715,0.0016,0.0042,0.0189,0.1212,0.0752,0.407,0.03,0.02,0.03,0.0,0.0,0.098,0.1445,0.0714,0.0334,0.0003,0.09,0.0202,0.1007,0.05,0.29,0.058,0.0194,0.0541,0.0166,0.2859,0.0196,0.0234,0.0122,0.017,0.002,0.0776,0.0726,0.0045,0.0142,0.006,0.0037,0.015,0.091,0.0826,0.1821,0.03,0.9174,0.106,0.98,0.6145,0.96,0.5407,0.85,0.9,0.96,0.9699,0.64,0.9421,0.9699,0.9341,0.8606,0.8651,0.9538],"coloraxis":"coloraxis","symbol":"circle"},"mode":"markers","name":"","orientation":"v","showlegend":false,"x":[10.792441297156916,10.76978239226268,0.0,8.571024456629198,0.0,8.614422988335823,8.484006781175223,0.0,0.0,8.879528115759323,0.0,0.0,0.0,0.0,0.0,9.192600351651647,8.594165731714519,0.0,0.0,0.0,7.311037466186321,0.0,9.002769719587798,8.76307748493126,9.524706850126247,8.43182537162787,8.987260242947832,8.422350232843476,8.526787942884786,9.328149353112442,7.561672203006716,0.0,9.454508792980567,9.248306878937314,0.0,0.0,0.0,0.0,10.69616206171446,11.616266865995831,0.0,0.0,11.859827601479275,8.303141801009161,0.0,10.783920845519637,0.0,0.0,9.433903849957591,10.861841572736775,9.489372990147483,0.0,0.0,10.492291616242218,0.0,9.989661317282824,8.317607385975874,7.886565560895402,10.833235075922067,0.0,0.0,0.0,0.0,8.012451487937502,10.193079630741071,10.345156884654784,0.0,0.0,0.0,9.275752595797039,9.593153831839416,0.0,0.0,8.03249485626628,8.705443613000469,8.053260530085385,0.0,8.673262104832178,10.747343134629526,0.0,11.386956361372793,0.0,0.0,0.0,6.9510842978853695,6.398361908960739,0.0,0.0,6.535717015388946,7.160539156570414,6.918190140733011,0.0,0.0,0.0,0.0,0.0,6.210640970560055,0.0,7.138838584375519,0.0,0.0,0.0,9.036058095169816,0.0,0.0,0.0,0.0,6.716277133638263,6.998180477286562,0.0,0.0,6.388755795651335,5.413820502430541,7.113810332557267,5.81841535458076,6.226482241277933,0.0,0.0,0.0,0.0,0.0,0.0,8.602713802654932,0.0,0.0,0.0,0.0,7.233501108967359,0.0,0.0,0.0,0.0,8.35279294264527,0.0,0.0,8.773318643539497,9.270842825763095,8.396476761990561,7.828345568168514,7.919109867174478,0.0,8.2727497063205,10.350337866689182,9.795899250611775,7.130949297261716,0.0,0.0,11.198520286488366,0.0,0.0,6.334165952028958,8.363547835094181,0.0,0.0,7.463563402068518,0.0,8.423206403127715,0.0,0.0,0.0,0.0,10.713732116746254,7.209069857837933,0.0,6.920273774796863,0.0,0.0,0.0,0.0,0.0,0.0,0.0,7.028941248785702,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,7.539155004564972,0.0,0.0,0.0,7.332957494264105,8.02098247447819,0.0,8.136550648134108,0.0,0.0,0.0,7.923352318967936,8.159201731122018],"xaxis":"x","y":[0.9975,0.999,0.9995,0.6619,0.8201999999999999,0.99,0.894,0.9277,0.8611,0.98,0.9268,0.9848,0.9237,0.973,0.999,0.997,0.8998,0.9964,0.9901,0.9762,0.9908,0.9916,0.9945,0.9959,0.9984,0.9963,1.0,0.9912,0.9807,0.9937,0.9989,0.9898,0.9833,0.9945,0.9948,0.9649,0.9971,0.9992,0.9407,0.9846,0.9965,0.9541,0.9827,0.9901,0.9965,0.9991,0.9417,0.9929,0.9848,0.9327,0.9468,0.9721,0.89,0.9945,0.9784,0.9984,0.9973,0.9957,0.9984,0.985,0.9961,0.9996,0.9989,0.9401,0.9944,0.9802,0.9991,0.9997,0.9958,0.9998,0.982,0.9939,0.9843,0.9991,0.9827,0.9991,0.9923,0.9943,0.9668,0.9827,0.9754,0.9598,0.9622,0.999,0.9977,0.9994,0.9886,0.9978,0.9999,0.9975,0.9823,0.979,0.9959,0.9979,0.9987,0.9997,0.9999,0.9946,0.9924,0.9968,0.9983,0.9982,0.9975,0.9967,0.997,0.9583,0.9998,0.9989,0.9989,0.9952,0.9991,0.9867,0.9975,0.9998,0.9993,0.997,0.9956,0.9956,0.9987,0.9951,0.9996,0.9914,0.9983,0.9966,0.9834,0.9968,0.9998,0.9998,0.9996,0.9989,0.9993,0.998,0.9937,0.9995,0.9915,0.9993,0.9952,0.9799,0.9955,0.9918,0.9954,1.0,0.9958,0.9982,0.99,0.9595,0.994,0.9185,0.9959,0.9677,0.9986,0.9904,0.9468,0.921,0.998,0.9987,0.9973,0.9963,0.9916,0.9962,0.9865,0.7129,0.9996,0.9989,0.9993,0.9996,0.9986,0.9963,0.9887,0.9996,0.9963,0.9964,0.9993,0.9997,0.9989,0.9986,0.9976,0.9976,0.9985,0.9985,0.9954,0.9965,0.9996,0.9802,0.9656,0.9901,0.9929,0.9996,0.9841,0.9699,0.9983,0.999,0.9803,0.9742],"yaxis":"y","type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Log GDP\u002fCap for 2010"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Percent Religious"}},"coloraxis":{"colorbar":{"title":{"text":"chrstgenpct"}},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"legend":{"tracegroupgap":0},"margin":{"t":60},"title":{"text":"Log GDP per Capita vs. Percentage of Population Religious"}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('81208101-890d-4d02-9906-1ccc03c12811');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>



```python
dfedu = pd.read_csv("GDL-Custom-set-of-indicators-(2010)-data.csv")
dfedu.rename(columns={'ISO_Code': 'name'}, inplace=True)
dfedu.drop(columns=['Country', 'Continent', 'Level'], inplace=True)
dfedu
```





  <div id="df-153e5b49-938d-4b6f-83b4-f9ecf2784fd4" class="colab-df-container">
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
      <th>name</th>
      <th>GDLCODE</th>
      <th>Region</th>
      <th>Educational index</th>
      <th>Mean years schooling</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AFG</td>
      <td>AFGt</td>
      <td>Total</td>
      <td>0.318</td>
      <td>1.890</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ALB</td>
      <td>ALBt</td>
      <td>Total</td>
      <td>0.715</td>
      <td>9.627</td>
    </tr>
    <tr>
      <th>2</th>
      <td>DZA</td>
      <td>DZAt</td>
      <td>Total</td>
      <td>0.639</td>
      <td>7.320</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AND</td>
      <td>ANDt</td>
      <td>Total</td>
      <td>0.693</td>
      <td>10.530</td>
    </tr>
    <tr>
      <th>4</th>
      <td>AGO</td>
      <td>AGOt</td>
      <td>Total</td>
      <td>0.380</td>
      <td>3.829</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>182</th>
      <td>VNM</td>
      <td>VNMt</td>
      <td>Total</td>
      <td>0.602</td>
      <td>7.627</td>
    </tr>
    <tr>
      <th>183</th>
      <td>PSE</td>
      <td>PSEt</td>
      <td>Total</td>
      <td>0.649</td>
      <td>8.306</td>
    </tr>
    <tr>
      <th>184</th>
      <td>YEM</td>
      <td>YEMt</td>
      <td>Total</td>
      <td>0.309</td>
      <td>2.600</td>
    </tr>
    <tr>
      <th>185</th>
      <td>ZMB</td>
      <td>ZMBt</td>
      <td>Total</td>
      <td>0.515</td>
      <td>6.301</td>
    </tr>
    <tr>
      <th>186</th>
      <td>ZWE</td>
      <td>ZWEt</td>
      <td>Total</td>
      <td>0.555</td>
      <td>7.666</td>
    </tr>
  </tbody>
</table>
<p>187 rows × 5 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-153e5b49-938d-4b6f-83b4-f9ecf2784fd4')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-153e5b49-938d-4b6f-83b4-f9ecf2784fd4 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-153e5b49-938d-4b6f-83b4-f9ecf2784fd4');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-34d6b43e-2b9f-43a4-8586-dbebd2ddfea8">
  <button class="colab-df-quickchart" onclick="quickchart('df-34d6b43e-2b9f-43a4-8586-dbebd2ddfea8')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-34d6b43e-2b9f-43a4-8586-dbebd2ddfea8 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

  <div id="id_0d5b846b-7e3b-44c5-8156-732ce33ceb0f">
    <style>
      .colab-df-generate {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
      }

      .colab-df-generate:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
      }

      [theme=dark] .colab-df-generate {
        background-color: #3B4455;
        fill: #D2E3FC;
      }

      [theme=dark] .colab-df-generate:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
      }
    </style>
    <button class="colab-df-generate" onclick="generateWithVariable('dfedu')"
            title="Generate code using this dataframe."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M7,19H8.4L18.45,9,17,7.55,7,17.6ZM5,21V16.75L18.45,3.32a2,2,0,0,1,2.83,0l1.4,1.43a1.91,1.91,0,0,1,.58,1.4,1.91,1.91,0,0,1-.58,1.4L9.25,21ZM18.45,9,17,7.55Zm-12,3A5.31,5.31,0,0,0,4.9,8.1,5.31,5.31,0,0,0,1,6.5,5.31,5.31,0,0,0,4.9,4.9,5.31,5.31,0,0,0,6.5,1,5.31,5.31,0,0,0,8.1,4.9,5.31,5.31,0,0,0,12,6.5,5.46,5.46,0,0,0,6.5,12Z"/>
  </svg>
    </button>
    <script>
      (() => {
      const buttonEl =
        document.querySelector('#id_0d5b846b-7e3b-44c5-8156-732ce33ceb0f button.colab-df-generate');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      buttonEl.onclick = () => {
        google.colab.notebook.generateWithVariable('dfedu');
      }
      })();
    </script>
  </div>

    </div>
  </div>





```python
# prompt: merge dfedu and merged_df where each country code matches

# Merge dfedu and merged_df based on the 'name' column
merged_df_edu = pd.merge(merged_df, dfedu, on='name', how='left')
merged_df_edu.drop(columns=['Region', 'GDLCODE'], inplace=True)
merged_df_edu.head()
# Now, merged_df_edu contains the data from both merged_df and dfedu,
# with matching country codes.
```





  <div id="df-322e25e1-be24-4f3f-99b7-5c282be6c1a8" class="colab-df-container">
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
      <th>name</th>
      <th>chrstgenpct</th>
      <th>judgenpct</th>
      <th>islmgenpct</th>
      <th>budgenpct</th>
      <th>hindgenpct</th>
      <th>sikhgenpct</th>
      <th>confgenpct</th>
      <th>nonreligpct</th>
      <th>othrgenpct</th>
      <th>sumreligpct</th>
      <th>GDP/Cap for 2010</th>
      <th>Log GDP/Cap for 2010</th>
      <th>Educational index</th>
      <th>Mean years schooling</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USA</td>
      <td>0.7454</td>
      <td>0.0190</td>
      <td>0.0090</td>
      <td>0.0109</td>
      <td>0.0057</td>
      <td>0.0013</td>
      <td>0.0003</td>
      <td>0.1900</td>
      <td>0.0025</td>
      <td>0.9975</td>
      <td>48650.664323</td>
      <td>10.792441</td>
      <td>0.891</td>
      <td>13.05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>CAN</td>
      <td>0.7661</td>
      <td>0.0099</td>
      <td>0.0194</td>
      <td>0.0194</td>
      <td>0.0080</td>
      <td>0.0080</td>
      <td>0.0001</td>
      <td>0.1643</td>
      <td>0.0010</td>
      <td>0.9990</td>
      <td>47560.666601</td>
      <td>10.769782</td>
      <td>0.872</td>
      <td>13.51</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BHM</td>
      <td>0.9660</td>
      <td>0.0010</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0290</td>
      <td>0.0005</td>
      <td>0.9995</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>CUB</td>
      <td>0.6589</td>
      <td>0.0001</td>
      <td>0.0007</td>
      <td>0.0000</td>
      <td>0.0022</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1315</td>
      <td>0.0000</td>
      <td>0.6619</td>
      <td>5275.532601</td>
      <td>8.571024</td>
      <td>0.826</td>
      <td>11.23</td>
    </tr>
    <tr>
      <th>4</th>
      <td>HAI</td>
      <td>0.8200</td>
      <td>0.0000</td>
      <td>0.0002</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.0000</td>
      <td>0.1000</td>
      <td>0.0000</td>
      <td>0.8202</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-322e25e1-be24-4f3f-99b7-5c282be6c1a8')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-322e25e1-be24-4f3f-99b7-5c282be6c1a8 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-322e25e1-be24-4f3f-99b7-5c282be6c1a8');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-fe4c533b-7f67-4e92-9031-800c60da4010">
  <button class="colab-df-quickchart" onclick="quickchart('df-fe4c533b-7f67-4e92-9031-800c60da4010')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-fe4c533b-7f67-4e92-9031-800c60da4010 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

    </div>
  </div>





```python
# prompt: draw a graph x axis being the gdp per capita, y axis being the educational index (disclude educational index for countries with NaN), and the color profile of each point being the sumreligpct

# Assuming 'merged_df_edu' is your DataFrame with the necessary columns
# and 'Educational Index' is the column containing the educational index values

# Remove rows with NaN values in 'Educational Index'
merged_df_edu_cleaned = merged_df_edu.dropna(subset=['GDP/Cap for 2010'])

# Create the scatter plot
fig = px.scatter(merged_df_edu_cleaned, x='GDP/Cap for 2010', y='Educational index ',
                 color='chrstgenpct',
                 hover_data=['name'])

fig.update_layout(
    title='GDP per Capita vs. Educational Index (2010)',
    xaxis_title='GDP per Capita',
    yaxis_title='Educational Index'
)

fig.show()
```


<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax && window.MathJax.Hub && window.MathJax.Hub.Config) {window.MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="90ab9b16-8aa2-4768-ae50-06d55af44da8" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("90ab9b16-8aa2-4768-ae50-06d55af44da8")) {                    Plotly.newPlot(                        "90ab9b16-8aa2-4768-ae50-06d55af44da8",                        [{"customdata":[["USA"],["CAN"],["BHM"],["CUB"],["HAI"],["DOM"],["JAM"],["TRI"],["BAR"],["DMA"],["GRN"],["SLU"],["SVG"],["AAB"],["SKN"],["MEX"],["BLZ"],["GUA"],["HON"],["SAL"],["NIC"],["COS"],["PAN"],["COL"],["VEN"],["GUY"],["SUR"],["ECU"],["PER"],["BRA"],["BOL"],["PAR"],["CHL"],["ARG"],["URU"],["UKG"],["IRE"],["NTH"],["BEL"],["LUX"],["FRN"],["MNC"],["LIE"],["SWZ"],["SPN"],["AND"],["POR"],["GMY"],["POL"],["AUS"],["HUN"],["CZR"],["SLO"],["ITA"],["SNM"],["MLT"],["ALB"],["MNG"],["MAC"],["CRO"],["YUG"],["BOS"],["KOS"],["SLV"],["GRC"],["CYP"],["BUL"],["MLD"],["ROM"],["RUS"],["EST"],["LAT"],["LIT"],["UKR"],["BLR"],["ARM"],["GRG"],["AZE"],["FIN"],["SWD"],["NOR"],["DEN"],["ICE"],["CAP"],["STP"],["GNB"],["EQG"],["GAM"],["MLI"],["SEN"],["BEN"],["MAA"],["NIR"],["CDI"],["GUI"],["BFO"],["LBR"],["SIE"],["GHA"],["TOG"],["CAO"],["NIG"],["GAB"],["CEN"],["CHA"],["CON"],["DRC"],["UGA"],["KEN"],["TAZ"],["BUI"],["RWA"],["SOM"],["DJI"],["ETH"],["ERI"],["ANG"],["MZM"],["ZAM"],["ZIM"],["MAW"],["SAF"],["NAM"],["LES"],["BOT"],["SWA"],["MAG"],["COM"],["MAS"],["SEY"],["MOR"],["ALG"],["TUN"],["LIB"],["SUD"],["IRN"],["TUR"],["IRQ"],["EGY"],["SYR"],["LEB"],["JOR"],["ISR"],["SAU"],["YEM"],["KUW"],["BAH"],["QAT"],["UAE"],["OMA"],["AFG"],["TKM"],["TAJ"],["KYR"],["UZB"],["KZK"],["CHN"],["MON"],["TAW"],["PRK"],["ROK"],["JPN"],["IND"],["BHU"],["PAK"],["BNG"],["MYA"],["SRI"],["MAD"],["NEP"],["THI"],["CAM"],["LAO"],["DRV"],["MAL"],["SIN"],["BRU"],["PHI"],["INS"],["ETM"],["AUL"],["PNG"],["NEW"],["VAN"],["SOL"],["KIR"],["TUV"],["FIJ"],["TON"],["NAU"],["MSI"],["PAL"],["FSM"],["WSM"]],"hovertemplate":"GDP\u002fCap for 2010=%{x}\u003cbr\u003eEducational index =%{y}\u003cbr\u003ename=%{customdata[0]}\u003cbr\u003echrstgenpct=%{marker.color}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":[0.7454,0.7661,0.966,0.6589,0.82,0.87,0.6881,0.5588,0.6434,0.92,0.87,0.9218,0.899,0.914,0.8979,0.9686,0.7365,0.95,0.89,0.861,0.9005,0.8822,0.9793,0.9701,0.95,0.5575,0.48,0.903,0.938,0.8823,0.9426,0.951,0.9128,0.8515,0.8183,0.6263,0.9299,0.5794,0.692,0.9106,0.7019,0.802,0.8678,0.8056,0.8056,0.907,0.8573,0.7078,0.9046,0.73,0.6736,0.2138,0.7548,0.7939,0.8631,0.9727,0.2144,0.7593,0.6374,0.9137,0.9122,0.52,0.0369,0.67,0.9438,0.7453,0.8227,0.8213,0.9751,0.7423,0.2837,0.7902,0.8296,0.852,0.5684,0.951,0.798,0.0241,0.794,0.7606,0.8401,0.8172,0.9155,0.9478,0.9441,0.1088,0.892,0.0435,0.03,0.0349,0.4,0.0026,0.039,0.375,0.08,0.2935,0.85,0.1905,0.7034,0.48,0.4952,0.42,0.7472,0.492,0.34,0.8063,0.9302,0.833,0.8063,0.4777,0.889,0.8945,0.0005,0.0139,0.6156,0.575,0.8912,0.4734,0.87,0.8188,0.7228,0.8094,0.87,0.9418,0.692,0.7843,0.5858,0.0013,0.3252,0.9365,0.01,0.008,0.0035,0.03,0.0715,0.0016,0.0042,0.0189,0.1212,0.0752,0.407,0.03,0.02,0.03,0.0,0.0,0.098,0.1445,0.0714,0.0334,0.0003,0.09,0.0202,0.1007,0.05,0.29,0.058,0.0194,0.0541,0.0166,0.2859,0.0196,0.0234,0.0122,0.017,0.002,0.0776,0.0726,0.0045,0.0142,0.006,0.0037,0.015,0.091,0.0826,0.1821,0.03,0.9174,0.106,0.98,0.6145,0.96,0.5407,0.85,0.9,0.96,0.9699,0.64,0.9421,0.9699,0.9341,0.8606,0.8651,0.9538],"coloraxis":"coloraxis","symbol":"circle"},"mode":"markers","name":"","orientation":"v","showlegend":false,"x":[48650.6643227232,47560.6666009406,0.0,5275.53260105122,0.0,5509.56803417837,4835.79108651148,0.0,0.0,7182.40020254419,0.0,0.0,0.0,0.0,0.0,9823.16407459477,5399.06209583265,0.0,0.0,0.0,1495.72918990272,0.0,8124.55830734871,6392.75802564031,13692.9149666211,4589.87249766592,7999.50739437676,4546.57877452911,5047.2046433225,11249.2918904352,1922.05857050664,0.0,12764.5931178671,10385.9644319555,0.0,0.0,0.0,0.0,44184.946353964,110885.991378721,0.0,0.0,141466.827324144,4035.53448063299,0.0,48237.8911738235,0.0,0.0,12504.2501856093,52147.0241942843,13217.5045951108,0.0,0.0,36035.6449950691,0.0,21798.9142935915,4094.34968570481,2660.28817507398,50676.3870819204,0.0,0.0,0.0,0.0,3017.3073947577,26716.6488260274,31105.02734375,0.0,0.0,0.0,10674.990234375,14663.0446126465,0.0,0.0,3078.41479492188,6034.67885177216,3143.0294799683,0.0,5843.5337683582,46505.3031791811,0.0,88163.2085931423,0.0,0.0,0.0,1043.28142666295,599.859967945903,0.0,0.0,688.327865858558,1286.60496647046,1009.48949478478,0.0,0.0,0.0,0.0,0.0,497.020365397034,0.0,1258.96419689048,0.0,0.0,0.0,8399.59734808121,0.0,0.0,0.0,0.0,824.73767112214,1093.63962367926,0.0,0.0,594.115673355408,223.487606875311,1227.82085311429,335.438495270931,504.972460176652,0.0,0.0,0.0,0.0,0.0,0.0,5445.42006302741,0.0,0.0,0.0,0.0,1384.06328257479,0.0,0.0,0.0,0.0,4241.01190951928,0.0,0.0,6458.57395613765,10622.7020439723,4430.42624189518,2509.77203417522,2748.32269383475,0.0,3914.70123105389,31266.6053174383,17958.9444813361,1249.06308529856,0.0,0.0,73021.3097525035,0.0,0.0,562.499221552971,4286.88050515414,0.0,0.0,1742.34925645077,0.0,4550.47394356715,0.0,0.0,0.0,0.0,44968.1562349739,1350.63447029137,0.0,1011.59718017727,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1127.83482203842,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1879.24055902232,0.0,0.0,0.0,1528.89975749675,3043.16668029498,0.0,3416.11069898939,0.0,0.0,0.0,2760.0113395546,3494.39522455198],"xaxis":"x","y":[0.891,0.872,null,0.826,null,0.609,0.647,null,null,0.68,null,null,null,null,null,0.64,0.694,null,null,null,0.496,null,0.669,0.647,0.681,0.559,0.574,0.669,0.674,0.614,0.653,null,0.748,0.826,null,null,null,null,0.881,0.813,null,null,0.805,0.473,null,0.693,null,null,0.848,0.901,0.826,null,null,0.778,null,null,0.715,0.736,null,null,null,null,null,0.549,0.818,0.77,null,null,null,0.81,0.903,null,null,0.802,0.808,0.716,null,0.701,0.887,null,0.905,null,null,null,0.458,0.36,null,null,0.266,0.3,0.382,null,null,null,null,null,0.415,null,0.54,null,null,null,0.585,null,null,null,null,0.497,0.49,null,null,0.432,0.235,0.241,0.294,0.355,null,null,null,null,null,null,0.533,null,null,null,null,0.442,null,null,null,null,0.612,null,null,0.698,0.624,0.516,0.557,0.544,null,0.641,0.834,0.667,0.309,null,null,0.634,null,null,0.318,0.644,null,null,0.687,null,0.587,null,null,null,null,0.843,0.461,null,0.321,null,null,null,null,null,null,null,0.445,null,null,null,null,null,null,null,null,0.36,null,null,null,0.593,0.641,null,0.772,null,null,null,0.608,0.721],"yaxis":"y","type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"GDP per Capita"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Educational Index"}},"coloraxis":{"colorbar":{"title":{"text":"chrstgenpct"}},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"legend":{"tracegroupgap":0},"margin":{"t":60},"title":{"text":"GDP per Capita vs. Educational Index (2010)"}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('90ab9b16-8aa2-4768-ae50-06d55af44da8');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>



```python

# Create the scatter plot
fig = px.scatter(merged_df_edu_cleaned, x='Log GDP/Cap for 2010', y='Educational index ',
                 color='nonreligpct',
                 hover_data=['name'])

fig.update_layout(
    title='Log of GDP per Capita vs. Educational Index (2010)',
    xaxis_title='GDP per Capita',
    yaxis_title='Educational Index'
)

fig.show()
```


<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax && window.MathJax.Hub && window.MathJax.Hub.Config) {window.MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script charset="utf-8" src="https://cdn.plot.ly/plotly-2.35.2.min.js"></script>                <div id="640e60be-369b-48dc-8396-41f5dcd32b48" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("640e60be-369b-48dc-8396-41f5dcd32b48")) {                    Plotly.newPlot(                        "640e60be-369b-48dc-8396-41f5dcd32b48",                        [{"customdata":[["USA"],["CAN"],["BHM"],["CUB"],["HAI"],["DOM"],["JAM"],["TRI"],["BAR"],["DMA"],["GRN"],["SLU"],["SVG"],["AAB"],["SKN"],["MEX"],["BLZ"],["GUA"],["HON"],["SAL"],["NIC"],["COS"],["PAN"],["COL"],["VEN"],["GUY"],["SUR"],["ECU"],["PER"],["BRA"],["BOL"],["PAR"],["CHL"],["ARG"],["URU"],["UKG"],["IRE"],["NTH"],["BEL"],["LUX"],["FRN"],["MNC"],["LIE"],["SWZ"],["SPN"],["AND"],["POR"],["GMY"],["POL"],["AUS"],["HUN"],["CZR"],["SLO"],["ITA"],["SNM"],["MLT"],["ALB"],["MNG"],["MAC"],["CRO"],["YUG"],["BOS"],["KOS"],["SLV"],["GRC"],["CYP"],["BUL"],["MLD"],["ROM"],["RUS"],["EST"],["LAT"],["LIT"],["UKR"],["BLR"],["ARM"],["GRG"],["AZE"],["FIN"],["SWD"],["NOR"],["DEN"],["ICE"],["CAP"],["STP"],["GNB"],["EQG"],["GAM"],["MLI"],["SEN"],["BEN"],["MAA"],["NIR"],["CDI"],["GUI"],["BFO"],["LBR"],["SIE"],["GHA"],["TOG"],["CAO"],["NIG"],["GAB"],["CEN"],["CHA"],["CON"],["DRC"],["UGA"],["KEN"],["TAZ"],["BUI"],["RWA"],["SOM"],["DJI"],["ETH"],["ERI"],["ANG"],["MZM"],["ZAM"],["ZIM"],["MAW"],["SAF"],["NAM"],["LES"],["BOT"],["SWA"],["MAG"],["COM"],["MAS"],["SEY"],["MOR"],["ALG"],["TUN"],["LIB"],["SUD"],["IRN"],["TUR"],["IRQ"],["EGY"],["SYR"],["LEB"],["JOR"],["ISR"],["SAU"],["YEM"],["KUW"],["BAH"],["QAT"],["UAE"],["OMA"],["AFG"],["TKM"],["TAJ"],["KYR"],["UZB"],["KZK"],["CHN"],["MON"],["TAW"],["PRK"],["ROK"],["JPN"],["IND"],["BHU"],["PAK"],["BNG"],["MYA"],["SRI"],["MAD"],["NEP"],["THI"],["CAM"],["LAO"],["DRV"],["MAL"],["SIN"],["BRU"],["PHI"],["INS"],["ETM"],["AUL"],["PNG"],["NEW"],["VAN"],["SOL"],["KIR"],["TUV"],["FIJ"],["TON"],["NAU"],["MSI"],["PAL"],["FSM"],["WSM"]],"hovertemplate":"Log GDP\u002fCap for 2010=%{x}\u003cbr\u003eEducational index =%{y}\u003cbr\u003ename=%{customdata[0]}\u003cbr\u003enonreligpct=%{marker.color}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":[0.19,0.1643,0.029,0.1315,0.1,0.12,0.1994,0.1346,0.205,0.06,0.0481,0.059,0.019,0.059,0.0888,0.0272,0.1562,0.0459,0.1,0.111,0.09,0.1,0.0,0.015,0.0439,0.05,0.0,0.085,0.04,0.085,0.04,0.03,0.06,0.12,0.172,0.2616,0.0605,0.34,0.192,0.0496,0.1915,0.129,0.0546,0.1342,0.16,0.0796,0.0691,0.23,0.08,0.1542,0.2716,0.7575,0.1344,0.1868,0.106,0.015,0.1507,0.0451,0.019,0.0565,0.0528,0.0293,0.0059,0.24,0.0261,0.032,0.0473,0.1404,0.0163,0.1404,0.6903,0.2006,0.1521,0.1348,0.411,0.0346,0.0876,0.0193,0.166,0.16,0.1105,0.1011,0.0325,0.0179,0.0124,0.0162,0.0344,0.0052,0.0019,0.0017,0.0334,0.0011,0.001,0.0058,0.0019,0.005,0.01,0.0122,0.06,0.0025,0.0073,0.0031,0.016,0.0124,0.0025,0.0737,0.0051,0.0043,0.0033,0.0089,0.0026,0.0035,0.0004,0.0096,0.0013,0.0128,0.0179,0.0088,0.0018,0.0256,0.0061,0.064,0.0193,0.0028,0.0249,0.0118,0.0061,0.0024,0.0071,0.0097,0.0,0.0,0.0,0.0,0.01,0.0036,0.005,0.011,0.01,0.0146,0.03,0.0,0.045,0.02,0.0,0.0,0.0,0.0177,0.0136,0.0,0.002,0.01,0.025,0.05,0.0179,0.1152,0.325,0.3095,0.07,0.6432,0.4542,0.095,0.0031,0.0003,0.001,0.0008,0.0049,0.0005,0.0,0.0019,0.01,0.0039,0.0111,0.364,0.0018,0.1178,0.0118,0.0093,0.0075,0.0039,0.3101,0.0052,0.3919,0.0331,0.0032,0.01,0.007,0.0105,0.0043,0.0,0.022,0.0153,0.0315,0.0146],"coloraxis":"coloraxis","symbol":"circle"},"mode":"markers","name":"","orientation":"v","showlegend":false,"x":[10.792441297156916,10.76978239226268,0.0,8.571024456629198,0.0,8.614422988335823,8.484006781175223,0.0,0.0,8.879528115759323,0.0,0.0,0.0,0.0,0.0,9.192600351651647,8.594165731714519,0.0,0.0,0.0,7.311037466186321,0.0,9.002769719587798,8.76307748493126,9.524706850126247,8.43182537162787,8.987260242947832,8.422350232843476,8.526787942884786,9.328149353112442,7.561672203006716,0.0,9.454508792980567,9.248306878937314,0.0,0.0,0.0,0.0,10.69616206171446,11.616266865995831,0.0,0.0,11.859827601479275,8.303141801009161,0.0,10.783920845519637,0.0,0.0,9.433903849957591,10.861841572736775,9.489372990147483,0.0,0.0,10.492291616242218,0.0,9.989661317282824,8.317607385975874,7.886565560895402,10.833235075922067,0.0,0.0,0.0,0.0,8.012451487937502,10.193079630741071,10.345156884654784,0.0,0.0,0.0,9.275752595797039,9.593153831839416,0.0,0.0,8.03249485626628,8.705443613000469,8.053260530085385,0.0,8.673262104832178,10.747343134629526,0.0,11.386956361372793,0.0,0.0,0.0,6.9510842978853695,6.398361908960739,0.0,0.0,6.535717015388946,7.160539156570414,6.918190140733011,0.0,0.0,0.0,0.0,0.0,6.210640970560055,0.0,7.138838584375519,0.0,0.0,0.0,9.036058095169816,0.0,0.0,0.0,0.0,6.716277133638263,6.998180477286562,0.0,0.0,6.388755795651335,5.413820502430541,7.113810332557267,5.81841535458076,6.226482241277933,0.0,0.0,0.0,0.0,0.0,0.0,8.602713802654932,0.0,0.0,0.0,0.0,7.233501108967359,0.0,0.0,0.0,0.0,8.35279294264527,0.0,0.0,8.773318643539497,9.270842825763095,8.396476761990561,7.828345568168514,7.919109867174478,0.0,8.2727497063205,10.350337866689182,9.795899250611775,7.130949297261716,0.0,0.0,11.198520286488366,0.0,0.0,6.334165952028958,8.363547835094181,0.0,0.0,7.463563402068518,0.0,8.423206403127715,0.0,0.0,0.0,0.0,10.713732116746254,7.209069857837933,0.0,6.920273774796863,0.0,0.0,0.0,0.0,0.0,0.0,0.0,7.028941248785702,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,7.539155004564972,0.0,0.0,0.0,7.332957494264105,8.02098247447819,0.0,8.136550648134108,0.0,0.0,0.0,7.923352318967936,8.159201731122018],"xaxis":"x","y":[0.891,0.872,null,0.826,null,0.609,0.647,null,null,0.68,null,null,null,null,null,0.64,0.694,null,null,null,0.496,null,0.669,0.647,0.681,0.559,0.574,0.669,0.674,0.614,0.653,null,0.748,0.826,null,null,null,null,0.881,0.813,null,null,0.805,0.473,null,0.693,null,null,0.848,0.901,0.826,null,null,0.778,null,null,0.715,0.736,null,null,null,null,null,0.549,0.818,0.77,null,null,null,0.81,0.903,null,null,0.802,0.808,0.716,null,0.701,0.887,null,0.905,null,null,null,0.458,0.36,null,null,0.266,0.3,0.382,null,null,null,null,null,0.415,null,0.54,null,null,null,0.585,null,null,null,null,0.497,0.49,null,null,0.432,0.235,0.241,0.294,0.355,null,null,null,null,null,null,0.533,null,null,null,null,0.442,null,null,null,null,0.612,null,null,0.698,0.624,0.516,0.557,0.544,null,0.641,0.834,0.667,0.309,null,null,0.634,null,null,0.318,0.644,null,null,0.687,null,0.587,null,null,null,null,0.843,0.461,null,0.321,null,null,null,null,null,null,null,0.445,null,null,null,null,null,null,null,null,0.36,null,null,null,0.593,0.641,null,0.772,null,null,null,0.608,0.721],"yaxis":"y","type":"scatter"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"GDP per Capita"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Educational Index"}},"coloraxis":{"colorbar":{"title":{"text":"nonreligpct"}},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"legend":{"tracegroupgap":0},"margin":{"t":60},"title":{"text":"Log of GDP per Capita vs. Educational Index (2010)"}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('640e60be-369b-48dc-8396-41f5dcd32b48');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>

