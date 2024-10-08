Phi-3.5-MoE is a lightweight, state-of-the-art open model built upon datasets used for Phi-3 - synthetic data and filtered publicly available documents - with a focus on very high-quality, reasoning dense data. The model supports multilingual and comes with 128K context length (in tokens). The model underwent a rigorous enhancement process, incorporating supervised fine-tuning, proximal policy optimization, and direct preference optimization to ensure precise instruction adherence and robust safety measures.

### Resources
🏡 [Phi-3 Portal](https://azure.microsoft.com/en-us/products/phi-3) <br>
📰 [Phi-3 Microsoft Blog](https://aka.ms/phi3.5-techblog) <br>
📖 [Phi-3 Technical Report](https://arxiv.org/abs/2404.14219) <br>
👩‍🍳 [Phi-3 Cookbook](https://github.com/microsoft/Phi-3CookBook) <br>

### Model Summary
|      |      |
|------|------|
| **Architecture** | Phi-3.5-MoE has 16x3.8B parameters with 6.6B active parameters when using 2 experts. The model is a mixture-of-expert decoder-only Transformer model using the tokenizer with vocabulary size of 32,064. |
| **Inputs**  | Text. It is best suited for prompts using chat format. |
| **Context length** | 128K tokens |
| **GPUs** | 512 H100-80G |
| **Training time** | 23 days |
| **Training data** | 4.9T tokens |
| **Outputs** | Generated text in response to the input |
| **Dates** | Trained between April and August 2024 |
| **Status** | This is a static model trained on an offline dataset with cutoff date October 2023 for publicly available data. Future versions of the tuned models may be released as we improve models. |
| **Supported languages** | Arabic, Chinese, Czech, Danish, Dutch, English, Finnish, French, German, Hebrew, Hungarian, Italian, Japanese, Korean, Norwegian, Polish, Portuguese, Russian, Spanish, Swedish, Thai, Turkish, Ukrainian |
| **Release date** | August 20, 2024 |
| **License** | MIT |


## Benchmarks

To understand the capabilities, we compare Phi-3.5-MoE with a set of models over a variety of benchmarks using our internal benchmark platform. At the high-level overview of the model quality on representative benchmarks:

| Category | Benchmark | Phi-3.5-MoE-instruct | Mistral-Nemo-12B-instruct-2407 | Llama-3.1-8B-instruct | Gemma-2-9b-It | Gemini-1.5-Flash | GPT-4o-mini-2024-07-18 (Chat) |
|--|--|--|--|--|--|--|--|
| Popular aggregated benchmark | Arena Hard | 37.9 | 39.4 | 25.7 | 42.0 | 55.2 | 75.0 |
| | BigBench Hard CoT (0-shot) | 79.1 | 60.2 | 63.4 | 63.5 | 66.7 | 80.4 |
| | MMLU (5-shot) | 78.9 | 67.2 | 68.1 | 71.3 | 78.7 | 77.2 |
| | MMLU-Pro (0-shot, CoT) | 54.3 | 40.7 | 44.0 | 50.1 | 57.2 | 62.8 |
| Reasoning | ARC Challenge (10-shot) | 91.0 | 84.8 | 83.1 | 89.8 | 92.8 | 93.5 |
| | BoolQ (2-shot) | 84.6 | 82.5 | 82.8 | 85.7 | 85.8 | 88.7 |
| | GPQA (0-shot, CoT) | 36.8 | 28.6 | 26.3 | 29.2 | 37.5 | 41.1 |
| | HellaSwag (5-shot) | 83.8 | 76.7 | 73.5 | 80.9 | 67.5 | 87.1 |
| | OpenBookQA (10-shot) | 89.6 | 84.4 | 84.8 | 89.6 | 89.0 | 90.0 |
| | PIQA (5-shot) | 88.6 | 83.5 | 81.2 | 83.7 | 87.5 | 88.7 |
| | Social IQA (5-shot) | 78.0 | 75.3 | 71.8 | 74.7 | 77.8 | 82.9 |
| | TruthfulQA (MC2) (10-shot) | 77.5 | 68.1 | 69.2 | 76.6 | 76.6 | 78.2 |
| | WinoGrande (5-shot) | 81.3 | 70.4 | 64.7 | 74.0 | 74.7 | 76.9 |
| Multilingual | Multilingual MMLU (5-shot) | 69.9 | 58.9 | 56.2 | 63.8 | 77.2 | 72.9 |
| | MGSM (0-shot CoT) | 58.7 | 63.3 | 56.7 | 75.1 | 75.8 | 81.7 |
| Math | GSM8K (8-shot, CoT) | 88.7 | 84.2 | 82.4 | 84.9 | 82.4 | 91.3 |
| | MATH (0-shot, CoT) | 59.5 | 31.2 | 47.6 | 50.9 | 38.0 | 70.2 |
| Long context | Qasper | 40.0 | 30.7 | 37.2 | 13.9 | 43.5 | 39.8 |
| | SQuALITY | 24.1 | 25.8 | 26.2 | 0.0 | 23.5 | 23.8 |
| Code Generation | HumanEval (0-shot) | 70.7 | 63.4 | 66.5 | 61.0 | 74.4 | 86.6 |
| | MBPP (3-shot) | 80.8 | 68.1 | 69.4 | 69.3 | 77.5 | 84.1 |
| **Average** | | **69.2** | **61.3** | **61.0** | **63.3** | **68.5** | **74.9** |

We take a closer look at different categories across 80 public benchmark datasets at the table below:
| Category | Phi-3.5-MoE-instruct | Mistral-Nemo-12B-instruct-2407 | Llama-3.1-8B-instruct | Gemma-2-9b-It | Gemini-1.5-Flash | GPT-4o-mini-2024-07-18 (Chat) |
|--|--|--|--|--|--|--|
| Popular aggregated benchmark | 62.6 | 51.9 | 50.3 | 56.7 | 64.5 | 73.9 |
| Reasoning | 78.7 | 72.2 | 70.5 | 75.4 | 77.7 | 80.0 |
| Language understanding | 71.8 | 67.0 | 62.9 | 72.8 | 66.6 | 76.8 |
| Robustness | 75.6 | 65.2 | 59.8 | 64.7 | 68.9 | 77.5 |
| Long context | 25.5 | 24.5 | 25.5 | 0.0 | 27.0 | 25.4 |
| Math | 74.1 | 57.7 | 65.0 | 67.9 | 60.2 | 80.8 |
| Code generation | 68.3 | 56.9 | 65.8 | 58.3 | 66.8 | 69.9 |
| Multilingual | 65.8 | 55.3 | 47.5 | 59.6 | 64.3 | 76.6 |

Overall, Phi-3.5-MoE with only **6.6B active parameters** achieves a similar level of language understanding and math as much larger models. Moreover, the model outperforms bigger models in reasoning capability and only behind GPT-4o-mini. However, it is still fundamentally limited by its size for certain tasks. The model simply does not have the capacity to store too much factual knowledge, therefore, users may experience factual incorrectness. However, we believe such weakness can be resolved by augmenting Phi-3.5 with a search engine, particularly when using the model under RAG settings.

### Multilingual

The table below highlights multilingual capability of Phi-3.5-MoE on multilingual MMLU, MEGA, and multilingual MMLU-pro datasets. Overall, we observed that even with just 6.6B active parameters, the model is very competitive on multilingual tasks in comparison to other models with a much bigger active parameters.

| Category | Phi-3.5-MoE-instruct | Mistral-Nemo-12B-instruct-2407 | Llama-3.1-8B-instruct | Gemma-2-9b-It | Gemini-1.5-Flash | GPT-4o-mini-2024-07-18 (Chat) |
|--|--|--|--|--|--|--|
| Multilingual MMLU | 69.9 | 58.9 | 56.2 | 63.8 | 77.2 | 72.9 |
| Multilingual MMLU-Pro | 45.3 | 34.0 | 21.4 | 43.0 | 57.9 | 53.2 |
| MGSM | 58.7 | 63.3 | 56.7 | 75.1 | 75.8 | 81.7 |
| MEGA MLQA | 65.3 | 61.2 | 45.2 | 54.4 | 61.6 | 70.0 |
| MEGA TyDi QA | 67.1 | 63.7 | 54.5 | 65.6 | 63.6 | 81.8 |
| MEGA UDPOS | 60.4 | 58.2 | 54.1 | 56.6 | 62.4 | 66.0 |
| MEGA XCOPA | 76.6 | 10.8 | 21.1 | 31.2 | 95.0 | 90.3 |
| MEGA XStoryCloze | 82.8 | 92.3 | 71.0 | 87.0 | 20.7 | 96.6 |
| **Average** | **65.8** | **55.3** | **47.5** | **59.6** | **64.3** | **76.6** |

### Long Context

Phi-3.5-MoE supports 128K context length, therefore the model is capable of several long context tasks including long document/meeting summarization, long document QA, multilingual context retrieval. We see that Phi-3.5 is clearly better than Gemma-2 family which only supports 8K context length. Phi-3.5-MoE-instruct is very competitive with other much larger open-weight models such as Llama-3.1-8B-instruct, and Mistral-Nemo-12B-instruct-2407.

| Benchmark | Phi-3.5-MoE-instruct | Mistral-Nemo-12B-instruct-2407 | Llama-3.1-8B-instruct | Gemini-1.5-Flash | GPT-4o-mini-2024-07-18 (Chat) |
|--|--|--|--|--|--|
| GovReport | 26.4 | 25.6 | 25.1 | 27.8 | 24.8 |
| QMSum | 19.9 | 22.1 | 21.6 | 24.0 | 21.7 |
| Qasper | 40.0 | 30.7 | 37.2 | 43.5 | 39.8 |
| SQuALITY | 24.1 | 25.8 | 26.2 | 23.5 | 23.8 |
| SummScreenFD | 16.9 | 18.2 | 17.6 | 16.3 | 17.0 |
| **Average** | **25.5** | **24.5** | **25.5** | **27.0** | **25.4** |

RULER: a retrieval-based benchmark for long context understanding
| Model | 4K | 8K | 16K | 32K | 64K | 128K | Average |
|--|--|--|--|--|--|--|--|
| Phi-3.5-MoE-instruct | 94.8 | 93 | 93.2 | 91.6 | 85.7 | 64.2 | **87.1** |
| Llama-3.1-8B-instruct | 95.5 | 93.8 | 91.6 | 87.4 | 84.7 | 77.0 | **88.3** |
| Mistral-Nemo-12B-instruct-2407 | 87.8 | 87.2 | 87.7 | 69.0 | 46.8 | 19.0 | **66.2** |

RepoQA: a benchmark for long context code understanding
| Model | Python | C++ | Rust | Java | TypeScript | Average |
|--|--|--|--|--|--|--|
| Phi-3.5-MoE-instruct | 89 | 74 | 81 | 88 | 95 | **85** |
| Llama-3.1-8B-instruct | 80 | 65 | 73 | 76 | 63 | **71** |
| Mistral-7B-instruct-v0.3 | 61 | 57 | 51 | 61 | 80 | **62** |


## Intended Use

### Primary Use Cases
The model is intended for broad commercial and research use in English. The model provides uses for general purpose AI systems and applications which require:

1) Memory/compute constrained environments
2) Latency bound scenarios
3) Strong reasoning (especially code, math and logic)

Our model is designed to accelerate research on language and multimodal models, for use as a building block for generative AI powered features.

### Out-of-Scope Use Cases

Our models are not specifically designed or evaluated for all downstream purposes. Developers should consider common limitations of language models as they select use cases, and evaluate and mitigate for accuracy, safety, and fairness before using within a specific downstream use case, particularly for high-risk scenarios. Developers should be aware of and adhere to applicable laws or regulations (including privacy, trade compliance laws, etc.) that are relevant to their use case.

**Nothing contained in this Model Card should be interpreted as or deemed a restriction or modification to the license the model is released under.**

## Responsible AI Considerations

Like other language models, the Phi family of models can potentially behave in ways that are unfair, unreliable, or offensive. Some of the limiting behaviors to be aware of include:

* Quality of Service: The Phi models are trained primarily on English text and some additional multilingual text. Languages other than English will experience worse performance as well as performance disparities across non-English. English language varieties with less representation in the training data might experience worse performance than standard American English.   
* Multilingual performance and safety gaps: We believe it is important to make language models more widely available across different languages, but the Phi 3 models still exhibit challenges common across multilingual releases. As with any deployment of LLMs, developers will be better positioned to test for performance or safety gaps for their linguistic and cultural context and customize the model with additional fine-tuning and appropriate safeguards.
* Representation of Harms & Perpetuation of Stereotypes: These models can over- or under-represent groups of people, erase representation of some groups, or reinforce demeaning or negative stereotypes. Despite safety post-training, these limitations may still be present due to differing levels of representation of different groups, cultural contexts, or prevalence of examples of negative stereotypes in training data that reflect real-world patterns and societal biases. 
* Inappropriate or Offensive Content: These models may produce other types of inappropriate or offensive content, which may make it inappropriate to deploy for sensitive contexts without additional mitigations that are specific to the use case. 
* Information Reliability: Language models can generate nonsensical content or fabricate content that might sound reasonable but is inaccurate or outdated.  
* Limited Scope for Code: Majority of Phi-3 training data is based in Python and use common packages such as "typing, math, random, collections, datetime, itertools". If the model generates Python scripts that utilize other packages or scripts in other languages, we strongly recommend users manually verify all API uses.
* Long Conversation: Phi-3 models, like other models, can in some cases generate responses that are repetitive, unhelpful, or inconsistent in very long chat sessions in both English and non-English languages. Developers are encouraged to place appropriate mitigations, like limiting conversation turns to account for the possible conversational drift

Developers should apply responsible AI best practices, including mapping, measuring, and mitigating risks associated with their specific use case and cultural, linguistic context. Phi-3 family of models are general purpose models. As developers plan to deploy these models for specific use cases, they are encouraged to fine-tune the models for their use case and leverage the models as part of broader AI systems with language-specific safeguards in place. Important areas for consideration include:  
* Allocation: Models may not be suitable for scenarios that could have consequential impact on legal status or the allocation of resources or life opportunities (ex: housing, employment, credit, etc.) without further assessments and additional debiasing techniques.
* High-Risk Scenarios: Developers should assess the suitability of using models in high-risk scenarios where unfair, unreliable or offensive outputs might be extremely costly or lead to harm. This includes providing advice in sensitive or expert domains where accuracy and reliability are critical (ex: legal or health advice). Additional safeguards should be implemented at the application level according to the deployment context. 
* Misinformation: Models may produce inaccurate information. Developers should follow transparency best practices and inform end-users they are interacting with an AI system. At the application level, developers can build feedback mechanisms and pipelines to ground responses in use-case specific, contextual information, a technique known as Retrieval Augmented Generation (RAG).   
* Generation of Harmful Content: Developers should assess outputs for their context and use available safety classifiers or custom solutions appropriate for their use case. 
* Misuse: Other forms of misuse such as fraud, spam, or malware production may be possible, and developers should ensure that their applications do not violate applicable laws and regulations.

## Training Data

Our training data includes a wide variety of sources, totaling 4.9 trillion tokens (including 10% multilingual), and is a combination of 
1) publicly available documents filtered rigorously for quality, selected high-quality educational data, and code;
2) newly created synthetic, “textbook-like” data for the purpose of teaching math, coding, common sense reasoning, general knowledge of the world (science, daily activities, theory of mind, etc.);
3) high quality chat format supervised data covering various topics to reflect human preferences on different aspects such as instruct-following, truthfulness, honesty and helpfulness. 

