# Circadian period Q<sub>10</sub> calculator
This is a simple code to calculate Q<sub>10</sub> values.

Q<sub>10</sub> values will be calculated by the following equation:<br />
![q10_eq_s](https://user-images.githubusercontent.com/101025597/157246791-fafd8e4e-d997-413c-a35e-82eea43a9cbc.png) <br />

**Open in Google Colab:**<br/>
https://colab.research.google.com/github/dxda6216/q10_two_temperatures/blob/main/circadian_period_q10_2_temperatures.ipynb

If you have period data obtained at more than 2 different temperatures, please see: https://github.com/dxda6216/q10

![q102ptss](https://user-images.githubusercontent.com/101025597/157476620-ea223179-3158-42d2-93d2-3a3b9b265200.png)

## Usage

<b><ins>Sample Description</ins></b>

Eter a description of your sample to the "<i>Data_description</i>" input form. This field can be blank.

<pre><b>Data_description:</b> <ins>XYZ gene knockout cells at 32.5 and 37.2˚C    </ins></pre>

<b><ins>Temperature and Period Data</ins></b>

Enter your data into the "<i>Temperature_1</i>", "<i>Period_1</i>", "<i>Temperature_2</i>", and "<i>Period_2</i>" input forms.
For example, if you have the following dataset

<pre><ins>Temp (˚C)</ins>   <ins>Period (hr)</ins>
  33.4        27.2
  37.0        22.6</pre>
enter your data as follows:
<pre><b>Temperature_1:</b> <ins>33.4                             </ins>
<b>Period_1:</b> <ins>27.2                                  </ins>
<b>Temperature_2:</b> <ins>37.0                             </ins>
<b>Period_2:</b> <ins>22.6                                  </ins></pre>

This calculator is for calculating Q<sub>10</sub> values and plotting data only. Your data entered to this calculator will not be recorded or saved in any location (please see the code).

<b><ins>Exporting Dataset and Fitted Curve</ins></b>

To output the dataset and fitted curve in tab-delimited format, select "<b>Yes</b>" in the "<i>Display_tab_delimited_data</i>" dropdown, and 2-column datasets will be displayed. To export the data to Excel, copy the 2-column dataset and paste it onto an Excel worksheet (right click -> Paste Options: Paste Special... -> Paste as Unicode Text -> click "OK").
