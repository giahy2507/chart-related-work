# Text-to-Vis

<p align="center">
    <img src="images/text-to-vis-pipeline.png" width="500">
</p>

Text-to-Vis refers to the task of taking a human language request for visualisation, data files (optional), and code context (optional), then generating code to produce the corresponding visualisation, as described in Figure above.

## Datasets

#### NLV Corpus [(Srinivasan et al., 2021)](https://dl.acm.org/doi/10.1145/3411764.3445400)
- How it was created: 
    1. Choose 3 CSV datasets: Cars, Movies, Superstore
    2. Manually create 10 different charts for each dataset using [Vega-lite](https://vega.github.io/vega-lite/) specifications.
    3. Conduct a survey on multiple social media platforms (e.g. LinkedIn and Reddit). Show participants data table and the chart, then ask them to provide utterances they would pose to generate the displayed charts.
    4. Collect, analyze, and organize the responses
- Dataset statistics:
    - Train/Validation/Test Split: No
    - Total utterances: 893
    - Plotting data: 3 CSV files (Cars, Movies, Superstore)
    - Visualisations created: 30
- Input: Natural Language Request (NL request), CSV file
- Output: Vega-lite JSON specification
- How to evaluate:
    - Chart type accuracy: Classify NL request --> Chart type
    - Exact match of Vega-lite components
- Website: https://nlvcorpus.github.io/
- Advantages: 100% manually created
- Limitations: small, no diversity in chart types and plotting data.

#### Plot Coder
#### ChartDialogs
#### nvBench


## Evaluation