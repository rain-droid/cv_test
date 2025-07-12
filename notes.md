


Richies Code Dependencies


--installs-------------

Pip Packages:

- bitsandbytes 
- accelerate:
Hardware Effizienz, Management von verteiltem Training => effizientes Training großer Modelle 
- nltk 
NLP, optional da wir transformers haben
edit_distance: evtl Caption Qualität messen
- lightning:
Training Kontrollmechanismen => Training: Struktur  & Skalierbarkeit
- peft
- datasets
- Pillow

Github Packages:
- huggingface/transformers  ->"https://github.com/huggingface/transformers.git"



--imports-------------

transformers: BitsAndBytesConfig, LlavaNextForConditionalGeneration, Autoprocessor
datasets:  load_dataset 
huggingface_hub: notebook_login, HfApi
peft: LoraConfig,  prepare_model_for_kbit_training, get_peft_model

prepare_model_for_kbit_training: Vorbereitung für QLoRA 

os
google.colab import drive 
json
torch

torch.utils.data : Dataset, DataLoader
typing:  Any, DIct
pandas
random
PIL: Image
matplotlib.pyplot 

lightning 
lightning.pytorch.callback: Callback -> logging um aktionen am ende einer epoche durchzuführen
lightning.pytorch.callback.early_stopping: Early Stopping -> wenn metriken (loss_func bswp.) sich über epochen nicht verbessern 
=> Prevention von Overfitting und spart Zeit
lightning.pytorch.loggers: CSVLogger => loggt einfach Daten in CSV , danach mit pandas read_csv zugreifen

=> empfehlenswert


re
nltk: edit_distance
numpy

Links:
- https://github.com/uygarkurt/Fine-Tune-VLMs

