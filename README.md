# KoLLaVA
KoLLaVA: Korean Large Language-and-Vision Assistant (feat.[LLaVA](https://github.com/haotian-liu/LLaVA/blob/main/README.md))

## To-do
 [ ] Finetuning 데이터셋 한국어 번역
 [ ] Pretraining 데이터셋 한국어 번역
 [ ] LLaVA 모델에서 Vicuna -> KoVicuna 대체 후 학습 (CLIP -> KoCLIP은 추후 결정)
 [ ] KoLLaVA의 linear layer를 Q-former로 업데이트([InstructBLIP](https://arxiv.org/abs/2305.06500))
 
## Data Download

| Data file name | Size |
| --- | ---: |
| [llava_instruct_150k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/llava_instruct_150k.json) | 229 MB |
| [llava_instruct_80k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/llava_instruct_80k.json) | 229 MB |
| [conversation_58k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/conversation_58k.json) | 126 MB |
| [detail_23k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/detail_23k.json) | 20.5 MB |
| [complex_reasoning_77k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/complex_reasoning_77k.json) | 79.6 MB |

To download our langauge-image multimodal instruction-folllowing dataset [`LLaVA-Instruct-150K`](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K), please run the following script:
```bash
sh download_data.sh
```

### Pretraining Dataset
The pretraining dataset used in this release is a subset of CC-3M dataset, filtered with a more balanced concept coverage distribution.  Please see [here](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K) for a detailed description on the dataset structure and how to download the images.

If you already have CC-3M dataset on your disk, the image names follow this format: `GCC_train_000000000.jpg`.  You may edit the `image` field correspondingly if necessary.

| Data | Chat File | Meta Data | Size |
| --- |  --- |  --- | ---: |
| CC-3M Concept-balanced 595K | [chat.json](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K/raw/main/chat.json) | [metadata.json](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K/raw/main/metadata.json) | 211 MB
| LAION/CC/SBU BLIP-Caption Concept-balanced 558K | [blip_laion_cc_sbu_558k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Pretrain/raw/main/blip_laion_cc_sbu_558k.json) | [metadata.json](#) | 181 MB

**Important notice**: Upon the request from the community, as ~15% images of the original CC-3M dataset are no longer accessible, we upload [`images.zip`](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K/blob/main/images.zip) for better reproducing our work in research community. It must not be used for any other purposes. The use of these images must comply with the CC-3M license. This may be taken down at any time when requested by the original CC-3M dataset owner or owners of the referenced images.



---

## 🌋 LLaVA: Large Language and Vision Assistant

*Visual instruction tuning towards large language and vision models with GPT-4 level capabilities.*

[[Project Page](https://llava-vl.github.io/)] [[Paper](https://arxiv.org/abs/2304.08485)] [[Demo](https://llava.hliu.cc/)]  [[Data](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K)] [[Model](https://huggingface.co/liuhaotian/LLaVA-13b-delta-v0)]

**Visual Instruction Tuning** <br>
[Haotian Liu*](https://hliu.cc), [Chunyuan Li*](https://chunyuan.li/), [Qingyang Wu](https://scholar.google.ca/citations?user=HDiw-TsAAAAJ&hl=en/), [Yong Jae Lee](https://pages.cs.wisc.edu/~yongjaelee/) (*Equal Contribution)

<a href="https://llava.hliu.cc/"><img src="assets/demo.gif" width="70%"></a>

[![Code License](https://img.shields.io/badge/Code%20License-Apache_2.0-green.svg)](https://github.com/tatsu-lab/stanford_alpaca/blob/main/LICENSE)
[![Data License](https://img.shields.io/badge/Data%20License-CC%20By%20NC%204.0-red.svg)](https://github.com/tatsu-lab/stanford_alpaca/blob/main/DATA_LICENSE)
**Usage and License Notices**: The data, code and checkpoint is intended and licensed for research use only. They are also restricted to uses that follow the license agreement of LLaMA, Vicuna and GPT-4. The dataset is CC BY NC 4.0 (allowing only non-commercial use) and models trained using the dataset should not be used outside of research purposes.


## Contents
- [Data Download](#data-download)
- [Install](#install)
- [LLaVA Weights](#llava-weights)
- [Serving](#serving)
- [Evaluation](#evaluation)
- [Fine-tuning](#fine-tuning)

## Data Download

| Data file name | Size |
| --- | ---: |
| [llava_instruct_150k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/llava_instruct_150k.json) | 229 MB |
| [llava_instruct_80k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/llava_instruct_80k.json) | 229 MB |
| [conversation_58k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/conversation_58k.json) | 126 MB |
| [detail_23k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/detail_23k.json) | 20.5 MB |
| [complex_reasoning_77k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K/raw/main/complex_reasoning_77k.json) | 79.6 MB |

To download our langauge-image multimodal instruction-folllowing dataset [`LLaVA-Instruct-150K`](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K), please run the following script:
```bash
sh download_data.sh
```

### Pretraining Dataset
The pretraining dataset used in this release is a subset of CC-3M dataset, filtered with a more balanced concept coverage distribution.  Please see [here](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K) for a detailed description on the dataset structure and how to download the images.

If you already have CC-3M dataset on your disk, the image names follow this format: `GCC_train_000000000.jpg`.  You may edit the `image` field correspondingly if necessary.

| Data | Chat File | Meta Data | Size |
| --- |  --- |  --- | ---: |
| CC-3M Concept-balanced 595K | [chat.json](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K/raw/main/chat.json) | [metadata.json](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K/raw/main/metadata.json) | 211 MB
| LAION/CC/SBU BLIP-Caption Concept-balanced 558K | [blip_laion_cc_sbu_558k.json](https://huggingface.co/datasets/liuhaotian/LLaVA-Pretrain/raw/main/blip_laion_cc_sbu_558k.json) | [metadata.json](#) | 181 MB

**Important notice**: Upon the request from the community, as ~15% images of the original CC-3M dataset are no longer accessible, we upload [`images.zip`](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K/blob/main/images.zip) for better reproducing our work in research community. It must not be used for any other purposes. The use of these images must comply with the CC-3M license. This may be taken down at any time when requested by the original CC-3M dataset owner or owners of the referenced images.

### GPT-4 Prompts

We provide our prompts and few-shot samples for GPT-4 queries, to better facilitate research in this domain.  Please check out the [`prompts`](playground/data/prompts) folder for three kinds of questions: conversation, detail description, and complex reasoning.

They are organized in a format of `system_message.txt` for system message, pairs of `abc_caps.txt` for few-shot sample user input, and `abc_conv.txt` for few-shot sample reference output.

Note that you may find them in different format. For example, `conversation` is in `jsonl`, and detail description is answer-only.  The selected format in our preliminary experiments work slightly better than a limited set of alternatives that we tried: `jsonl`, more natural format, answer-only.  If interested, you may try other variants or conduct more careful study in this.  Contributions are welcomed!

## Install

1. Clone this repository and navigate to LLaVA folder
```bash
git clone https://github.com/haotian-liu/LLaVA.git
cd LLaVA
```

2. Install Package
```Shell
conda create -n llava python=3.10 -y
conda activate llava
pip install --upgrade pip  # enable PEP 660 support
pip install -e .
```

**NOTE**:
[Update 4/30/23] We have successfully moved LLaVA framework to this repo, without the need of a special `transformers` modified by us.  If you install our repo before `4/30/23`, please reinstall `transformers` following the instructions [here](#upgrade-to-v01).

3. Install additional packages for training cases
```
pip install ninja
pip install flash-attn==1.0.2
```

### Upgrade to v0.1

**NOTE**:
If you install our package before 4/30/23, please make sure to execute the command below to correctly upgrade to v0.1.  You may try a [clean install](#install) as well.

```Shell
git pull
pip uninstall transformers
pip install git+https://github.com/huggingface/transformers@cae78c46
pip install -e .
```

## LLaVA Weights
We release [LLaVA](https://llava-vl.github.io/) weights as delta weights to comply with the LLaMA model license.
You can add our delta to the original LLaMA weights to obtain the LLaVA weights.

Instructions:

1. Get the original LLaMA weights in the huggingface format by following the instructions [here](https://huggingface.co/docs/transformers/main/model_doc/llama).
2. Use the following scripts to get LLaVA weights by applying our delta ([13b-v0](https://huggingface.co/liuhaotian/LLaVA-13b-delta-v0), [7b-v0](https://huggingface.co/liuhaotian/LLaVA-7b-delta-v0), [lightning-7B-v1-1](https://huggingface.co/liuhaotian/LLaVA-Lightning-7B-delta-v1-1)). It will automatically download delta weights from our Hugging Face account.

### LLaVA-13B
This conversion command needs around 60 GB of CPU RAM.
```bash
python3 -m llava.model.apply_delta \
    --base /path/to/llama-13b \
    --target /output/path/to/LLaVA-13B-v0 \
    --delta liuhaotian/LLaVA-13b-delta-v0
```

### LLaVA-7B
This conversion command needs around 30 GB of CPU RAM.
```bash
python3 -m llava.model.apply_delta \
    --base /path/to/llama-7b \
    --target /output/path/to/LLaVA-7B-v0 \
    --delta liuhaotian/LLaVA-7b-delta-v0
```


### LLaVA pretrained projector weights
The initial release is pretrained on [LLaVA-filtered CC3M 595K](https://huggingface.co/datasets/liuhaotian/LLaVA-CC3M-Pretrain-595K) with 1 epoch.  The pretrained weights are released [here](https://huggingface.co/liuhaotian/LLaVA-13b-pretrain-projector-v0).

You may perform instruction tuning on our pretrained checkpoints, by using our [visual instruction tuning](https://huggingface.co/datasets/liuhaotian/LLaVA-Instruct-150K) data following the instructions [here](https://github.com/haotian-liu/LLaVA#fine-tuning-with-local-gpus).

## Serving

### Web UI

#### Launch a controller
```Shell
python -m llava.serve.controller --host 0.0.0.0 --port 10000
```

#### Launch a model worker
```Shell
python -m llava.serve.model_worker --host 0.0.0.0 --controller http://localhost:10000 --port 40000 --worker http://localhost:40000 --model-path ./checkpoints/LLaVA-13B-v0 --multi-modal
```
Wait until the process finishes loading the model and you see "Uvicorn running on ...".

#### Launch a model worker (Multiple GPUs, when GPU VRAM <= 24GB)

If your the VRAM of your GPU is less than 24GB (e.g., RTX 3090, RTX 4090, etc.), you may try running it with multiple GPUs.

```Shell
python -m llava.serve.model_worker --host 0.0.0.0 --controller http://localhost:10000 --port 40000 --worker http://localhost:40000 --model-path ./checkpoints/LLaVA-13B-v0 --multi-modal --num-gpus 2
```
Wait until the process finishes loading the model and you see "Uvicorn running on ...".

#### Launch a gradio web server.
```Shell
python -m llava.serve.gradio_web_server --controller http://localhost:10000
```
#### You can open your browser and chat with a model now.

### CLI Inference

A starting script for inference with LLaVA without the need of Gradio interface. The current implementation only supports for a single-turn Q-A session, and the interactive CLI is WIP.  This also serves as an example for users to build customized inference scripts.

```Shell
python -m llava.eval.run_llava \
    --model-name /path/to/LLaVA-13B-v0 \
    --image-file "https://llava-vl.github.io/static/images/view.jpg" \
    --query "What are the things I should be cautious about when I visit here?"
```

Example output (varies in different runs):

> When visiting this picturesque location with a serene lake and a wooden pier extending over the water, one should be cautious about various safety aspects. Some important considerations include:
> 
> 1. Ensuring that the pier is structurally sound andstable, as old or weakened pier structures might not support the weight of visitors.
> 2. Being aware of the water depth around the pier and lake, as sudden drop-offs or strong currents may pose a risk to swimmers, boaters, or those who venture too close to the edge.
> 3. Staying vigilant about the presence of wildlife in the area, such as slippery, stealthy fish or other animals that might cause harm or inconvenience.
> 4. Maintaining a safe distance from the water's edge, particularly for children, elderly individuals, or those who are not strong swimmers.
> 5. Following any posted signs or guidelines related to safety and the use of the pier and surrounding areas.
> 
> By considering these safety precautions, visitors can enjoy the natural beauty of the location while minimizing risks and ensuring a safe and pleasant experience.


## Evaluation

### GPT-assisted Evaluation

Our GPT-assisted evaluation pipeline for multimodal modeling is provided for a comprehensive understanding of the capabilities of vision-language models.  Please see our paper for more details.

1. Generate LLaVA responses

```Shell
python model_vqa.py \
    --model-name ./checkpoints/LLaVA-13B-v0 \
    --question-file \
    playground/data/coco2014_val_qa_eval/qa90_questions.jsonl \
    --image-folder \
    /path/to/coco2014_val \
    --answers-file \
    /path/to/answer-file.jsonl
```

2. Evaluate the generated responses.  In our case, [`answer-file-1.jsonl`](./playground/data/coco2014_val_qa_eval/qa90_gpt4_answer.jsonl) is the response generated by text-only GPT-4 (0314), with the context captions/boxes provided.

```Shell
OPENAI_API_KEY="sk-***********************************" python eval_gpt_review_visual.py \
    --question playground/data/coco2014_val_qa_eval/qa90_questions.jsonl \
    --context table/caps_boxes_coco2014_val_80.jsonl \
    --answer-list \
    /path/to/answer-file-1.jsonl \
    /path/to/answer-file-2.jsonl \
    --rule table/rule.json \
    --output /path/to/review.json
```

3. Summarize the evaluation results

```Shell
python summarize_gpt_review.py
```

### ScienceQA

#### Prepare Data
1. Please see ScienceQA [repo](https://github.com/lupantech/ScienceQA) for setting up the dataset.
2. Generate ScienceQA dataset for LLaVA conversation-style format.

```Shell
python scripts/convert_sqa_to_llava \
    convert_to_llava \
    --base-dir /path/to/ScienceQA/data/scienceqa \
    --split {train,val,minival,test,minitest}
```

#### Evaluation

1. Download our pretrained LLaVA-13B (delta) weights for ScienceQA dataset [here](https://huggingface.co/liuhaotian/LLaVA-13b-delta-v0-science_qa).  Convert the delta weights to actual weights.

```Shell
python -m llava.model.apply_delta \
    --base /path/to/llama-13b \
    --target /path/to/LLaVA-13b-v0-science_qa \
    --delta liuhaotian/LLaVA-13b-delta-v0-science_qa
```

2. [Option 1] Multiple-GPU inference
You may evaluate this with multiple GPUs, and concatenate the generated jsonl files.  Please refer to our script for [batch evaluation](scripts/sqa_eval_batch.sh) and [results gathering](scripts/sqa_eval_gather.sh).

3. [Option 2] Single-GPU inference

(a) Generate LLaVA responses on ScienceQA dataset

```Shell
python -m llava.eval.model_vqa_science \
    --model-name /path/to/LLaVA-13b-v0-science_qa \
    --question-file /path/to/ScienceQA/data/scienceqa/llava_test.json \
    --image-folder /path/to/ScienceQA/data/scienceqa/images/test \
    --answers-file vqa/results/ScienceQA/test_llava-13b.jsonl \
    --answer-prompter
    --conv-mode simple
```

(b) Evaluate the generated responses

```Shell
python eval_science_qa.py \
    --base-dir /path/to/ScienceQA/data/scienceqa \
    --result-file vqa/results/ScienceQA/test_llava-13b.jsonl \
    --output-file vqa/results/ScienceQA/test_llava-13b_output.json \
    --output-result vqa/results/ScienceQA/test_llava-13b_result.json \
```

For reference, we attach our prediction file `test_llava-13b_result.json` [here](llava/eval/table/results/test_sqa_llava_13b_v0.json) for comparison when reproducing our results, as well as for further analysis in detail.

## Fine-tuning
### Data

The current version of LLaVA is fine-tuned from a Vicuna-13B model.  We use approximately 600K filtered CC3M in feature alignment pretraining and 150K GPT-generated multimodal instruction-following data in finetuning. For detailed description of the data generation pipeline, please refer see our [paper](https://arxiv.org/abs/2304.08485).

We are working on a more capable model that is pretrained with the data at a larger scale.  Stay tuned!

We release all three types of multimodal instruction-following data.  The use of these data is subject to OpenAI [TOS](https://openai.com/policies/terms-of-use).

### Code and Hyperparameters
We fine-tune the model using the code from [FastChat](https://github.com/lm-sys/FastChat). We use a similar set of hyperparameters as Vicuna in finetuning.  Both hyperparameters used in pretraining and finetuning are provided below.

1. Pretraining

| Hyperparameter | Global Batch Size | Learning rate | Epochs | Max length | Weight decay |
| --- | ---: | ---: | ---: | ---: | ---: |
| LLaVA-13B | 128 | 2e-3 | 1 | 2048 | 0 |

2. Finetuning

| Hyperparameter | Global Batch Size | Learning rate | Epochs | Max length | Weight decay |
| --- | ---: | ---: | ---: | ---: | ---: |
| LLaVA-13B | 32 | 2e-5 | 3 | 2048 | 0 |

### Fine-tuning with Local GPUs
LLaVA is trained on 8 A100 GPUs with 80GB memory with the following code. To train on fewer GPUs, you can reduce the `per_device_train_batch_size` and increase the `gradient_accumulation_steps` accordingly to keep the global batch size the same.

1. Pretraining

<details>
<summary>Pretrain: LLaVA-13B, 8x A100 (80G).  Time: ~4 hours.</summary>

```Shell
torchrun --nnodes=1 --nproc_per_node=8 --master_port=25001 \
    llava/train/train_mem.py \
    --model_name_or_path ./checkpoints/llama-vicuna-13b \
    --data_path /path/to/cc3m_595k.json \
    --image_folder /path/to/cc3m_595k \
    --vision_tower openai/clip-vit-large-patch14 \
    --tune_mm_mlp_adapter True \
    --mm_vision_select_layer -2 \
    --mm_use_im_start_end \
    --bf16 True \
    --output_dir ./checkpoints/llava-13b-pretrain \
    --num_train_epochs 1 \
    --per_device_train_batch_size 16 \
    --per_device_eval_batch_size 4 \
    --gradient_accumulation_steps 1 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 2400 \
    --save_total_limit 1 \
    --learning_rate 2e-3 \
    --weight_decay 0. \
    --warmup_ratio 0.03 \
    --lr_scheduler_type "cosine" \
    --logging_steps 1 \
    --tf32 True \
    --model_max_length 2048 \
    --gradient_checkpointing True \
    --lazy_preprocess True \
    --report_to wandb
```
</details>

You may run this with a single A100 GPU with the following code.  Please note that the `per_device_train_batch_size` * `gradient_accumulation_steps` should be equal to 128 to keep the global batch size the same.

<details>
<summary>Pretrain: LLaVA-13B, 1x A100 (80G).  Time: ~33 hours.</summary>

```Shell
python llava/train/train_mem.py \
    --model_name_or_path ./checkpoints/llama-vicuna-13b \
    --data_path /path/to/cc3m_595k.json \
    --image_folder /path/to/cc3m_595k \
    --vision_tower openai/clip-vit-large-patch14 \
    --tune_mm_mlp_adapter True \
    --mm_vision_select_layer -2 \
    --mm_use_im_start_end \
    --bf16 True \
    --output_dir ./checkpoints/llava-13b-pretrain \
    --num_train_epochs 1 \
    --per_device_train_batch_size 16 \
    --per_device_eval_batch_size 4 \
    --gradient_accumulation_steps 8 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 2400 \
    --save_total_limit 1 \
    --learning_rate 2e-3 \
    --weight_decay 0. \
    --warmup_ratio 0.03 \
    --lr_scheduler_type "cosine" \
    --logging_steps 1 \
    --tf32 True \
    --model_max_length 2048 \
    --gradient_checkpointing True \
    --lazy_preprocess True \
    --report_to wandb
```
</details>

<details>
<summary>Pretrain: LLaVA-7B, 1x A100 (80G/40G).  Time: ~19 hours.</summary>

```Shell
python llava/train/train_mem.py \
    --model_name_or_path ./checkpoints/llama-vicuna-7b \
    --data_path /path/to/cc3m_595k.json \
    --image_folder /path/to/cc3m_595k \
    --vision_tower openai/clip-vit-large-patch14 \
    --tune_mm_mlp_adapter True \
    --mm_vision_select_layer -2 \
    --mm_use_im_start_end \
    --bf16 True \
    --output_dir ./checkpoints/llava-7b-pretrain \
    --num_train_epochs 1 \
    --per_device_train_batch_size 16 \
    --per_device_eval_batch_size 4 \
    --gradient_accumulation_steps 8 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 2400 \
    --save_total_limit 1 \
    --learning_rate 2e-3 \
    --weight_decay 0. \
    --warmup_ratio 0.03 \
    --lr_scheduler_type "cosine" \
    --logging_steps 1 \
    --tf32 True \
    --model_max_length 2048 \
    --gradient_checkpointing True \
    --lazy_preprocess True \
    --report_to wandb
```
</details>


#### Experimental: use FSDP to save memory in pretraining

<details>
<summary>Learn more</summary>

Currently, PyTorch and Huggingface does not yet have stable/native support for FSDP on parameter efficient tuning (part of the parameters are frozen).  However, the feature is being developed in PyTorch nightly and shall be shipped in the next release.  We provide an experimental script to enable FSDP in pretraining.  To use it, please **create a new enviroment** (to be safe), install PyTorch nightly (**MUST**), and `LLaVA` package following the instructions below.

1. Prepare environment
```Shell
conda create -n llava_beta python=3.10 -y
conda activate llava_beta
pip install --upgrade pip
pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu117
pip install -e .
pip install einops ninja
pip install flash-attn
```

2. Run pretraining with FSDP (experimental)
```Shell
torchrun --nnodes=1 --nproc_per_node=8 --master_port=25001 \
    llava/train/train_mem.py \
    --model_name_or_path ./checkpoints/llama-vicuna-13b \
    --data_path /path/to/cc3m_595k.json \
    --image_folder /path/to/cc3m_595k \
    --vision_tower openai/clip-vit-large-patch14 \
    --tune_mm_mlp_adapter True \
    --mm_vision_select_layer -2 \
    --mm_use_im_start_end \
    --bf16 True \
    --output_dir ./checkpoints/llava-13b-pretrain_fsdp \
    --num_train_epochs 1 \
    --per_device_train_batch_size 16 \
    --per_device_eval_batch_size 4 \
    --gradient_accumulation_steps 1 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 2400 \
    --save_total_limit 1 \
    --learning_rate 2e-3 \
    --weight_decay 0. \
    --warmup_ratio 0.03 \
    --lr_scheduler_type "cosine" \
    --logging_steps 1 \
    --tf32 True \
    --fsdp "full_shard auto_wrap" \
    --fsdp_transformer_layer_cls_to_wrap 'LlamaDecoderLayer' \
    --model_max_length 2048 \
    --gradient_checkpointing True \
    --lazy_preprocess True \
    --report_to wandb
```
</details>

2. Extract projector features
```Shell
python scripts/extract_mm_projector.py \
  --model_name_or_path ./checkpoints/llava-13b-pretrain \
  --output ./checkpoints/mm_projector/llava-13b-pretrain.bin
```

3. Finetuning

```Shell
torchrun --nnodes=1 --nproc_per_node=8 --master_port=25001 \
    llava/train/train_mem.py \
    --model_name_or_path /path/to/llama-vicuna-13b \
    --data_path /path/to/llava_instruct_150k.json \
    --image_folder /Data/haotian/coco/train2014 \
    --vision_tower openai/clip-vit-large-patch14 \
    --pretrain_mm_mlp_adapter ./checkpoints/mm_projector/llava-13b-pretrain.bin \
    --mm_vision_select_layer -2 \
    --mm_use_im_start_end True \
    --bf16 True \
    --output_dir ./checkpoints \
    --num_train_epochs 3 \
    --per_device_train_batch_size 4 \
    --per_device_eval_batch_size 4 \
    --gradient_accumulation_steps 1 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 5000 \
    --save_total_limit 3 \
    --learning_rate 2e-5 \
    --weight_decay 0. \
    --warmup_ratio 0.03 \
    --lr_scheduler_type "cosine" \
    --logging_steps 1 \
    --tf32 True \
    --fsdp "full_shard auto_wrap" \
    --fsdp_transformer_layer_cls_to_wrap 'LlamaDecoderLayer' \
    --model_max_length 2048 \
    --gradient_checkpointing True \
    --lazy_preprocess True \
    --report_to wandb
```

### Train LLaVA Lightning
LLaVA-Lightning can be trained on 8x A100 GPUs in just 3 hours, including both pretraining and finetuning. When using spot instances, it costs just ~$40. *We are working on [SkyPilot](https://github.com/skypilot-org/skypilot.git) tutorial to make spot instance training even easier, stay tuned!*

Please make sure to: (1) [install](#install) or [upgrade](#upgrade-to-v01) to the latest code base, and (2) pass the correct model version identifier `v0`/`v1` to ensure the correct conversation template is loaded.

```Shell
bash ./scripts/train_lightning.sh {v0,v1}
```

#### Hyperparameters

1. Pretraining

| Hyperparameter | Global Batch Size | Learning rate | Epochs | Max length | Weight decay |
| --- | ---: | ---: | ---: | ---: | ---: |
| LLaVA-Lightning-7B | 128 | 2e-3 | 1 | 2048 | 0 |

2. Finetuning

| Hyperparameter | Global Batch Size | Learning rate | Epochs | Max length | Weight decay |
| --- | ---: | ---: | ---: | ---: | ---: |
| LLaVA-Lightning-7B | 128 | 2e-5 | 1 | 2048 | 0 |

#### LLaVA-MPT-7b
Thanks to LLaVA-Lightning, we are able to train a checkpoint based on MPT-7b-Chat on 8x A100 GPUs in just 3 hours, including both pretraining and finetuning.

**NOTE**: This is a research preview of the LLaVA-Lightning based on MPT-7B-chat checkpoint. The usage of the model should comply with MPT-7B-chat license and agreements.

**NOTE**: Unlike other LLaVA models, this model should be used directly without delta weights conversion!

**NOTE**: You need to upgrade to our latest code base to use LLaVA-MPT-7b!

1. Usage

You do not need to download our checkpoint, it will directly load from our Hugging Face model: [`liuhaotian/LLaVA-Lightning-MPT-7B-preview`](https://huggingface.co/liuhaotian/LLaVA-Lightning-MPT-7B-preview).

```Shell
python -m llava.serve.controller --host 0.0.0.0 --port 10000
python -m llava.serve.model_worker --host 0.0.0.0 --controller http://localhost:10000 --port 40000 --worker http://localhost:40000 --model-path liuhaotian/LLaVA-Lightning-MPT-7B-preview
python -m llava.serve.gradio_web_server --controller http://localhost:10000
```

2. Training

We use the same set of training dataset, and the hyperparameters as other Lightning checkpoints.

```Shell
bash ./scripts/train_lightning_mpt.sh
```

### Fine-tuning on ScienceQA
**NOTE**: Due to that ScienceQA experiments were done earlier, the current checkpoints are trained *without* `<im_start>` and `<im_end>` tokens.  Checkpoints with these tokens will be updated later.  Here we provide our training scripts for the current checkpoints.

<details>
<summary>1. Pretraining</summary>

```Shell
torchrun --nnodes=1 --nproc_per_node=8 --master_port=25001 \
    llava/train/train_mem.py \
    --model_name_or_path ./checkpoints/llama-vicuna-13b \
    --data_path /path/to/cc3m_595k.json \
    --image_folder /path/to/cc3m_595k \
    --vision_tower openai/clip-vit-large-patch14 \
    --tune_mm_mlp_adapter True \
    --mm_vision_select_layer -2 \
    --bf16 True \
    --output_dir ./checkpoints/llava-13b-pretrain-no_im_start_end_token \
    --num_train_epochs 1 \
    --per_device_train_batch_size 16 \
    --per_device_eval_batch_size 4 \
    --gradient_accumulation_steps 1 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 2400 \
    --save_total_limit 1 \
    --learning_rate 2e-3 \
    --weight_decay 0. \
    --warmup_ratio 0.03 \
    --lr_scheduler_type "cosine" \
    --logging_steps 1 \
    --tf32 True \
    --model_max_length 2048 \
    --gradient_checkpointing True \
    --lazy_preprocess True \
    --report_to wandb
```
</details>

<details>
<summary>2. Extract projector features</summary>

```Shell
python scripts/extract_mm_projector.py \
  --model_name_or_path ./checkpoints/llava-13b-pretrain-no_im_start_end_token \
  --output ./checkpoints/mm_projector/llava-13b-pretrain-no_im_start_end_token.bin
```
</details>

<details>
<summary>3. Finetuning</summary>

You may download our pretrained `llava-13b-pretrain-no_im_start_end_token.bin` [here](https://huggingface.co/liuhaotian/LLaVA-13b-pretrain-projector-v0/blob/main/LLaVA-13b-pretrain-projector-v0-CC3M-595K-original_caption-no_im_token.bin).

```Shell
torchrun --nnodes=1 --nproc_per_node=8 --master_port=25001 \
    llava/train/train_mem.py \
    --model_name_or_path /path/to/llama-vicuna-13b \
    --data_path /path/to/scienceqa/llava_train_QCM-LEPA.json \
    --image_folder /path/to/scienceqa/images/train \
    --vision_tower openai/clip-vit-large-patch14 \
    --pretrain_mm_mlp_adapter ./checkpoints/mm_projector/llava-13b-pretrain-no_im_start_end_token.bin \
    --mm_vision_select_layer -2 \
    --bf16 True \
    --output_dir ./checkpoints/llava-13b-pretrain-no_im_start_end_token-finetune_scienceqa \
    --num_train_epochs 12 \
    --per_device_train_batch_size 4 \
    --per_device_eval_batch_size 4 \
    --gradient_accumulation_steps 1 \
    --evaluation_strategy "no" \
    --save_strategy "steps" \
    --save_steps 5000 \
    --save_total_limit 3 \
    --learning_rate 2e-5 \
    --weight_decay 0. \
    --warmup_ratio 0.03 \
    --lr_scheduler_type "cosine" \
    --logging_steps 1 \
    --tf32 True \
    --fsdp "full_shard auto_wrap" \
    --fsdp_transformer_layer_cls_to_wrap 'LlamaDecoderLayer' \
    --model_max_length 2048 \
    --gradient_checkpointing True \
    --lazy_preprocess True \
    --report_to wandb
```
</details>

## Acknowledgement

- [Vicuna](https://github.com/lm-sys/FastChat): the codebase we built upon, and our base model Vicuna-13B that has the amazing language capabilities!


If you find LLaVA useful for your your research and applications, please cite using this BibTeX:
```bibtex
@misc{liu2023llava,
      title={Visual Instruction Tuning}, 
      author={Liu, Haotian and Li, Chunyuan and Wu, Qingyang and Lee, Yong Jae},
      publisher={arXiv:2304.08485},
      year={2023},
}
```

## Related Projects

- [Instruction Tuning with GPT-4](https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM)

For future project ideas, pleae check out:
- [SEEM: Segment Everything Everywhere All at Once](https://github.com/UX-Decoder/Segment-Everything-Everywhere-All-At-Once)
- [Grounded-Segment-Anything](https://github.com/IDEA-Research/Grounded-Segment-Anything) to detect, segment, and generate anything by marrying [Grounding DINO](https://github.com/IDEA-Research/GroundingDINO) and [Segment-Anything](https://github.com/facebookresearch/segment-anything).
