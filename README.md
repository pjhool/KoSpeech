# [UPDATED] KoSpeech: Open-Source Toolkit for End-to-End Korean Speech Recognition

[![CodeFactor](https://www.codefactor.io/repository/github/sooftware/kospeech/badge)](https://www.codefactor.io/repository/github/sooftware/kospeech) 
[<img src="http://img.shields.io/badge/docs-passing-success">](https://sooftware.github.io/KoSpeech/) 
[<img src="http://img.shields.io/badge/help wanted-issue 37-ff">](https://github.com/sooftware/KoSpeech/issues/37) 
<img src="https://img.shields.io/github/stars/sooftware/KoSpeech"> 
<img src="https://img.shields.io/github/forks/sooftware/KoSpeech">  
  
### What's New
  
- December 2020: Release v1.1
- December 2020: Update pre-train models
- December 2020: Joint CTC-Attention Updated (*Currently, Not Supports Multi-GPU*)
- November 2020: Deep Speech 2 Architecture Updated
- November 2020: KsponSpeech Subword & Grapheme Unit Updated (*Not Tested*)
- November 2020: RAdam & AdamP Optimizer Updated
  
### Note
  
- Currently, beam search may not work properly.  
- The model's inference is currently not working properly, but will be updated as soon as possible.  
- Transformer model is currently not working properly.
  
### ***[KoSpeech:  Open-Source Toolkit for End-to-End Korean Speech Recognition \[Technical Report\]](https://arxiv.org/abs/2009.03092)***
  
***KoSpeech***, an open-source software, is modular and extensible end-to-end Korean automatic speech recognition (ASR) toolkit based on the deep learning library PyTorch. Several automatic speech recognition open-source toolkits have been released, but all of them deal with non-Korean languages, such as English (e.g. ESPnet, Espresso). Although AI Hub opened 1,000 hours of Korean speech corpus known as KsponSpeech, there is no established preprocessing method and baseline model to compare model performances. Therefore, we propose preprocessing methods for KsponSpeech corpus and a baseline model for benchmarks. Our baseline model is based on Listen, Attend and Spell (LAS) architecture and ables to customize various training hyperparameters conveniently. By KoSpeech, we hope this could be a guideline for those who research Korean speech recognition. Our baseline model achieved **10.31%** character error rate (CER) at KsponSpeech corpus only with the acoustic model.  
  
### [UPDATED] Pre-train Models
  
|Description|Feature|Dataset|Epochs|CER|Model|  
|-----------|:-----:|-------|:----:|:-:|-----|    
|Deep Speech 2|Kaldi-style fbank 80|[KsponSpeech](http://www.aihub.or.kr/aidata/105)|1|42.3|[download](https://drive.google.com/file/d/1MMqZMjEuc5wvFNIxfhCkhn1kG3Z0HaEx/view?usp=sharing)|  
|Listen, Attend and Spell|Kaldi-style fbank 80|[KsponSpeech](http://www.aihub.or.kr/aidata/105)|1|19.2|[download](https://drive.google.com/file/d/17q2qg23ud-Kebsa0Fy4DEpA2Uy6rlT90/view?usp=sharing)|  
|Joint CTC-Attention|Kaldi-style fbank 80|[KsponSpeech](http://www.aihub.or.kr/aidata/105)|10|12.5|[download](https://drive.google.com/file/d/1DDclNR4BInOXvWOJphajkG4jDf8KCa_W/view?usp=sharing)|  
|VAD Model|-|-|-|-|[download](https://drive.google.com/file/d/14lLxfCiFgXqnb1a8dZ_AYhlKQeaMz7Jd/view?usp=sharing)|  
  
※ Training is in progress. As the training progresses, the pre-trained model will be updated.
  
### Pre-processed Transcripts
  
|Dataset    |Authentication|Output-Unit|Transcript|  
|-----------|--------------|-----------|:--------:|  
|KsponSpeech|*Required*    |Character  |[download](https://drive.google.com/file/d/12IAJSTRqkPALx9AX_SKyC4KkFVQN6Lge/view?usp=sharing)|  
|KsponSpeech|*Required*    |Subword    |[download](https://drive.google.com/file/d/1awhfTpqAaDs7K5R9npvFoqeMYWiUtGtq/view?usp=sharing)|  
|KsponSpeech|*Required*    |Grapheme   |[download](https://drive.google.com/file/d/1awhfTpqAaDs7K5R9npvFoqeMYWiUtGtq/view?usp=sharing)|   
|LibriSpeech|*Unrequired*  |Subword    |[download](https://drive.google.com/file/d/1RA29SLtNIo1zmnk0OgVeXNH553Ul_DhY/view?usp=sharing)|  
   
※ Authentication : Refer to [[Link]](https://github.com/sooftware/KoSpeech/issues/54)  
  
## Introduction
  
End-to-end (E2E) automatic speech recognition (ASR) is an emerging paradigm in the field of neural network-based speech recognition that offers multiple benefits. Traditional “hybrid” ASR systems, which are comprised of an acoustic model, language model, and pronunciation model, require separate training of these components, each of which can be complex.   
  
For example, training of an acoustic model is a multi-stage process of model training and time alignment between the speech acoustic feature sequence and output label sequence. In contrast, E2E ASR is a single integrated approach with a much simpler training pipeline with models that operate at low audio frame rates. This reduces the training time, decoding time, and allows joint optimization with downstream processing such as natural language understanding.  
  
## Features  
  
* [End-to-end (E2E) automatic speech recognition](https://sooftware.github.io/KoSpeech/)
* [Various Options](https://sooftware.github.io/KoSpeech/notes/opts.html)
* [(VGG / DeepSpeech2) Extractor](https://sooftware.github.io/KoSpeech/Seq2seq.html#module-kospeech.models.seq2seq.sublayers)
* [MaskCNN & pack_padded_sequence](https://sooftware.github.io/KoSpeech/Seq2seq.html#module-kospeech.models.seq2seq.sublayers)
* [Attention (Multi-Head / Location-Aware / Additive / Scaled-dot)](https://sooftware.github.io/KoSpeech/Seq2seq.html#module-kospeech.models.seq2seq.attention)
* [Top K Decoding (Beam Search)](https://sooftware.github.io/KoSpeech/Seq2seq.html#module-kospeech.models.seq2seq.beam_search)
* [Various Feature (Spectrogram / Mel-Spectrogram / MFCC / Filter-Bank)](https://sooftware.github.io/KoSpeech/Data.html#module-kospeech.data.audio.feature)
* [Delete silence](https://sooftware.github.io/KoSpeech/Data.html#module-kospeech.data.audio.core)
* [SpecAugment / NoiseAugment](https://sooftware.github.io/KoSpeech/Data.html#module-kospeech.data.audio.augment)
* [Label Smoothing](https://sooftware.github.io/KoSpeech/Optim.html#module-kospeech.optim.loss)

* [Save & load Checkpoint](https://sooftware.github.io/KoSpeech/Checkpoint.html#id1)
* [Learning Rate Scheduling](https://sooftware.github.io/KoSpeech/Optim.html#module-kospeech.optim.lr_scheduler)
* [Implement data loader as multi-thread for speed](https://sooftware.github.io/KoSpeech/Data.html#module-kospeech.data.data_loader)
* Scheduled Sampling (Teacher forcing scheduling)
* Inference with batching
* Multi-GPU training
  
We have referred to several papers to develop the best model possible. And tried to make the code as efficient and easy to use as possible. If you have any minor inconvenience, please let us know anytime.   
We will response as soon as possible.

## Roadmap
  
![image](https://user-images.githubusercontent.com/42150335/101985614-8b1f2080-3ccc-11eb-9645-e5217a2dfa53.png)
  
So far, four models are implemented: *Deep Speech 2, Listen Attend and Spell (LAS), Speech Transformer, and Joint CTC-Attention LAS*. To check details of these model architectures, check figures attached to each section.
  
- *Deep Speech 2*  
  
Deep Speech 2 showed faster and more accurate performance on ASR tasks with Connectionist Temporal Classification (CTC) loss. This model has been highlighted for significantly increasing performance compared to the previous end- to-end models.

  
- *Listen, Attend and Spell*
   
We follow the architecture previously proposed in the "Listen, Attend and Spell", but some modifications were added to improve performance. We provide four different attention mechanisms, `scaled dot-product attention`, `additive attention`, `location aware attention`, `multi-head attention`. Attention mechanisms much affect the performance of models. 
  
- *Speech Transformer*  
  
Transformer is a powerful architecture in the Natural Language Processing (NLP) field. This architecture also showed good performance at ASR tasks. In addition, as the research of this model continues in the natural language processing field, this model has high potential for further development.
  
- *Joint CTC-Attention*
  
With the proposed architecture to take advantage of both the CTC-based model and the attention-based model. It is a structure that makes it robust by adding CTC to the encoder.
  
### Various Options   
  
We support various options for training. More details please check [here](https://sooftware.github.io/KoSpeech/notes/opts.html).  
  
* Options
```
usage: main.py [-h] [--mode MODE] [--sample_rate SAMPLE_RATE]
               [--frame_length FRAME_LENGTH] [--frame_shift FRAME_SHIFT]
               [--n_mels N_MELS] [--normalize] [--del_silence]
               [--input_reverse] [--feature_extract_by FEATURE_EXTRACT_BY]
               [--transform_method TRANSFORM_METHOD]
               [--freq_mask_para FREQ_MASK_PARA]
               [--time_mask_num TIME_MASK_NUM] [--freq_mask_num FREQ_MASK_NUM]
               [--architecture ARCHITECTURE] [--use_bidirectional]
               [--mask_conv] [--hidden_dim HIDDEN_DIM] [--dropout DROPOUT]
               [--num_heads NUM_HEADS] [--label_smoothing LABEL_SMOOTHING]
               [--num_encoder_layers NUM_ENCODER_LAYERS]
               [--num_decoder_layers NUM_DECODER_LAYERS] [--rnn_type RNN_TYPE]
               [--extractor EXTRACTOR] [--activation ACTIVATION]
               [--attn_mechanism ATTN_MECHANISM]
               [--teacher_forcing_ratio TEACHER_FORCING_RATIO]
               [--num_classes NUM_CLASSES] [--d_model D_MODEL]
               [--ffnet_style FFNET_STYLE] [--dataset_path DATASET_PATH]
               [--transcripts_path TRANSCRIPTS_PATH]
               [--data_list_path DATA_LIST_PATH] [--spec_augment] [--use_cuda]
               [--batch_size BATCH_SIZE] [--num_workers NUM_WORKERS]
               [--num_epochs NUM_EPOCHS] [--init_lr INIT_LR]
               [--peak_lr PEAK_LR] [--final_lr FINAL_LR]
               [--final_lr_scale FINAL_LR_SCALE]
               [--init_lr_scale INIT_LR_SCALE] [--max_len MAX_LEN]
               [--max_grad_norm MAX_GRAD_NORM] [--weight_decay WEIGHT_DECAY]
               [--reduction REDUCTION] [--warmup_steps WARMUP_STEPS]
               [--teacher_forcing_step TEACHER_FORCING_STEP]
               [--min_teacher_forcing_ratio MIN_TEACHER_FORCING_RATIO]
               [--seed SEED] [--save_result_every SAVE_RESULT_EVERY]
               [--checkpoint_every CHECKPOINT_EVERY]
               [--print_every PRINT_EVERY] [--resume]
```
  
## Installation
This project recommends Python 3.7 or higher.   
We recommend creating a new virtual environment for this project (using virtual env or conda).  

### Prerequisites
  
* Numpy: `pip install numpy` (Refer [here](https://github.com/numpy/numpy) for problem installing Numpy).
* Pytorch: Refer to [PyTorch website](http://pytorch.org/) to install the version w.r.t. your environment.   
* Pandas: `pip install pandas` (Refer [here](https://github.com/pandas-dev/pandas) for problem installing Pandas)  
* Matplotlib: `pip install matplotlib` (Refer [here](https://github.com/matplotlib/matplotlib) for problem installing Matplotlib)
* librosa: `conda install -c conda-forge librosa` (Refer [here](https://github.com/librosa/librosa) for problem installing librosa)
* torchaudio: `pip install torchaudio` (Refer [here](https://github.com/pytorch/pytorch) for problem installing torchaudio)
* tqdm: `pip install tqdm` (Refer [here](https://github.com/tqdm/tqdm) for problem installing tqdm)
* sentencepiece: `pip install sentencepiece` (Refer [here](https://github.com/google/sentencepiece) for problem installing sentencepiece)
  
### Install from source
Currently we only support installation from source code using setuptools. Checkout the source code and run the   
following commands:  
```
pip install -e .
```
  
## Get Started
    
### Preparing KsponSpeech Dataset (LibriSpeech also supports)
  
Download from [here](https://github.com/sooftware/KoSpeech#pre-processed-transcripts) or refer to the following to preprocess.
  
- KsponSpeech : [Check this page](https://github.com/sooftware/KoSpeech/tree/master/dataset/kspon)
- LibriSpeech : [Check this page](https://github.com/sooftware/KoSpeech/tree/master/dataset/libri)
  
### Training KsponSpeech Dataset
  
You can choose from four models and training this. There are many other training options, so look carefully and execute the following command:  
  
- **Deep Speech 2** Training
```
python ./bin/main.py --dataset $DATASET --transcripts_path $TRANSCRIPTS_PATH --output_unit $OUTPUT_UNIT --architecture deepspeech2 --batch_size 32 --num_workers 4 --num_epochs 70 --use_bidirectional --audio_extension pcm --optimizer adam --spec_augment --use_cuda --hidden_dim 1024 --dropout 0.3 --transform_method fbank --num_encoder_layers 3 --rnn_type lstm --sample_rate 16000 --frame_length 20 --frame_shift 10 --n_mels 80 --normalize --del_silence --feature_extract_by kaldi --freq_mask_para 18 --time_mask_num 4 --freq_mask_num 2 --save_result_every 1000 --checkpoint_every 5000 --print_every 10 --init_lr 1e-06 --final_lr 1e-06 --peak_lr 1e-04 --init_lr_scale 0.01 --final_lr_scale 0.05 --mode train --max_grad_norm 400 --warmup_steps 2000 --max_len 400 --weight_decay 1e-05 --activation hardtanh
```
  
- **Listen, Attend and Spell** Training
```
python ./bin/main.py --dataset $DATASET --transcripts_path $TRANSCRIPTS_PATH --output_unit $OUTPUT_UNIT --architecture las --batch_size 32 --num_workers 4 --num_epochs 20 --use_bidirectional --audio_extension pcm --optimizer adam --spec_augment --use_cuda --hidden_dim 512 --dropout 0.3 --num_heads 4 --label_smoothing 0.1 --transform_method fbank --num_encoder_layers 3 --num_decoder_layers 2 --rnn_type lstm --teacher_forcing_ratio 1.0 --sample_rate 16000 --frame_length 20 --frame_shift 10 --n_mels 80 --normalize --del_silence --feature_extract_by kaldi --freq_mask_para 18 --time_mask_num 4 --freq_mask_num 2 --save_result_every 1000 --checkpoint_every 5000 --print_every 10 --init_lr 3e-04 --final_lr 1e-06 --peak_lr 3e-04 --init_lr_scale 0.01 --final_lr_scale 0.05 --mode train --max_grad_norm 400 --warmup_steps 0 --max_len 400 --weight_decay 1e-05 --reduction sum --attn_mechanism multi-head --teacher_forcing_step 0.0 --min_teacher_forcing_ratio 1.0 --extractor vgg --activation hardtanh
```
  
- **Joint CTC-Attention** Training
```
python ./bin/main.py --dataset $DATASET --transcripts_path $TRANSCRIPTS_PATH --output_unit $OUTPUT_UNIT --architecture las --batch_size 32 --num_workers 4 --num_epochs 20 --use_bidirectional --audio_extension pcm --optimizer adam --use_cuda --hidden_dim 768 --dropout 0.3 --num_heads 4 --transform_method fbank --num_encoder_layers 3 --num_decoder_layers 1 --rnn_type lstm --teacher_forcing_ratio 1.0 --sample_rate 16000 --frame_length 20 --frame_shift 10 --n_mels 80 --normalize --del_silence --feature_extract_by kaldi --freq_mask_para 18 --time_mask_num 4 --freq_mask_num 2 --save_result_every 1000 --checkpoint_every 5000 --print_every 10 --init_lr 1e-06 --final_lr 1e-06 --peak_lr 3e-04 --init_lr_scale 0.01 --final_lr_scale 0.05 --mode train --max_grad_norm 400 --warmup_steps 2000 --max_len 400 --weight_decay 1e-05 --reduction mean --attn_mechanism multi-head --teacher_forcing_step 0.1 --min_teacher_forcing_ratio 0.9 --extractor vgg --activation hardtanh --cross_entropy_weight 0.7 --ctc_weight 0.3 --mask_conv --joint_ctc_attention
```
  
- **Speech Transformer** Training
```
python ./bin/main.py --dataset $DATASET --transcripts_path $TRANSCRIPTS_PATH --output_unit $OUTPUT_UNIT --architecture transformer --batch_size 32 --d_model 512 --reduction mean --num_heads 8 --num_encoder_layers 12 --num_decoder_layers 6 --dropout 0.3 --ffnet_style ff --num_workers 4 --num_epochs 70 --init_lr 1e-06 --final_lr 1e-06 --peak_lr 1e-04 --init_lr_scale 0.01 --final_lr_scale 0.05 --sample_rate 16000 --frame_length 20 --frame_shift 10 --n_mels 80 --feature_extract_by kaldi --transform_method fbank --freq_mask_para 18 --time_mask_num 4 --freq_mask_num 2 --save_result_every 1000 --checkpoint_every 5000 --print_every 10 --mode train  --del_silence --normalize --use_cuda
```
  
### Evaluate for KsponSpeech
```
python ./eval.py --dataset_path $DATASET_PATH --transcripts_path $TRANSCRIPTS_PATH --model_path $MODEL_PATH --sample_rate 16000 --frame_length 20 --frame_shift 10 --n_mels 80 --normalize --del_silence --feature_extract_by kaldi --num_workers 4 --use_cuda --batch_size 32 --k 3  --decode greedy --print_every 10 --mode eval --transform_method fbank
```
  
Now you have a model which you can use to predict on new data. We do this by running `greedy search` or `beam search`.  
  
### Inference One Audio with Pre-train Models

* Command
```
$ python3 inference.py --model_path $MODEL_PATH --audio_path $AUDIO_PATH --device $DEVICE
```
* Output
```
음성인식 결과 문장이 나옵니다
```  
You can get a quick look of pre-trained model's inference, with a audio.  
  
### Checkpoints   
Checkpoints are organized by experiments and timestamps as shown in the following file structure.  
```
save_dir
+-- checkpoints
|  +-- YYYY_mm_dd_HH_MM_SS
   |  +-- trainer_states.pt
   |  +-- model.pt
```
You can resume and load from checkpoints.
  
## Troubleshoots and Contributing
If you have any questions, bug reports, and feature requests, please [open an issue](https://github.com/sooftware/End-to-end-Speech-Recognition/issues) on Github.   
For live discussions, please go to our [gitter](https://gitter.im/Korean-Speech-Recognition/community) or Contacts sh951011@gmail.com please.
  
We appreciate any kind of feedback or contribution.  Feel free to proceed with small issues like bug fixes, documentation improvement.  For major contributions and new features, please discuss with the collaborators in corresponding issues.  
  
### Code Style
We follow [PEP-8](https://www.python.org/dev/peps/pep-0008/) for code style. Especially the style of docstrings is important to generate documentation.  
    
### Paper References
  
*Ilya Sutskever et al. [Sequence to Sequence Learning with Neural Networks](https://arxiv.org/abs/1409.3215) arXiv: 1409.3215*  
  
*Dzmitry Bahdanau et al. [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473) arXiv: 1409.0473*   
  
*Jan Chorowski et al. [Attention Based Models for Speech Recognition](https://arxiv.org/abs/1506.07503) arXiv: 1506.07503*    
  
*Wiliam Chan et al. [Listen, Attend and Spell](https://arxiv.org/abs/1508.01211) arXiv: 1508.01211*   
   
*Dario Amodei et al. [Deep Speech2: End-to-End Speech Recognition in English and Mandarin](https://arxiv.org/abs/1512.02595) arXiv: 1512.02595*   
   
*Takaaki Hori et al. [Advances in Joint CTC-Attention based E2E Automatic Speech Recognition with a Deep CNN Encoder and RNN-LM](https://arxiv.org/abs/1706.02737) arXiv: 1706.02737*   
  
*Ashish Vaswani et al. [Attention Is All You Need](https://arxiv.org/abs/1706.03762) arXiv: 1706.03762*     
  
*Chung-Cheng Chiu et al. [State-of-the-art Speech Recognition with Sequence-to-Sequence Models](https://arxiv.org/abs/1712.01769) arXiv: 1712.01769*   
  
*Anjuli Kannan et al. [An Analysis Of Incorporating An External LM Into A Sequence-to-Sequence Model](https://arxiv.org/abs/1712.01996) arXiv: 1712.01996*  
  
*Daniel S. Park et al. [SpecAugment: A Simple Data Augmentation Method for Automatic Speech Recognition](https://arxiv.org/abs/1904.08779) arXiv: 1904.08779*     
    
*Rafael Muller et al. [When Does Label Smoothing Help?](https://arxiv.org/abs/1906.02629) arXiv: 1906.02629*   
  
*Daniel S. Park et al. [SpecAugment on large scale datasets](https://arxiv.org/abs/1912.05533) arXiv:1912.05533* 
    
*Jung-Woo Ha et al. [ClovaCall: Korean Goal-Oriented Dialog Speech Corpus for Automatic Speech Recognition of Contact Centers](https://arxiv.org/abs/2004.09367) arXiv: 2004.09367*
    
### Github References
  
*[IBM/Pytorch-seq2seq](https://github.com/IBM/pytorch-seq2seq)*  
  
*[SeanNaren/deepspeech.pytorch](https://github.com/SeanNaren/deepspeech.pytorch)*  
  
*[kaituoxu/Speech-Transformer](https://github.com/kaituoxu/Speech-Transformer)*  
  
*[OpenNMT/OpenNMT-py](https://github.com/OpenNMT/OpenNMT-py)*  
  
*[clovaai/ClovaCall](https://github.com/clovaai/ClovaCall)*  
  
*[LiyuanLucasLiu/RAdam](https://github.com/LiyuanLucasLiu/RAdam)*
  
*[AppleHolic/2020 AI Challenge - SpeechRecognition](https://github.com/AppleHolic/2020AIChallengeSpeechRecognition)*
   
### License
This project is licensed under the Apache-2.0 LICENSE - see the [LICENSE.md](https://github.com/sooftware/KoSpeech/blob/master/LICENSE) file for details
  
## Citation
  
A [technical report](https://arxiv.org/abs/2009.03092) on KoSpeech is available. If you use the system for academic work, please cite:
  
```
@ARTICLE{2020kospeech,
  author = {Soohwan Kim, Seyoung Bae, Cheolhwang Won},
  title = "{KoSpeech: Open-Source Toolkit for End-to-End Korean Speech Recognition}",
  journal = {ArXiv e-prints},
  eprint = {2009.03092}
}
```
