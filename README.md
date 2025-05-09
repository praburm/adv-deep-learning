
# Intelligent Face Recognition System using Siamese Networks

This project is a Flask-based web application for intelligent facial recognition using Siamese Networks. It supports both 1:1 face verification and 1:N face identification, and integrates live video analysis, image comparison, and statistics reporting.

---

## 📦 Project Structure

```
.
├── app.py                        # Flask WebApp main file
├── face_compare.py              # CLI utility to test face comparison and stats
├── generate_embeddings.py       # Generate embeddings from known faces
├── train.py                     # Train base and Siamese models
├── known_faces/                 # Folder containing known face images
├── known_embeddings/            # Stores embeddings.pkl
├── saved_models/                # Trained models (base_model.h5, siamese_model.h5)
├── output/
│   └── frame_detected/          # Stores processed frames with detected faces
├── static/                      # Static assets like CSS, JS, images
├── templates/                   # HTML templates
└── face_recog_env.yml           # Conda environment file with dependencies
```

---

## ⚙️ Setup Instructions

### 1. Create and Activate Conda Environment

```bash
$ conda env create -f face_recog_env.yml
$ conda activate face_recog_env
```

### 2. Generate Embeddings

Generate embeddings for the images in the `known_faces/` directory.

```bash
$ python generate_embeddings.py
```

This will generate `embeddings.pkl` under `known_embeddings/`.

### 3. Train and Save Models

Train the Base model and Siamese network:

```bash
$ python train.py
```

This will save the trained models to `saved_models/base_model.h5` and `siamese_model.h5`.

### 4. Test Standalone Face Comparison (Optional)

You can run face comparison from CLI using:

```bash
$ python face_compare.py
```

### 5. Run the Flask Web Application

```bash
$ python app.py
```

This launches the Flask web server with features like:

- **Face Compare** (Verification 1:1 and Identification 1:N)
- **Live Camera Feed** - Face detection in real-time
- **Register New Face** - Register new identities via image
- **Upload and Analyze Video** - Frame extraction and face recognition
- **Show Match Statistics** - Displays distance metrics and similarity data

> ℹ️ **Note:** When you run `app.py`, it will process the frames and detect the faces with the stored embeddings in the database. The resulting object-detected images will be saved in the folder: `output/frame_detected/`.

---

## ✅ Features

- Siamese Neural Network for face verification
- Embedding-based identification from known faces
- Image upload and video processing interface
- Real-time face detection from webcam
- Distance metric logging and match statistics

---

## 📌 Face Verification vs Identification

| Task               | Description                                   |
|--------------------|-----------------------------------------------|
| **Face Verification (1:1)** | Compares two face images and tells whether they match. |
| **Face Identification (1:N)** | Compares a face image against a database to find the best match. |

---

## 📄 License

This project is intended for educational purposes.
