# deidentification-medical-records

## Google Colab Notebooks and Saved Models

#### Dataset

The **synthetic dataset** consists of 2 JSON files: `annotations.json` and `discharge_summaries.json`.

The `discharge_summaries` file contains a `document_id` and the text of the medical record. The `annotations` file contains the `annotation_id`, `start_index`, `stop_index`, `entity`, `entity_type`, and the `document_id`.

Here are the dataset statistics:

| Metric                       | Value   |   | Entity Type | Count |
| ---------------------------- | ------- | --- | ----------- | ----- |
| Number of Documents          | 1000    |   | NAME        | 2000  |
| Number of Annotations        | 9000    |   | AGE         | 1000  |
| Average Annotations per Document | 9.0     |   | DATE        | 3000  |
| Average Document Length (words)| 205.9   |   | IDNUM       | 1000  |
|                              |         |   | LOCATION    | 1000  |
|                              |         |   | PHONE       | 1000  |

#### Fine Tuning Pre-trained Models and Fresh training

We explored two approaches for training:

1.  **Fine tune** the three pre-trained models available along with the original paper, with the synthetic data and measure the performance.
2.  **Train the three base models** BERT, RoBERTa, DistilBERT with the synthetic data and measure the performance.

Each of the 3 model files contain both fine tuning of the pretrained model and fresh training with the synthetic data:

1.  `Bert_KindLab_Predict_FinetuneLLM.ipynb`
2.  `Roberta_KindLab_Predict_FinetuneLLM.ipynb`
3.  `Distilbert_KindLab_Predict_FinetuneLLM.ipynb`

Additionally, two more LLM models were trained as an extension. Since there were no pretrained models for these, only fresh training with the synthetic data was performed:

4.  `Electra_LLM.ipynb`
5.  `Deberta_LLM.ipynb`

#### Hyperparameter Tuning for BERT

We experimented with several variations of the LLM training hyperparameters. This was done during the fine-tuning of the pre-trained model `KindLab/bert-deid` and also during the fresh training of BERT with synthetic data. In the hyperparameter tuning, we explored the impact of varying learning rates, batch sizes, and training epochs on evaluation metrics such as precision, recall, F1-score, and accuracy.

The following Colab notebooks contain the hyperparameter tuning experiments:

1.  `Hyperparameter_Fresh_BertLLM.ipynb`: Contains the hyperparameter tuning done for the fresh training with synthetic dataset.
2.  `Hyperparameter_KindLabFinetune_Bert.ipynb`: Contains the hyperparameter tuning done for the fine tuning of the pre-trained models with synthetic dataset.
3.  `Bert_CPU_Training_Fresh.ipynb`: Contains the fine tuning of the BERT model with CPU as the runtime environment.

#### Saved Models

The models obtained after **fresh training** with the synthetic dataset are saved in the 5 folders below:

*   [bert_base_cased_finetuned](https://drive.google.com/open?id=1fS94C2DxVPyzw1FDUnSWoAdipn_DuVfn&usp=drive_copy)
*   [deberta_base_cased_finetuned](https://drive.google.com/open?id=1Uk4pwOzvRnMs-m59wov5XVzyYdTD9Wo5&usp=drive_copy)
*   [distilbert_base_finetuned](https://drive.google.com/open?id=17sUc_UZOCmyrPfMPPrHiHTeYtsaT-xQZ&usp=drive_copy)
*   [Electra_base_cased_finetuned](https://drive.google.com/open?id=1HTTL4bnl3KzB3T-R-6mkOvw1-0tyu16U&usp=drive_copy)
*   [Roberta_base_finetuned](https://drive.google.com/open?id=1hhvCobsMw4MRR0Pu_iJitNlBCHLVgScG&usp=drive_copy)

The models obtained after **fine-tuning the pretrained models** with the synthetic dataset are saved in the 3 folders below:

*   [kindlab_bert_deid_finetuned](https://drive.google.com/open?id=1aTonoiHHQthgT9meEwyFjlf-cr8ATy2v&usp=drive_copy)
*   [kindlab_distilbert_deid_finetuned](https://drive.google.com/open?id=1PHp96AgyJ54RQqYV9Fkuse7CPFv1eSps&usp=drive_copy)
*   [kindlab_roberta_deid_finetuned](https://drive.google.com/open?id=16fzqUvLwc5RkiKWxyc2bw4ehCnZwJK6B&usp=drive_copy)