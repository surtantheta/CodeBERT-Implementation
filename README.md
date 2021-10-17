# CodeBERT-Implementation
In this repo we have replicated the paper <b><a href = "https://arxiv.org/abs/2002.08155">CodeBERT: A Pre-Trained Model for Programming and Natural Languages</a></b>. </br>
We are interested in evaluating CodeBERT specifically in Natural language code search. Given a natural language as the input, the objective of code search is to find the most semantically related code from a collection of codes. 

This code was implemented on a 64-bit Windows system with 8 GB ram and GeForce GTX 1650 4GB graphics card.

Due to limited compuational power, we have trained and evaluated the model on a smaller data compared to the original data. 
<table>
  <tr>
    <th rowspan ="2"> Language </th>
    <th colspan="2">Training data size</th>
    <th colspan="2">Validation data size</th>
    <th colspan="2">Test data size for batch_0</th>
  </tr>
  <tr>
    <td>Original</td>
    <td>Our</td>
    <td>Original</td>
    <td>Our</td>
    <td>Original</td>
    <td>Our</td>
  </tr>
  <tr>
    <td>Ruby</td>
    <td>97580</td>
    <td>500</td>
    <td>4417</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>Go</td>
    <td>635653</td>
    <td>500</td>
    <td>28483</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>PHP</td>
    <td>1047404</td>
    <td>500</td>
    <td>52029</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>Python</td>
    <td>824342</td>
    <td>500</td>
    <td>46213</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>Java</td>
    <td>908886</td>
    <td>500</td>
    <td>30655</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  <tr>
    <td>Javascript</td>
    <td>247773</td>
    <td>500</td>
    <td>16505</td>
    <td>100</td>
    <td>1000000</td>
    <td>20000</td>
  </tr>
  
  
  </table>
  
Compared to the code in original <a href = "https://github.com/microsoft/CodeBERT/tree/master/CodeBERT/codesearch">repo</a>, code in this repo can be implemented directly in Windows system without any hindrance. We have already provided a subset of pre-processed data for batch_0 (shown in table under Testing data size) in ```./data/codesearch/test/```
## Fine tuning pretrained model CodeBERT on individual languages
```
lang = go
cd CodeBERT-Implementation
! python run_classifier.py --model_type roberta --task_name codesearch --do_train --do_eval --eval_all_checkpoints --train_file train_short.txt --dev_file valid_short.txt --max_seq_length 50 --per_gpu_train_batch_size 8 --per_gpu_eval_batch_size 8 --learning_rate 1e-5 --num_train_epochs 1 --gradient_accumulation_steps 1 --overwrite_output_dir --data_dir CodeBERT-Implementation/data/codesearch/train_valid/$lang/ --output_dir ./models/$lang/ --model_name_or_path microsoft/codebert-base
```
## Inference and Evaluation
```
lang = go
idx = 0
! python run_classifier.py --model_type roberta --model_name_or_path microsoft/codebert-base --task_name codesearch --do_predict --output_dir CodeBERT-Implementation/data/models/$lang --data_dir CodeBERT-Implementation/data/codesearch/test/$lang/ --max_seq_length 50 --per_gpu_train_batch_size 8 --per_gpu_eval_batch_size 8 --learning_rate 1e-5 --num_train_epochs 1 --test_file batch_short_${idx}.txt --pred_model_dir ./models/ruby/checkpoint-best/ --test_result_dir ./results/$lang/${idx}_batch_result.txt
```
```
! python mrr.py
```

The Mean Evaluation Rank (MER), the evaluation mteric, for the subset of data is given as follows:

<table>
  <tr>
    <th> Language </th>
    <th> MER </th>
  </tr>
  <tr>
    <td>Ruby</td>
    <td>0.0037</td>
  </tr>
  <tr>
    <td>Go</td>
    <td>0.0034</td>
  </tr>
  <tr>
    <td>PHP</td>
    <td>0.0044</td>
  </tr>
  <tr>
    <td>Python</td>
    <td>0.0052</td>
  </tr>
  <tr>
    <td>Java</td>
    <td>0.0033</td>
  </tr>
  <tr>
    <td>Java script</td>
    <td>0.0054</td>
  </tr>
 </table>
 
The accuracy is way less than what is reported in the paper. However, the purpose of this repo is to provide the user, ready to implement data of CodeBERT without any heavy downloads. We have also included the prediction results in this repo corresponding to the test data.
