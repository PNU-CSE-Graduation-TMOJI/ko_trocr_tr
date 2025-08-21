# ko-trocr-tr
Textctrl 한국어 모델 본학습시 ocr-loss에 사용한 모델
**forked from ddobokki/ko_trocr**

## environment
```
python 3.8.20
```

## install
```
bash shell_scripts/install_base.sh
pip install -re requirements.txt
```

## run
기존 모델은 data 폴더 아래에 open.zip이 있어야 한다
https://dacon.io/competitions/official/236042/data

현재 모델은, SRnet에서 생성된 데이터를 아래의 open.zip 파일 형식에 맞게 바꾸어 넣었다.

- train [폴더]
폰트 손글씨 학습 데이터
TRAIN_00000.png ~ TRAIN_76887.png


- test [폴더]
폰트 손글씨 평가 데이터
TEST_00000.png ~ TEST_74120.png


- train.csv [파일]
id : 샘플 고유 id
img_path : 샘플 이미지 파일 경로
label : 샘플 이미지에 해당하는 Text


- test.csv [파일]
id : 샘플 고유 id
img_path : 샘플 이미지 파일 경로


- sample_submission.csv [제출양식]
utf-8 / utf-8-sig 인코딩으로 생성해야 정상적으로 채점이 가능합니다.
id : 샘플 고유 id
label : 이미지로부터 예측한 Text

또한, SRnet에서 생성한 이미지가 RGBA라서, RGB로 차원축소하는 함수를 추가했다

```
cd data
unzip open.zip
cd ..
bash shell_scripts/preprocess.sh
bash shell_scripts/run_train.sh
bash shell_scripts/inference.sh
```

## dirs 
```
├── data
│   ├── open.zip
│   ├── preprocess
│   ├── sample_submission.csv
│   ├── test
│   ├── test.csv
│   ├── train
│   └── train.csv
├── arguments
│   ├── __init__.py
│   ├── DatasetsArguments.py
│   ├── ModelArguments.py
│   ├── MyTrainingArguments.py
│   └── __pycache__
├── utils
│   ├── __init__.py
│   ├── augmentation.py
│   ├── data_collator.py
│   ├── dataset_utils.py
│   └── training_utils.py
├── shell_scripts
│   ├── inference.sh
│   ├── inference_tc.sh
│   ├── install_base.sh
│   ├── pid_kill.sh
│   ├── preprocess.sh
│   └── run_train.sh
├── LICENSE
├── literal.py
├── output
├── preprocess.py
├── README.md
├── requirements.txt
├── inference.py
├── inference_tc.py
└── train.py
```


