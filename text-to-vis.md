# Text-to-Vis

<p align="center">
    <img src="images/text-to-vis-pipeline.png" width="500">
</p>

Text-to-Vis refers to the task of taking a human language request for visualisation, data files (optional), and code context (optional), then generating code to produce the corresponding visualisation, as described in Figure above.



## Datasets
| Year | Dataset         | Input Type                        | Output Type                | # Utterances | Chart Types |
|------|-----------------|-----------------------------------|----------------------------|--------------|-------------|
| 2021 | Plot Coder      | Python code context, NL request   | Python code                | N/A          | N/A         |
| 2021 | NLV Corpus      | CSV file, NL request              | Vega-lite JSON spec        | 893          | 10          |
| 2022 | ChartDialogs    | Dialog context, NL request        | Slot values                | 15,754       | 12          |
| N/A  | nvBench         | NL request, data                  | Visualization spec         | N/A          | N/A         |
|      | (Add more here) |                                   |                            |              |             |


## Detail

#### Plot Coder [(Chen et al., 2021)](https://aclanthology.org/2021.acl-long.169/)
- How it was created: 
    1. Select notebooks from the Juice dataset on GitHub that contain visualization code (e.g., matplotlib, pandas, seaborn).
    2. Identify lines of code that invoke plotting functions (e.g., plt.plot(), sns.barplot()).
    3. Use the plotting code line as the output, and treat the preceding lines as input (including code context and any natural language requests found in the notebook).
- Input: Python Code Context, Natural Language Request
- Output: Python code
- Dataset statistics:
    - Train/Validation/Test Split: 38971/884/942
    - Total utterances: N/A
    - Plotting data: N/A
    - Visualisations created: N/A
    - #. Chart types: N/A
- How to evaluate:
    - Chart type accuracy: use the same plotting function?
    - Exact match of data fields
- Website: https://github.com/jungyhuk/plotcoder
- Advantages: Provides a large collection of real-world text-to-vis examples from public notebooks.
- Limitations: Licensing of GitHub notebooks is unclear, and the dataset may overlap with data used to train large language models.

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
    - #. Chart types: 10
- Input: Natural Language Request (NL request), CSV file
- Output: Vega-lite JSON specification
- How to evaluate:
    - Chart type accuracy: Classify NL request --> Chart type
    - Exact match of Vega-lite components
- Website: https://nlvcorpus.github.io/
- Advantages: 100% manually created
- Limitations: small, no diversity in chart types and plotting data.


#### ChartDialogs
- How it was created: 
    1. Generate random data points and charts
    2. Use slot-filling approach to manually annotate. Human interact with system (another human) to create dialogs aiming to change slots (around 53 chart attributes, such as bar_width, reverse_x_axis, log_scale_x_axis). A pre-defined Python program was used to generate the changes.
- Dataset statistics:
    - Train/Validation/Test Split: 11,903/1,562/1,481
    - Total utterances: 15,754
    - Plotting data: randomly generated
    - Visualisations created: 15,754
    - #. Chart types: 12
- Input: Contextual dialogs, a new request for changing chart attributes
- Output: Slots (e.g. bar_width=12, reverse_x_axis=True, log_scale_x_axis=False)
- How to evaluate:
    - Accuracy of slot filling
- Website: https://github.com/sythello/ChartDialog
- Advantages: 100% manually created
- Limitations: Too easy for LLMs (e.g. ChatGPT)

#### nvBench


## Evaluation