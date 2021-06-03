# Generalized End-To-End Loss for Speaker Embedding

Use this repo to train speaker embedding weights for multi-speaker synthesizer model like [Tacotron2, GlowTTS](https://github.com/coqui-ai/TTS), ...

## **Pre-requisites**
1. Python >= 3.6
2. Install [ffmpeg](https://ffmpeg.org/download.html#get-packages).
3. Install requirements.
4. Download the [preprocessed VIVOS dataset]().

## **Preprocess**
Put vivos dataset in <datasets_root> then run this command
```
python encoder_preprocess.py <datasets_root>
```
Generated mels for each speaker are saved in `<datasets_root>/ge2e_data/` by default,<br>
you can change the path by adding `--out_dir` option. <br>
For details in dataset format before and after preprocess: `dataset_format.txt` 

## **Pretrained Model**
[Download pretrained models](https://drive.google.com/drive/folders/11ZnmF9wtgWNH_MeTwttGVUGoSXrfO7jh?usp=sharing)<br/> 

## **Training**
Generated mel-spectrograms in numpy format using Tacotron2 with teacher-forcing (GTA) <br>
are provided in **preprocessed VIVOS dataset**.
```
python encoder_train.py <run_ID> \
<datasets_root>/ge2e_data \
-m <dir_to_load_pretrained_model_and_store_backup> \
--no_visdom
```
If a model state from the same run ID was previously saved, the training will restart from there.<br>
Pass -f to start from scratch.<br>
