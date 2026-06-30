<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github.com/AMALIA-LLM/amalia-llm.github.io/blob/main/source/_static/logo/logo-color-white.png?raw=true" width="300">
  <source media="(prefers-color-scheme: light)" srcset="https://github.com/AMALIA-LLM/amalia-llm.github.io/blob/main/source/_static/logo/logo-color-black.png?raw=true" width="300">
  <img src="https://github.com/AMALIA-LLM/amalia-llm.github.io/blob/main/source/_static/logo/logo-color-black.png?raw=true" alt="AMALIA" width="300"/>
</picture>
<br/>

**A Fully Open Large Language Model for European Portuguese**

[![Website](https://img.shields.io/badge/Website-amaliallm.pt-blue)](https://amaliallm.pt/)
[![HuggingFace](https://img.shields.io/badge/🤗%20HuggingFace-amalia--llm-yellow)](https://huggingface.co/amalia-llm)
[![Paper](https://img.shields.io/badge/Paper-Technical%20Report-red?logo=arxiv&logoColor=white)](https://arxiv.org/abs/2603.26511)
 
</div>

---

## 📚 Overview

Despite rapid progress in Large Language Models (LLMs), European Portuguese (pt-PT) remains significantly underrepresented in both training data and evaluation benchmarks.

**AMALIA aims to bridge this gap by delivering fully open-source resources and LLMs designed specifically for European Portuguese.**

To support the development of high-quality pt-PT language models, AMALIA provides an end-to-end open ecosystem spanning data processing, model training, and evaluation. Our contributions include:

* 🎯 **Prioritizing high-quality European Portuguese data** throughout every stage of training
* 🔓 **Releasing fully open models** tailored specifically for pt-PT
* 📊 **Introducing new evaluation benchmarks** for European Portuguese
* 🛠️ **Open-sourcing data cleaning, filtering, and processing pipelines** to enable further research

Our experimental results show that AMALIA is competitive with strong open-model baselines while delivering gains on European Portuguese benchmarks. These findings underscore the value of targeted language-specific training and native evaluation resources for underrepresented language variants.

---

## 📝 News

- **[2026/07]** 🚀 AMALIA public launch
- **[2026/06]** 📝 AMALIA-VL (Vision-Language) and PorTEXTO papers available on arXiv
- **[2026/05]** 📄 P3B3 benchmark accepted at MeLLM workshop at ACL 2026
- **[2026/04]** 📄 AMALIA and ALBA papers accepted at PROPOR 2026
- **[2026/03]** 📝 AMALIA LLM Technical report available on arXiv
- **[2026/02]** 📄 PHEB benchmark accepted at LREC 2026

---

## 🤗 Models

AMALIA provides multiple model variants tailored for different use cases:

| Model     | Size | Type            | HuggingFace                                                              |
|:----------|:-----|:----------------|:-------------------------------------------------------------------------|
| AMALIA-9B | 9B   | Language        | [🤗 Link](https://huggingface.co/collections/amalia-llm/amalia-llm-0626) |
| AMALIA-VL | 9B   | Vision-Language | [🤗 Link](https://huggingface.co/collections/amalia-llm/amalia-vl-0626)  |
> Additional derivative models built on top of AMALIA are also available on [HuggingFace](https://huggingface.co/amalia-llm).

---


## 🗂️ Project Repositories

This organization contains multiple repositories covering different aspects of the AMALIA project:

### Training & Data Processing

| Repository                                                                 | Description                                                                             |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| [datatrove-amalia](https://github.com/AMALIA-LLM/datatrove-amalia)         | Customizable pipeline processing blocks for data handling                               |
| [arquivo_processing](https://github.com/AMALIA-LLM/arquivo_processing)     | ArquivoPT data processing pipeline used for AMALIA                                      |
| [Megatron-LM-pretrain](https://github.com/AMALIA-LLM/Megatron-LM-pretrain) | Modular codebase for AMALIA model pretraining, based on Megatron-LM                     |
| [amalia-lm-post-train](https://github.com/AMALIA-LLM/amalia-lm-post-train) | Post-training pipeline for supervised fine-tuning and preference optimization of AMALIA |
| [amalia-vl-sft](https://github.com/AMALIA-LLM/amalia-vl-sft)               | Code and scripts for supervised fine-tuning of AMALIA Vision-Language models            |
| [amalia-vl-dpo](https://github.com/AMALIA-LLM/amalia-vl-dpo)               | Code and scripts for direct preference optimization of AMALIA Vision-Language models    |


### Evaluation & Benchmarks

| Repository                                                     | Description                                                                                                |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| [amalia-lm-eval](https://github.com/AMALIA-LLM/amalia-lm-eval) | Evaluation suite for AMALIA LLM                                                                            |
| [amalia-vl-eval](https://github.com/AMALIA-LLM/amalia-vl-eval) | Evaluation framework for AMALIA Vision-Language models                                                     |
| [alba-benchmark](https://github.com/AMALIA-LLM/alba-benchmark) | ALBA: A European Portuguese Benchmark for Evaluating Language and Linguistic Dimensions in Generative LLMs |
| [p3b3-benchmark](https://github.com/AMALIA-LLM/p3b3-benchmark) | P3B3: A Multi-Turn Conversational Benchmark for Measuring European and Brazilian Portuguese Variety Bias   |
| [pheb](https://github.com/AMALIA-LLM/pheb)                     | Portuguese High (School) Exams Benchmark                                                                   |

---

## 🚀 Deployment and Quickstart

AMALIA can be served using any platform or library for LLM inference and serving. However, we recommend using it with [vLLM](https://docs.vllm.ai/en/stable/) on an environment with a Python >=3.12 version installed. 

To serve the AMALIA model just execute the following command on any shell terminal with vLLM installed:
~~~
vllm serve amalia-llm/AMALIA-9B-0626-DPO
~~~

Executing the previous command will serve the AMALIA model and will expose it locally on the url: http://localhost:8000.

### Interacting with the AMALIA LLM

With the model served with vLLM, it can be queried on a terminal shell using `curl` via
~~~shell
curl -X POST http://localhost:8000/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer api_key" \
    --data ’{"model": "amalia-llm/AMALIA-9B-0626-DPO", \
    "messages": [{"role": "user", "content": "Olá"}]}’
~~~
This example sends the query "Olá" to AMALIA and displays the model's answer. 

Alternatively, AMALIA can be used through a Python script using either the `requests` library or the [OpenAI API](https://developers.openai.com/api/reference/overview) for python. The following code shows a snippet of how to use `requests` to interact with AMALIA, using the same example as before:
~~~python
import requests

url = "http://localhost:8000/v1/chat/completions"

headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer api_key"
}

payload = {
    "model": "amalia-llm/AMALIA-9B-0626-DPO",
    "messages": [
        {
            "role": "user",
            "content": "Olá"
        }
    ]
}

response = requests.post(url, headers=headers, json=payload)

if response.status_code == 200:
    print(response.json()['choices'][0]['message']['content'])
else:
    print(f"Error {response.status_code}: {response.text}")
~~~

Using the python `openai` library is as following:

~~~python
from openai import OpenAI

url = "http://localhost:8000/v1/chat/completions"

client = OpenAI(base_url=url, api_key='')

messages = [
    {
        'role': 'user', 
        'content': 'Olá'
    }
]

outputs = client.chat.completions.create(
    model="amalia-llm/AMALIA-9B-0626-DPO",
    messages=messages,
)
answer = outputs.choices[0].message.content.strip()
print(answer)
~~~


### Interacting with the AMALIA-VL

AMALIA also has been developed both in language-only and vison-language variants. In order to interact with the VLM variant, first serve the vision-language variant, here we will use `amalia-llm/AMALIA-VL-DPO`. After serving with the command above, the model will be at http://localhost:8000, and we can interact with it, like before, either on the terminal via `curl` or using a Python script using the `requests` or `openai` libraries.

```shell
# curl

curl -X POST http://127.0.0.1:8001/v1/chat/completions \
       -H "Content-Type: application/json" \
       -H "Authorization: Bearer api_key" \
       --data '{"model": "amalia-llm/AMALIA-VL-DPO", \
       "messages": [{"role": "user", "content": \
        [{"type": "image","image": "path/to/image.png"}, \
        {"type": "text","text": "O que está nesta imagem?"}]}]}'
```

```python
# requests

import requests

url = "http://127.0.0.1:8001/v1/chat/completions"

headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer api_key"
}

payload = {
    "model": "amalia-llm/AMALIA-VL-DPO",
    "messages": [
        {
            "role": "user",
            "content": [
                {
                    "type": "image",
                    "image": "path/to/image.png"
                },
                {
                    "type": "text",
                    "text": "O que está nesta imagem?"
                }
            ]
        }
    ]
}

response = requests.post(url, headers=headers, json=payload)

if response.status_code == 200:
    print(response.json()['choices'][0]['message']['content'])
else:
    print(f"Error {response.status_code}: {response.text}")
```

```python
# OpenAI API

from openai import OpenAI

url = "http://localhost:8000/v1/chat/completions"

client = OpenAI(base_url=url, api_key='')

messages = [
    {
        'role': 'user', 
        "content": [
            {
                "type": "image",
                "image": "path/to/image.png"
            },
            {
                "type": "text",
                "text": "O que está nesta imagem?"
            }
        ]
    }
]

outputs = client.chat.completions.create(
    model="amalia-llm/AMALIA-9B-0626-DPO",
    messages=messages,
)
answer = outputs.choices[0].message.content.strip()
print(answer)
```

---

## 📖 Citation

If you use AMALIA in your work, please cite:

```bibtex
@inproceedings{simplicio-etal-2026-amalia,
    title = "{AMALIA}: A Fully Open Large Language Model for {E}uropean {P}ortuguese",
    author = "Simpl{\'i}cio, Afonso and Vinagre, Gon{\c{c}}alo and Ramos, Miguel Moura and Tavares, Diogo and Ferreira, Rafael and Attanasio, Giuseppe and Alves, Duarte M. and Calvo, In{\^e}s and Vieira, In{\^e}s and Guerra, Rui and Furtado, James and Canaverde, Beatriz and Paulo, Iago and Ramos, Vasco and Gl{\'o}ria-Silva, Diogo and Faria, Miguel and Treviso, Marcos and Gomes, Daniel and Gomes, Pedro and Semedo, David and Martins, Andr{\'e} and Magalh{\~a}es, Jo{\~a}o",
    booktitle = "Proceedings of the 17th International Conference on Computational Processing of {P}ortuguese ({PROPOR} 2026) - Vol. 1",
    month = apr,
    year = "2026",
    address = "Salvador, Brazil",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2026.propor-1.38/",
    pages = "380--391",
    isbn = "979-8-89176-387-6"
}
```

If you use AMALIA-VL (Vision-Language):

```bibtex
@misc{amaliavl2026,
    title = {AMALIA-VL: Vision-Language Model for European Portuguese}, 
    author = {AMALIA Team},
    year = {2026},
    eprint = {2606.19100},
    archivePrefix = {arXiv},
    primaryClass = {cs.CV},
    url = {https://arxiv.org/abs/2606.19100}
}
```

---

##  Acknowledgments

We would like to thank the following projects and communities that made AMALIA possible:

- **[EleutherAI lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness)** - For the evaluation harness and benchmark framework
- **[lmms-eval](https://github.com/evolvinglmms-lab/lmms-eval)** - For the multimodal evaluation framework basis
- **[Megatron-LM](https://github.com/NVIDIA/Megatron-LM)** - For the pre-training framework
- **[DataTrove](https://github.com/huggingface/datatrove)** - For data processing pipeline tools
- **[ArquivoPT](https://arquivo.pt/)** - For providing access to high-quality Portuguese web archive data
- All contributors and researchers who provided feedback and continuous support to the AMALIA project.

---

<div align="center">

**AMALIA** - Advancing European Portuguese in the era of Large Language Models

[Website](https://amaliallm.pt/) • [HuggingFace](https://huggingface.co/amalia-llm) • [GitHub](https://github.com/AMALIA-LLM)

</div>

