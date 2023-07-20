# FELM
 FELM is a benchmark for factuality evaluation of large language models. We firstly collect prompts from various sources including standard datasets like truthfulQA, online platforms like Github repositories, ChatGPT generation or drafted by authors, then we use ChatGPT to produce the responses for the prompts. Next we annotate these reponses in segment granularity with reference links, error types and error reasons provided by annotators. This benchmark can serve as meta-metric for factuality detectors of LLM.
![](image/felm_examples.png)
## Data Description
#### Dataset Snapshot

Category | Data
--- | ---
Number of Instances | 847
Number of Fields | 5
Labeled Classes | 2
Number of Labels | 4427
Average Labeles Per Instance | 4.8

#### Descriptive Statistics


Statistic | All | world_knowledge | Reasoning | Math | Science/tech | Writting/Recommendation 
--- | --- | --- | --- | --- | --- | ---
Segments | 4427 | 532  | 1025 | 599 | 683 |  1588
Positive segments | 3642 | 385  | 877 | 477 | 582 |1321 
Negative segments |785 | 147  | 148 | 122 | 101 | 267  

#### Data Fields

| Field Name  | Field Value | Description                                 |
| ----------- | ----------- | ------------------------------------------- |
| index         | Integer     | the order number of the data point          |
| source   | string      | the prompt source   |
| prompt           | string      | the prompt for generating response                   |
| response           | string      | the response of ChatGPT for prompt                  |
| segmented_response           | list      | segments of reponse                   |
| labels          | list      | factuality labels for segmented_response                  |
| comment      | list      | error reasons for segments with factual error  |
| type | list      |  error types for segments with factual error        |
| ref | list      |  reference links       |


#### Typical Data Point


```
{"index": "0", "source": "quora", "prompt": "Which country or city has the maximum number of nuclear power plants?", "response": "The United States has the highest number of nuclear power plants in the world, with 94 operating reactors. Other countries with a significant number of nuclear power plants include France, China, Russia, and South Korea.", "segmented_response": ["The United States has the highest number of nuclear power plants in the world, with 94 operating reactors.", "Other countries with a significant number of nuclear power plants include France, China, Russia, and South Korea."], "labels": [false, true], "comment": ["As of December 2022, there were 92 operable nuclear power reactors in the United States.", ""], "type": ["knowledge_error", null], "ref": ["https://www.eia.gov/tools/faqs/faq.php?id=207&t=3"]}

```





## Download

- Method 1: Download the zip file then unzip it:
  ```
  git clone https://github.com/SJTU-LIT/felm.git
  ```
- Method 2: Directly load the dataset using [Hugging Face datasets](https://huggingface.co/datasets/sjtu-lit/felm):

  ```python
  from datasets import load_dataset
  dataset=load_dataset(r"sjtu-lit/felm",'wk')
  print(dataset['test'][0])
  
  ```


## Licenses

[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)

This work is licensed under a [MIT License](https://lbesson.mit-license.org/).

[![CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

The FELM dataset is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/).




