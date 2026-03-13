# 🤟 Real-Time Sign Language Detection System

A real-time sign language gesture detection system built using **TensorFlow 2 Object Detection API** with **SSD MobileNet v2** as the base model. The system uses a webcam to detect and classify sign language gestures in real time.

## 🎯 Detected Gestures

| # | Gesture       | Description                        |
|---|---------------|------------------------------------|
| 1 | **Hello**     | Common greeting sign               |
| 2 | **Yes**       | Affirmative gesture                |
| 3 | **No**        | Negative gesture                   |
| 4 | **Thanks**    | Gratitude/Thank you sign           |
| 5 | **I Love You**| Universal sign for "I Love You"    |

## 🛠️ Tech Stack

- **Python** 3.10
- **TensorFlow** 2.10
- **OpenCV** for real-time video capture and display
- **SSD MobileNet v2** — pre-trained model fine-tuned on custom sign language data
- **LabelImg** — used for image annotation (bounding boxes)
- **TFRecord** format for training data pipeline

## 📁 Project Structure

```
RealTimeObjectDetection/
├── Tensorflow/
│   ├── labelImg/                  # Image annotation tool
│   ├── models/                    # TF Object Detection API models
│   ├── scripts/
│   │   └── generate_tfrecord.py   # XML-to-TFRecord converter
│   └── workspace/
│       ├── annotations/
│       │   ├── label_map.pbtxt    # Class labels (hello, yes, no, thanks, iloveyou)
│       │   ├── train.record       # Training TFRecords
│       │   └── test.record        # Testing TFRecords
│       ├── images/                # Training & test images
│       ├── models/
│       │   └── my_ssd_mobnet/     # Fine-tuned model checkpoints & pipeline config
│       └── pre-trained-models/    # Downloaded pre-trained SSD MobileNet
├── Tutorial.ipynb                 # Step-by-step training notebook
├── environment.yml                # Conda environment (tf2)
└── README.md
```

## 🚀 Getting Started

### Prerequisites

- [Anaconda](https://www.anaconda.com/download) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html) installed
- A webcam for real-time detection

### 1. Clone the Repository

```bash
git clone https://github.com/RockZoid2080/Real-time-sign-language-management-system-.git
cd Real-time-sign-language-management-system-
```

### 2. Create the Conda Environment

Recreate the exact environment using the exported `environment.yml`:

```bash
conda env create -f environment.yml
```

This will create a conda environment named **`tf2`** with all required dependencies (TensorFlow 2.10, OpenCV, Object Detection API, etc.).

### 3. Activate the Environment

```bash
conda activate tf2
```

### 4. Run the Detection

Open the `Tutorial.ipynb` notebook in Jupyter to train the model or run real-time detection:

```bash
jupyter notebook Tutorial.ipynb
```

## 🧠 Model Details

- **Architecture:** SSD MobileNet v2 320x320
- **Framework:** TensorFlow 2 Object Detection API
- **Training Data:** Custom-collected images annotated with LabelImg (Pascal VOC XML format)
- **Data Pipeline:** XML annotations → TFRecord via `generate_tfrecord.py`

## 📝 Training Pipeline

1. **Collect images** of each sign language gesture
2. **Annotate images** using LabelImg (creates XML bounding box annotations)
3. **Generate TFRecords** from annotated images:
   ```bash
   python Tensorflow/scripts/generate_tfrecord.py -x <XML_DIR> -l <LABELS_PATH> -o <OUTPUT_PATH> -i <IMAGE_DIR>
   ```
4. **Configure the pipeline** in `pipeline.config` (batch size, learning rate, etc.)
5. **Train the model** using the TF2 Object Detection training script
6. **Evaluate & detect** in real time using OpenCV

## 📄 License

This project is for educational and research purposes.

## 🙌 Acknowledgments

- [TensorFlow Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection)
- [LabelImg](https://github.com/heartexlabs/labelImg) for image annotation
- [Nicholas Renotte's](https://www.youtube.com/@NicholasRenotte) tutorials for inspiration
