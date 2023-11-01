# Context-focused Prompt Tuning Pre-trained Code Models to Improve Code Summarization

Developers often describe specific contextual information in code comments to facilitate program understanding. Though existing code summarization approaches have considered context, they usually use the same context factors for all code methods but overlook developers' discriminative context focuses. This paper proposes a context-focused code summarization approach based on the prompt tuning technique. It enables the pre-trained code models to identify the specific context focus around a method and to generate the method's comment with corresponding essential contextual information, which improves the generated comment's informativeness and interpretability. 

## Experiments

To run the code, put the data in the following fold: ./summarization/data/java

Then, to fine-tune the CodeT5 model:
```bash
cd summarization
python finetune_t5_gene.py --visible_gpu <GPU> --lang java --max_source_length 256 --max_target_length 64 --log_name=../java.log --do_train --do_eval --do_test
```

to prompt-tune the CodeT5 model:
```bash
cd summarization
python prompt_t5.py --visible_gpu <GPU> --lang java --max_source_length 256 --max_target_length 64 --log_name=../java.log --do_train --do_eval --do_test
```
PLBART model is similar, and the result will be saved in model/test_1.output

The hyper-paremeter setting follows the previous work ["No More Fine-Tuning? An Experimental Evaluation of Prompt Tuning in Code Intelligence"](https://arxiv.org/abs/2207.11680)
and there code can be accessed from here:

https://github.com/adf1178/PT4Code


## Evaluation

To better evaluation the comment generation results, we adopt three BLEU variants and a semantic similarity metric, namely SentenceBert Similarity.

### BLEU

The three BLEU variants is borrowed from the previous work

["On the Evaluation of Neural Code Summarization"](https://arxiv.org/abs/2107.07112) 

and there code can be accessed from here: 

https://github.com/DeepSoftwareAnalytics/CodeSumEvaluation

### SentenceBert Similarity

The similarity metric is borrowed from the previous work  

["Semantic similarity metrics for evaluating source code summarization"](https://dl.acm.org/doi/abs/10.1145/3524610.3527909) 

and there code can be accessed from here:

https://github.com/similarityMetrics/similarityMetrics
