# LLM-201
Large Language Model Project for Harvard AM201 Course.

Please use the below notebook access the example:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/BaeHenryS/LLM-201/blob/main/examples/example_math_openai.ipynb)


## Purpose

With the growing interest in Large Laguage Models (LLM's), there are many work evaluating and fine tuning them on domain specific datasets. One interesting direction is to assess LLM's ability to perform various forms of mathmetical inferences. While previous studies have explored the ability of LLM's to solve relatively simple mathematical problems such as algebraic equations, there are limited studies on their ability to evaluate more complex and domain-specific mathematical problems. Therefore, we believe evaluating and refining LLM's on problems presented in courses such as AM201 are valuable following reasons:
- The nature of these physical mathmetics problems particularly emphasizes intuitive approximations and abstraction abilities, which is known to be a weak point of many LLMs ([Mishra, Swaroop et al.](https://arxiv.org/abs/2204.05660))
- Through conducting a questionnaire-based study across the semester for the AM201 course, we as a whole class responded with anecdotal evidence that the most capable LLM's generally lack the ability to solve these types of problems.

We have a wealth of data from student homework submissions. Students spend a long time writing their submissions (and many work very hard to achieve high quality), resulting in a wealth of data generated from classrooms every year. This can be used to build new models or fine-tune existing models to potentially help students with problems and make them be able to solve more complex problems in the future. 


The difficulty comes from organization and curation of data into a standard format for fine tuning. In the classroom, none of the data are standardized. Students hand, and their homework in variety of formats ranging from latex PDF's to image files of handwritten submissions. Even in the same format, students have different templates and organizations. This makes procurement and cleaning up data a challenge. Furthermore, it calls for a standardized data collection and formatting process that allows for easy conversion into a standard format for fine tuning. 


For the project, we present a framework to efficiently collect, clean, and process student submissions to train a language model, as well as the steps to fine-tune the model for specific classes. 




## Process Overview

Here, we outline our process to collect, clean, and process student submissions to train a language model, as well as the steps to fine-tune the model for specific classes.

### Data Collection

To standardize data formats, we have outlined the steps to collect and input the data into a spreadsheet, which can be quickly converted into a standard format for fine tuning. We have followed the formatting of the MATH dataset introduced by [Hendrycks et al.](https://arxiv.org/abs/2103.03874), which is a dataset of mathematical problems and solutions. The dataset is also available [here](https://paperswithcode.com/dataset/math). The below shows the format of the dataset we have used:

| Column          | Description           |
| ------------------ | --------------------- |
| problem            | The statement of the math problem |
| type               | The category of the problem (e.g. AM201 Integrals) |
| level              | The difficulty level of the problem in integer (optional) |
| solution           | The solution to the problem, the final solution should be withinin \$\\\boxed{}\$ |

We have also made it so that the person can input the data into a JSONL, which would not require any conversions.

One could alternatively follow the .json/.jsonl format. with the following format:

```json
{
    "problem": "The statement of the math problem",
    "type": "The category of the problem (e.g. AM201)",
    "level": "The difficulty level of the problem in integer (optional)",
    "solution": "The solution to the problem, the final solution should be withinin \$\\\boxed{}\$"
}
```

The standardized format ensures proper selection of test values (final answers for the math problems) and organization of data. 

### Fine-Tuning

We have identified two broad methods of fine-tuning language models. First, with the GPT models with OpenAI, we have used the OpenAI library in Python as well as the [OpenAI API website](https://platform.openai.com/docs/overview) to fine-tune a baseline [GPT-3.5 model](https://openai.com/blog/gpt-3-5-turbo-fine-tuning-and-api-updates). We found this to be the easiest method to fine-tune LLM's with its simple interface and easy-to-use API commands. The example Colab Notebook that we have provided at the top of the report provides the fine-tuning steps with OpenAI. 

The other option has been through the HuggingFace library. The Transformers Library provides a wide range of LLM's that can be fine-tuned. We have identified that [Llama-2 model](https://arxiv.org/abs/2307.09288) would be the best model to fine-tune for our purposes. We have the data format and the skeleton code for fine-tuning with Llama-2 in the [example_math_huggingface.ipynb](./examples/example_math_huggingface.ipynb) notebook.


Our primarly limitation from the project came from the compute power. We were limited to usage of API calls and compute resources from our personal accounts and Google Colab, which limited the fine tuning that we could do currently. Although we have requested for API access many weeks ago, we have not redeived access to it yet.





### Evaluation

To objectively and efficiently measure the impact of domain-specific datsets (specifically curated dataset on advanced mathematics problems), it is important to develop tools to quantitatively assess the performance of LLM's and the improvements resulting from additional data. For this reason, we have developed a similar methodology to the MATH Dataset, which required final answers to include a boxed answer. We created a function to extract these boxed answers from the loop, then compare them to the predicted answers from the LLM, which are also extracted from a boxed answer. Then we compare the two answers. Note that in the case of sybmolic responses which would be common in our dataset, we compare the two answers using the [SymPy](https://www.sympy.org/en/index.html) library, which is a Python library for symbolic mathematics. This is used to objectively determine the accuracy of the LLM's on the dataset.

## Future Work

We have outlined an end-to-end framework to fine-tune and evaluate different large language models. We will have to conduct additional investigations with the data given from the course team to determine its efficacy and potential for future use. 

Standardized data collection is the most important step, as (similar to many machine learning tasks), data organization and cleaning takes the bulk of the time. Therefore, it is important to have rigorous and standardized data collection procedures from the beginning. For classrooms, we propose mandating a standardized LaTeX template, requiring students to submit the answers in the same format and to clearly identify the location of their final answers. With the standard template, one can easily create a script to extract the working and final answers from the LaTeX files with minimal work required across different data points. 








