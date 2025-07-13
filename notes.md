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

## Params

N_DATA = 283 # ! muss angepasst werden noch keine Ahnung

EPOCHE = 3-5 
BATCH_SIZE = 2-4 
GRADIENT_CHECKPOINTING = True
USE_REENTRAT = False  # bei memerr true, da cuda vorhanden
OPTIM = "paged_adamw_32bit"     # efficient (annahme: wenig speicher)
LEARNING_RATE =  2e-5  # bis zu 3e-5
LOGGING_STEPS = 50 # abhängig von num_step (ca 20%)
EVAL_STEPS = 50
SAVE_STEPS = 50 # kann größer um speicher zu sparen
EVAL_STRATEGY = "steps" > alle EVAL_STEPS wird Eval ausgeführt
SAVE_STRATEGY = "steps"
METRIC_FOR_BEST_MODEL = "eval_loss"
LOAD_BEST_MODEL_AT_END = True
MAX_GRAD_NORM = 1 # 0.5 stabiler, ausprobieren
WARMUP_STEPS = 0 # 5-10% der Schritte
DATASET_KWARG = {"skip_prepare_dataset":True} # wir preparen selber afaoik
REMOVE_UNUSED_COLUMNS = False
MAX_SEQ_LEN = 512
NUM_STEPS = (N_DATA // BATCH_SIZE) * EPOCHS
print(f"NUM_STEPS: {NUM_STEPS}")

weitere:

gradient_accumulation_steps hoch und batch size niedrig, wenn mem gering
-/- klein und batch size hoch, wenn mem hoch


warm up:

< 1k sample  < 500 num steps => 5-30
10k samples ; 1-5k ; 3-5%
> 100k ; > 10k; 10%+
