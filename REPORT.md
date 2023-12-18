# LLM-201
Large Language Model Project for Harvard AM201 Course.

Please use the below notebook access the example:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/BaeHenryS/LLM-201/blob/main/examples/example_math_openai.ipynb)


## Purpose

With the growing interest in Large Laguage Models (LLM's), there are many work evaluating and fine tuning them on domain specific datasets. One interesting direction is to assess LLM's ability to perform various forms of mathmetical inferences. While previous studies have explored the ability of LLM's to solve relatively simple mathematical problems such as algebraic equations, there are limited studies on their ability to evaluate more complex and domain-specific mathematical problems. Therefore, we believe evaluating and refining LLM's on problems presented in courses such as AM201 are valuable following reasons:
- The nature of these physical mathmetics problems particularly emphasizes intuitive approximations and abstraction abilities, which is known to be a weak point of many LLMs ([Mishra, Swaroop et al.](https://arxiv.org/abs/2204.05660))
- Through conducting a questionnaire-based study across the semester for the AM201 course, we as a whole class responded with anecdotal evidence that the most capable LLM's generally lack the ability to solve these types of problems.

We have a wealth of data from student homework submissions. Students spend a long time writing their submissions (and many work very hard to achieve high quality), resulting in a wealth of data generated from classrooms every year. This can be used to build new models or fine-tune existing models to potentially help students with problems and make them be able to solve more complex problems in the future. For the project, we present a framework to efficiently collect, clean, and process student submissions to train a language model, as well as the steps to fine-tune the model for specific classes. 

## Challenges

The difficulty comes from organization and curation of data into a standard format for fine tuning. In the classroom, none of the data are standardized. Students hand, and their homework in variety of formats ranging from latex PDF's to image files of handwritten submissions. Even in the same format, students have different templates and organizations. This makes procurement and cleaning up data a challenge. 

For this reason, the bulk of the time spent on this project 


## Process Overview

Here, we outline our process to collect, clean, and process student submissions to train a language model, as well as the steps to fine-tune the model for specific classes.

### Data Collection

To standardize data formats, we have outlined the steps to collect and input the data into a spreadsheet, which can be quickly converted into a standard format for fine tuning. We have followed the formatting of the MATH dataset, which is a dataset of mathematical problems and solutions. The dataset is also available [here](https://paperswithcode.com/dataset/math). The below shows the format of the dataset we have used:

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

We have identified two broad methods of fine-tuning language models. First, with the GPT models with OpenAI, we have used the OpenAI library in Python as well as the OpenAI API website to fine-tune a baseline GPT-3.5 model. We found this to be the easiest method to fine-tune LLM's with its simple interface and easy-to-use API commands. The example Colab Notebook that we have provided at the top of the report provides the fine-tuning steps with OpenAI. 

The other option has been through the HuggingFace library. 


## Evaluation

To objectively and efficiently measure the impact of domain-specific datsets (specifically curated dataset on advanced mathematics problems), it is important to develop tools to quantitatively assess the performance of LLM's and the improvements resulting from additional data. Here, we outline the process to evaluate our LLM's performance on the AM201 dataset. 

## Future Work







