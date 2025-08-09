# Treinamento YOLOv8 com Subconjunto COCO (2 Classes)

Este projeto treina a rede **YOLOv8** usando um subconjunto do dataset COCO (COCO128) para detectar **duas classes**: `dog` e `bicycle`.  
O treinamento foi feito via **Transfer Learning**, aproveitando pesos pré-treinados para acelerar e melhorar os resultados.

---

## 📂 Estrutura do Projeto
```
.
├── datasets/
│   └── coco128_custom/       # Configuração personalizada com 2 classes
│       └── data.yaml
├── notebook/
│   └── treino_yolo_coco_colab.ipynb
├── runs/                     # Resultados do treinamento (gerado após treino)
├── README.md
└── LICENSE
```

---

## 🚀 Como Rodar no Google Colab

1. Abra o notebook no Colab:  
   [📌 **Abrir no Colab**](https://colab.research.google.com/drive/1awJq91sYF8IP6tT-Lj4O9VdpLPVmgFjP?usp=sharing)

2. Execute todas as células (`Runtime > Run all`).

3. O modelo treinado será salvo em:
```
runs/detect/train/weights/best.pt
```

4. Resultados de detecção estarão em:
```
runs/detect/predict/
```

---

## 💻 Como Rodar Localmente (com GPU)

### 1. Clonar o repositório
```bash
git clone https://github.com/seu-usuario/yolo-coco2-classes.git
cd yolo-coco2-classes
```

### 2. Criar ambiente virtual
```bash
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
.venv\Scripts\activate     # Windows
```

### 3. Instalar dependências
```bash
pip install ultralytics
```

### 4. Baixar e preparar o dataset COCO128
```bash
curl -L "https://github.com/ultralytics/yolov5/releases/download/v1.0/coco128.zip" -o coco128.zip
unzip coco128.zip -d ./datasets
```

### 5. Treinar o modelo
```bash
yolo task=detect mode=train model=yolov8s.pt data=./datasets/coco128_custom/data.yaml epochs=20 imgsz=640 batch=8
```

### 6. Fazer predições
```bash
yolo task=detect mode=predict model=runs/detect/train/weights/best.pt source=./datasets/coco128/images/train2017
```

---

## 📊 Configuração do Treinamento
- Modelo base: `yolov8s.pt` (pré-treinado no COCO completo)
- Dataset: COCO128
- Classes utilizadas: `dog` (classe 16), `bicycle` (classe 1)
- Tamanho da imagem: 640x640
- Épocas: 20
- Batch size: 8

---

## 🖼 Exemplo de Resultado

![Exemplo de detecção](https://raw.githubusercontent.com/ultralytics/yolov5/master/data/images/zidane.jpg)

---

## 📜 Licença
Este projeto segue a licença [MIT](LICENSE).
