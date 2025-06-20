**Parent Topic** : [[Generative AI]]
**Created** : June 13, 2025 | 12:26 PM
**Platform** : #pw 

---
- Text generation is one of the primary use case of LLM or GenAI. 
- GPT (Generative Pre-Trained Transformer) is one of the breakthrough for GenAI.
### GPT Workflow
- When we ask a question or give a prompt in ChatGPT, that questions are transferred to the backend via as an API call where the LLM Models has been hosted and return us the output (which has been generated)
-  We will try to replicate the similar kind of work flow in out jupyter notebook using the openai library and [OpenAI Text gen guide Docs](https://platform.openai.com/docs/guides/) 
## Notebook workflow
- Import all libraries
```
import openai
import os
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from IPython.display import Markdown
from PIL import Image
import base64
```
- Create an openai client to make api calls
- We need to generate an openai [[API]] key
	- Using GPT Models are not free, OpenAI charges as usage per token
	- Token can be viewed as words, Suppose we asked `What is Programming?` - Here we have 4 tokens and what the model will generate will also be some amount of tokens and we will be charged on basis of that. We get 5$ of free usage per month
	- Visualize Tokens [Tokens](https://platform.openai.com/tokenizer)
- Steps to Follow 
	- Create a Prompt
	- Call GPT model via API
	- Store the response of the model
	- print the response

