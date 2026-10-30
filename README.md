# Circadian period Q10 calculator (web app)

**Try it now: <https://dxda6216.github.io/q10_two_temperatures/index.html>**

Open the link in your browser and start using it right away — no download needed. Everything runs locally in your browser. No data is sent anywhere or saved.

This is a single-file web app that calculates the temperature coefficient (Q10) of the circadian period from measurements taken at two temperatures. It is a browser-based version of the Colab notebook in this repository ([`circadian_period_q10_2_temperatures.ipynb`](https://github.com/dxda6216/q10_two_temperatures/blob/main/circadian_period_q10_2_temperatures.ipynb)), extended to accept replicate measurements at each temperature.

## What is Q10?

Q10 is the factor by which a rate changes for a 10°C rise in temperature ([see van't Hoff's Q10 table](https://dxda6216.github.io/q10/images/vant_hoff_q10.png)). From rates R1 and R2 measured at temperatures T1 and T2:

![Q_{10} = \left(\frac{R_2}{R_1}\right)^{\frac{10}{T_2-T_1}}](https://latex.codecogs.com/svg.image?Q_%7B10%7D%20%3D%20%5Cleft%28%5Cfrac%7BR_2%7D%7BR_1%7D%5Cright%29%5E%7B%5Cfrac%7B10%7D%7BT_2-T_1%7D%7D)

In a periodic phenomenon where frequencies f1 and f2, and periods τ1 and τ2 are measured at temperatures T1 and T2:

![Q_{10} = \left (  \frac{f_{2}}{f_{1}}\right )^{\frac{10}{ T_2-T_1 }} = \left ( \frac{\tau_1}{\tau_2} \right )^{\frac{10}{ T_2-T_1 }}](https://latex.codecogs.com/svg.image?Q_%7B10%7D%3D%5Cleft%28%5Cfrac%7Bf_%7B2%7D%7D%7Bf_%7B1%7D%7D%5Cright%29%5E%7B%5Cfrac%7B10%7D%7BT_2-T_1%7D%7D%3D%5Cleft%28%5Cfrac%7B%5Ctau_1%7D%7B%5Ctau_2%7D%5Cright%29%5E%7B%5Cfrac%7B10%7D%7BT_2-T_1%7D%7D)

## Quick start

The fastest way is to open the hosted app at <https://dxda6216.github.io/q10_two_temperatures/index.html>. To use it offline instead:

1. Open [`index.html`](https://github.com/dxda6216/q10_two_temperatures/blob/main/index.html) on GitHub, then click **Download raw file**.
2. Open the downloaded file in any modern browser (Chrome, Edge, Firefox, Safari).
3. The values shown on first load are sample data. Press **Clear inputs** to erase them, then enter your own data.

No installation, server, or Python environment is required. The page loads two web fonts from Google Fonts when online; offline, it falls back to system fonts and works the same.

## Inputs

| Field              | Description                                                       |
|--------------------|-------------------------------------------------------------------|
| Sample description | Optional. Shown as the plot title.                                |
| Temp (°C)          | Temperature for each condition. The two temperatures must differ. |
| Periods (h)        | One or more period measurements for that temperature.             |

Replicate periods can be separated by line breaks, spaces, commas, semicolons, or tabs, so a column copied from Excel can be pasted directly. All periods must be greater than zero.

Results update as you type.

## Calculation

Replicates at each temperature are averaged, and Q10 is calculated from the mean periods:

```
Q10 = (τ̄1 / τ̄2) ^ (10 / (T2 − T1))
```

where τ̄1 and τ̄2 are the mean periods at temperatures T1 and T2. With a single value per temperature, this is identical to the original notebook's two-point calculation.

### Fitted curve

The plotted curve is the exponential relationship implied by Q10, passing through both mean periods:

```
τ(T) = τ̄1 · Q10 ^ (−(T − T1) / 10)
```

It is drawn from 25% of the temperature span below the lower temperature to 25% above the higher one (101 points).

### Summary statistics

For each temperature the app reports n, mean, sample standard deviation (SD, n − 1 denominator), and standard error of the mean (SEM = SD / √n).

### Uncertainty of Q10

When both temperatures have at least two replicates, an approximate standard error of Q10 is estimated by propagating each mean's SEM (delta method on ln Q10):

```
SE(ln Q10) = (10 / |T2 − T1|) · √[ (SEM1 / τ̄1)² + (SEM2 / τ̄2)² ]
SE(Q10)   ≈ Q10 · SE(ln Q10)
95% range ≈ Q10 · exp(±1.96 · SE(ln Q10))
```

This is a large-sample approximation intended as a guide. With small n, consider a t-based interval or bootstrap analysis for formal reporting.

### Interpretation

The app labels the result against the commonly cited temperature-compensation range for circadian clocks:

| Q10     | Label                                |
|---------|--------------------------------------|
| 0.9–1.1 | Within the typical compensated range |
| > 1.1   | Above the typical compensated range  |
| < 0.9   | Overcompensated                      |

## Plot

- Open circles show individual replicates (offset slightly left of the mean so they do not overlap it).
- Filled circles show the mean at each temperature, with ± SD error bars when n ≥ 2.
- The line shows the fitted curve, with the Q10 value in the corner.

Hover over a point to see its exact values.

## Exporting data

The **Tab-delimited data** panel provides three blocks, each with a **Copy** button:

| Block          | Contents                                                   |
|----------------|------------------------------------------------------------|
| All replicates | Temperature and period for every measurement               |
| Summary        | Temperature, n, mean, SD, SEM for each condition, plus Q10 |
| Fitted curve   | Temperature and fitted period for the curve                |

To paste into Excel: right-click a cell → **Paste Special…** → **Unicode Text** → **OK**.

## Layout

The page is designed to fit in a 900-pixel-tall browser window on desktop screens. Below 760 px wide (for example, on phones) the panels stack vertically. Light and dark mode follow your system setting.

## Related

- For period data at more than two temperatures: [dxda6216/q10](https://github.com/dxda6216/q10)

## License

This web app is derived from the Colab notebook version [`circadian_period_q10_2_temperatures.ipynb`](https://github.com/dxda6216/q10_two_temperatures/blob/main/circadian_period_q10_2_temperatures.ipynb), which is licensed under the GNU General Public License v3.0. This derivative work is likewise distributed under GPL-3.0.
