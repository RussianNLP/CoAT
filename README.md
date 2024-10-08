# CoAT

CoAT🧥 (Corpus of Artificial Texts) is a large-scale corpus for Russian, which consists of 246k human-written texts from publicly available resources and artificial texts generated by 13 neural models, varying in the number of parameters, architecture choices, pre-training objectives, and downstream applications.
Each model is fine-tuned for one or more of six natural language generation tasks, ranging from paraphrase generation to text summarisation. CoAT provides two task formulations:

1. detection of artificial texts, i.e., classifying if a given text is machine-generated or human-written;

2. authorship attribution, i.e., classifying the author of a given text among 14 candidates.

The design of our corpus enables various experiment settings, ranging from analysing the dependence of the detector performance on the natural language generation task to the robustness of detectors towards unseen generative models and text domains.

CoAT is available on [HuggingFace](https://huggingface.co/datasets/RussianNLP/coat) and in the [datasets/](./datasets) folder of the repository. 

Read more about CoAT in our [paper](https://www.cambridge.org/core/journals/natural-language-processing/article/coat-corpus-of-artificial-texts/7E2CA97E21663CC031FB6BAFE56E0046) published in the Natural Language Processing journal in 2024.

## Design

We provide a high-level description of the data collection methodology. Please refer to our paper for more details on the CoAT design, post-processing and filtering procedure and general statistics.

### Human-written Texts

The human-written texts are collected from six domains: Russian National Corpus, social media, Wikipedia, news articles, digitalized personal diaries, and machine translation datasets.

### Machine-generated Texts

We use human-written texts as the input to 13 generative models, which are finetuned for one or more of the following natural language generation tasks: machine translation, paraphrase generation, text simplification, and text summarisation. In addition, we consider back-translation and zero-shot generation approaches.

<details>
    <summary>Models</summary>
<br>


Machine translation and back-translation via [EasyNMT](https://github.com/UKPLab/EasyNMT):
* OPUS-MT. Jörg Tiedemann and Santhosh Thottingal. 2020. [OPUS-MT – Building open translation services for the World](https://aclanthology.org/2020.eamt-1.61/)
* M-BART50. Yuqing Tang et al. 2020. [Multilingual Translation with Extensible Multilingual Pretraining and Finetuning](https://arxiv.org/abs/2008.00401)
* M2M-100. Angela Fan et al. 2021. [Beyond English-Centric Multilingual Machine Translation](https://jmlr.org/papers/volume22/20-1307/20-1307.pdf)

Paraphrase generation via [russian-paraphrasers](https://github.com/RussianNLP/russian_paraphrasers):
* [ruGPT2-Large](https://huggingface.co/sberbank-ai/rugpt2large)
* ruGPT3-Large. Zmitrovich et al., 2024. [A Family of Pretrained Transformer Language Models for Russian](https://aclanthology.org/2024.lrec-main.45/)
* [ruT5-Base-Multitask](https://huggingface.co/cointegrated/rut5-base-paraphraser)
* mT5-Small/Large. Linting Xue et al. 2021. [mT5: A Massively Multilingual Pre-trained Text-to-Text Transformer](https://aclanthology.org/2021.naacl-main.41/)

Text simplification via finetuning on a filtered version of the RuSimpleSentEval-2022 dataset ([Fenogenova, 2021](https://www.dialog-21.ru/media/5595/fenogenovaa141.pdf)):
* ruGP3-Small/Medium/Large. Zmitrovich et al., 2024. [A Family of Pretrained Transformer Language Models for Russian](https://aclanthology.org/2024.lrec-main.45/)
* mT5-Large. Linting Xue et al. 2021. [mT5: A Massively Multilingual Pre-trained Text-to-Text Transformer](https://aclanthology.org/2021.naacl-main.41/)
* ruT5-Large. Zmitrovich et al., 2024. [A Family of Pretrained Transformer Language Models for Russian](https://aclanthology.org/2024.lrec-main.45/)

Text summarization:
* [ruT5-base](https://huggingface.co/IlyaGusev/rut5_base_sum_gazeta)
* [M-BART](https://huggingface.co/IlyaGusev/mbart_ru_sum_gazeta)

Open-ended generation.
* ruGP3-Small/Medium/Large. Zmitrovich et al., 2024. [A Family of Pretrained Transformer Language Models for Russian](https://aclanthology.org/2024.lrec-main.45/)

</details>

## Leaderboards

- **Detection of artificial texts:** https://www.kaggle.com/competitions/coat-artificial-text-detection
- **Authorship attribution:** https://www.kaggle.com/competitions/coat-authorship-attribution

## Contact us

For any questions about CoAT, codebase, or dataset configurations used in the paper, please contact [vladism@ifi.uio.no](mailto:vladism@ifi.uio.no) or create an issue in this repository.

## Cite

```
@article{shamardinacoat,
  title={CoAT: Corpus of artificial texts},
  author={Shamardina, Tatiana and Saidov, Marat and Fenogenova, Alena and Tumanov, Aleksandr and Zemlyakova, Alina and Lebedeva, Anna and Gryaznova, Ekaterina and Shavrina, Tatiana and Mikhailov, Vladislav and Artemova, Ekaterina},
  journal={Natural Language Processing},
  pages={1--26},
  publisher={Cambridge University Press}
}
```

The early version of CoAT is published as RuATD.

```
@article{shamardinafindings,
  title={Findings of the The RuATD Shared Task 2022 on Artificial Text Detection in Russian},
  author={Shamardina, Tatiana and Mikhailov, Vladislav and Chernianskii, Daniil and Fenogenova, Alena and Saidov, Marat and Valeeva, Anastasiya and Shavrina, Tatiana and Smurov, Ivan and Tutubalina, Elena and Artemova, Ekaterina}
  journal={Computational Linguistics and Intellectual Technologies: Proceedings of the International Conference ''Dialogue 2022''},
  pages={1--15},
  publisher={RSUH}
}
```