We are focusing on the quality of data that could potentially improve the reasoning ability for the model, and we filter the publicly available documents to contain the correct level of knowledge. As an example, the result of a game in premier league in a particular day might be good training data for frontier models, but we need to remove such information to leave more model capacity for reasoning for the small size models. More details about data can be found in the [Phi-3 Technical Report](https://arxiv.org/pdf/2404.14219).

## Sample Inputs and Outputs (for real-time inference)

### **Sample input**
```json
{
  "input_data": {
    "input_string": [
      {
        "role": "user",
        "content": "I am going to Paris, give me a list of 10 places to visit"
      }
    ],
    "parameters": {
      "temperature": 0.7,
      "top_p": 0.9,
      "do_sample": true,
      "max_new_tokens": 1000
    }
  }
}
``` 

### **Sample output**
```json
{
  "output": " 1. Eiffel Tower: Visit the iconic symbol of Paris, offering breathtaking views of the city.\n\n2. Louvre Museum: Explore one of the world's largest and most visited museums, home to thousands of works of art, including the Mona Lisa.\n\n3. Notre-Dame Cathedral: Marvel at the stunning Gothic architecture of this famous cathedral, although note that it is currently under renovation due to the 2019 fire.\n\n4. Montmartre: Discover this historic and artistic neighborhood, famous for its bohemian past and the stunning Sacré-Cœur Basilica.\n\n5. Seine River Cruise: Take a relaxing cruise on the Seine River, seeing some of the city's most famous landmarks like the Louvre, Notre-Dame, and the Eiffel Tower from a unique perspective.\n\n6. Champs-Élysées: Visit this famous avenue lined with shops, cafes, and theaters. Don't forget to check out the Arc de Triomphe at its end.\n\n7. Palace of Versailles: Take a day trip from Paris to explore the opulent palace and gardens of Versailles, a UNESCO World Heritage site.\n\n8. Sacré-Cœur Basilica: Located at the highest point in the city, this basilica offers panoramic views of Paris.\n\n9. Latin Quarter: Stroll through this historic and vibrant neighborhood, famous for its student life, lively atmosphere, and cafes.\n\n10. Musée d'Orsay: Visit this museum, housing an impressive collection of Impressionist and Post-Impressionist art, including works by Monet, Degas, Renoir, and Van Gogh."
}
```


## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft’s Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party’s policies.
