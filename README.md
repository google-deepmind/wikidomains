# WikiDomains

This repository hosts the WikiDomains dataset used in our paper: [Evaluating LLMs for Targeted Concept Simplification for Domain-Specific Texts](https://www.arxiv.org/abs/2410.20763).

## Abstract

One useful application of NLP models is to support people in reading complex text from unfamiliar domains (e.g., scientific articles). Simplifying the entire text makes it understandable but sometimes removes important details. On the contrary, helping adult readers understand difficult concepts in context can enhance their vocabulary and knowledge. In a preliminary human study, we first identify that lack of context and unfamiliarity with difficult concepts is a major reason for adult readers' difficulty with domain-specific text. We then introduce *targeted concept simplification*, a simplification task for rewriting text to help readers comprehend text containing unfamiliar concepts. We also introduce **WikiDomains**, a new dataset of 22k definitions from 13 academic domains paired with a difficult concept within each definition. We benchmark the performance of open-source and commercial LLMs and a simple dictionary baseline on this task across human judgments of ease of understanding and meaning preservation. Interestingly, our human judges preferred explanations about the difficult concept more than simplification of the concept phrase. Further, no single model achieved superior performance across all quality dimensions, and automated metrics also show low correlations with human evaluations of concept simplification (∼0.2), opening up rich avenues for research on personalized human reading comprehension support.

## Data

The WikiDomains dataset is available at: [link](https://console.cloud.google.com/storage/browser/wikidomains). The data can be downloaded via direct download using:

```bash
wget https://storage.googleapis.com/wikidomains/wikidomains_train.tsv
wget https://storage.googleapis.com/wikidomains/wikidomains_dev.tsv
wget https://storage.googleapis.com/wikidomains/wikidomains_test.tsv
```

The dataset files when downloaded will take up approximately 28MB. The data will contain 15,873/3,384/3,304 examples in the train/dev/test set files, respectively. Note: our targeted concept simplification task in the paper only used the zero-shot and few-shot settings with the test set only.

WikiDomains is a dataset from English Wikipedia articles, consisting of terms (article titles), the term definition taken from the article's lead sentence, a difficult concept contained in each definition, and the domain (i.e. academic area) to which the article belongs.

We selected thirteen domains derived from Wikipedia’s categorization of articles:
Food & Drink, Performing arts, Business & Economics, Politics & Government, Biology, Chemistry, Computing, Earth and Environment, Mathematics, Medicine & Health, Physics, Engineering, Technology.

The Targeted Concept Simplification task presented in our paper uses the "term", "definition", and "difficult_concept" columns as the task inputs.  We only considered the few-shot and zero-shot set-ups for the task in the paper without fine-tuning.

The following are the columns in the dataset, and their descriptions.

- `page_id` (int): The Wikipedia page ID of the corresponding article.
- `qid` (int): The Wikidata ID of the entity linked to the concept of the article.
- `term` (str): The article title (term) of the Wikipedia article.
- `definition` (str): The first sentence of the lead section of the Wikipedia article.
- `difficult_concept` (str): The phrase in the definition that has been identified as a ``difficult concept'' for the Targeted Concept Simplification task.
- `term_domain` (str): The domain (topic) assignment for the Wikipedia article.
- `term_pagerank_score` (float): The pagerank score of the article computed on Wikipedia.
- `term_frequency_indomain` (int): The frequency of the term within articles of the same domain.
- `term_frequency_outdomain` (int): The frequency of the term across articles outside of the domain.
- `term_lead_section` (str): The lead section of the Wikipedia article.

## Citing this work

If you use any of the material here, please cite the following paper:

```latex
@article{asthana2024evaluating,
  title={Evaluating LLMs for Targeted Concept Simplification forDomain-Specific Texts},
  author={Asthana, Sumit and Rashkin, Hannah and Clark, Elizabeth and Huot, Fantine and Lapata, Mirella},
  journal={arXiv preprint arXiv:2410.20763},
  year={2024}
}
```

## License and disclaimer

Copyright 2024 DeepMind Technologies Limited

All software is licensed under the Apache License, Version 2.0 (Apache 2.0);
you may not use this file except in compliance with the Apache 2.0 license.
You may obtain a copy of the Apache 2.0 license at:
https://www.apache.org/licenses/LICENSE-2.0

Certain data elements, including the `term` and `definition` (str), are from Wikipedia and copyright is owned by the authors listed on the relevant Wikipedia page, which can be identified from the data element `page_id` (int), and are licensed under the Creative Commons Attribution-Sharealike 4.0 International License (CC-BY-SA).
You may obtain a copy of the CC-BY-SA license at:
https://creativecommons.org/licenses/by-sa/4.0/legalcode.en

All other materials are also licensed under the Creative Commons Attribution-Sharealike 4.0 International License (CC-BY-SA).
You may obtain a copy of the CC-BY-SA license at:
https://creativecommons.org/licenses/by-sa/4.0/legalcode.en

Unless required by applicable law or agreed to in writing, all software and materials distributed here under the Apache 2.0 or CC-BY-SA licenses are distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the licenses for the specific language governing permissions and limitations under those licenses.

This is not an official Google product.
