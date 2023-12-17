# Pipeline for evaluation and fine tuning of LLMs on mathematics problems

This repo provides a pipeline for evaluating and fine tuning different LLMs on various kinds of mathematics problems. The current implementation includes different versions of OpenAI GPT models and [Llama](https://huggingface.co/docs/transformers/main/model_doc/llama). On the dataset side, this repo currently provides the [MATH](https://paperswithcode.com/dataset/math) dataset as well as the AM201 physical mathematics problems dataset (to be added). 

## Working Notebook

The [example_math_openai.ipynb](./examples/example_math_openai.ipynb) notebook provides a step-by-step guideline to refine the data, fine tune LLM with OpenAI, then evaluate it on the Math Dataset, with options to easily switch to a custom-made dataset. The notebook is also available on Google Colab below:

</br>

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/BaeHenryS/LLM-201/blob/main/examples/example_math_openai.ipynb)

## Local Installation 

To run the Jupyter notebook locally, you could follow the folowing steps to clone the repo and create a environment:

### Step 1: clone the repo

```
git clone https://github.com/BaeHenryS/LLM-201.git
```
### Step 2: create a virtual environment (using Anaconda)

```
conda env create -f LLM201.yaml
```

## Dataset 

The following image provides a example of the [MATH](https://paperswithcode.com/dataset/math) dataset and our AM201 dataset side-by-side (todo: usethe format of the MATH dataset Github).