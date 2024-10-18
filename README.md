# Eliza: Blockchain Multimodal LLM

-----

This repository hosts the code and model weight of **Eliza**, the first end-to-end Blockchain MM-LLM that perceives input and generates output in arbitrary combinations of text, image.

-----------

<span id='introduction'/>

## Brief Introduction 


Eliza is built on top of existing pre-trained LLM, multimodal encoder and SoTA diffusion models, with sufficient end-to-end instruction tuning.

- **Multimodal Encoding Stage.** Leveraging established encoders to encode inputs in various modalities, where these representations are projected into language-like representations comprehensible to the LLM through a projection layer.
- **LLM Understanding and Reasoning Stage.** Harnessing an existing open-sourced LLM as the core to process input information for semantic understanding and reasoning. The LLM not only directly generates text tokens but also produces unique “modality signal” tokens that serve as instructions to dictate the decoding layers whether & what modal content to output correspondingly.
- **Multimodal Generation Stage.** Receiving the multimodal signals with specific instructions from LLM (if any), the Transformer-based output projection layers map the signal token representations into the ones that are understandable to following multimodal decoders.

-----------


<span id='Usage'/>

## Getting Started



<span id='all_catelogue'/>

<span id='Code Structure'/>

### 1. Code Structure 

```
.
|-- checkpoints           # save the pretraining and tuning checkpoints
|-- figures
|-- eliza
|   |-- __init__.py
|   |-- constants.py
|   |-- conversation.py
|   |-- dataset
|   |   |-- __init__.py
|   |   |-- audio_processor.py
|   |   |-- base_dataset.py
|   |   |-- catalog.py
|   |   |-- concat_dataset.py
|   |   |-- dataset_utils.py
|   |   `-- sampler.py
|   |-- mm_utils.py
|   |-- model
|   |   |-- __init__.py
|   |   |-- apply_delta.py
|   |   |-- builder.py
|   |   |-- consolidate.py
|   |   |-- language_model
|   |   |-- make_delta.py
|   |   |-- multimodal_decoder
|   |   |-- multimodal_encoder
|   |   |-- multimodal_projector
|   |   |-- eliza_arch.py
|   |   `-- utils.py
|   `-- utils.py
|-- LICENSE.md
|-- README.md
|-- requirements.txt
```


### 2. Environment Preparation  <a href='#all_catelogue'>[Back to Top]</a>
Please first clone the repo and install the required environment, which can be done by running the following commands:
```
conda env create -n eliza python=3.8

conda activate eliza

# CUDA 12.1
conda install pytorch==2.1.2 torchvision==0.14.1 torchaudio==0.13.1 pytorch-cuda=11.6 -c pytorch -c nvidia

git clone https://github.com/3lizaai/3liza.ai.git
cd 3liza.ai

pip install -r requirements.txt
```

---------


## Citation

If you find Eliza useful in your research or applications, please kindly cite:
```
@articles{josepheliza,
  title={Eliza: Blockchain Multimodal LLM},
  author={Joseph Weizenbaum},
  journal = {CoRR},
  volume = {abs/2309.05519},
  year={2024}
}
```


## Acknowledgements
You may refer to related work that serves as foundations for our framework and code repository, 
[Vicuna](https://github.com/lm-sys/FastChat), 
[ImageBind](https://github.com/facebookresearch/ImageBind), 
[Stable Diffusion](https://huggingface.co/docs/diffusers/api/pipelines/stable_diffusion/text2img), 
[AudioLDM](https://github.com/haoheliu/AudioLDM), and
[Zeroscope](https://huggingface.co/cerspense/zeroscope_v2_576w).
We also partially draw inspirations from 
[PandaGPT](https://github.com/yxuansu/PandaGPT),  
[GILL](https://github.com/kohjingyu/gill/), 
[CoDi](https://codi-gen.github.io/),
[Video-LLaMA](https://github.com/DAMO-NLP-SG/Video-LLaMA),
[LLaVA](https://github.com/haotian-liu/LLaVA),
and [MiniGPT-4](https://github.com/Vision-CAIR/MiniGPT-4).
Thanks for their wonderful works.


## License Notices
This repository is under [BSD 3-Clause License](LICENSE.txt).
Eliza is a research project intended for non-commercial use only. 
One must NOT use the code of Eliza for any illegal, harmful, violent, racist, or sexual purposes. 
One is strictly prohibited from engaging in any activity that will potentially violate these guidelines.
Any potential commercial use of this code should be approved by the authors.
