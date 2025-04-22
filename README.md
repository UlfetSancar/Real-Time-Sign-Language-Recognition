Real-Time Sign Language Recognition System
==========================================

This project implements a lightweight, real-time sign language recognition system using MediaPipe Holistic for landmark detection 
and a Long Short-Term Memory (LSTM) neural network for temporal gesture classification. Designed for assistive communication, 
the system supports smooth gesture recognition using only webcam input, without requiring specialised hardware.

Features
--------
- Live gesture detection from webcam input
- Trained on custom sequences of 3 signs: `hello`, `thanks`, and `I love you`
- Uses MediaPipe Holistic for 3D landmark extraction (face, hands, and pose)
- Lightweight LSTM model with under 600K parameters
- Real-time FPS counter, confidence thresholds, and UI enhancements

Project Structure
-----------------
/SignLanguageRecognition/
│
├── Untitled.ipynb               # Jupyter notebook with full pipeline
├── model.h5                     # Trained LSTM model
├── data/                        # Collected gesture sequences (NumPy arrays)
│   ├── hello/
│   ├── thanks/
│   └── iloveyou/
├── images/                      # Optional screenshots or result visuals
├── requirements.txt             # Project dependencies

Setup Instructions
------------------
1. Clone the repository
   git clone https://github.com/yourusername/SignLanguageRecognition.git
   cd SignLanguageRecognition

2. Create a virtual environment (optional but recommended)
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate

3. Install dependencies
   pip install -r requirements.txt

Alternatively, install manually:
   pip install tensorflow==2.17.0 opencv-python mediapipe scikit-learn matplotlib pillow

Running the Project
-------------------
1. Open the notebook:
   jupyter notebook Untitled.ipynb

2. Run all cells in sequence:
   - Data collection
   - Feature extraction
   - Model training
   - Real-time gesture recognition with webcam and OpenCV interface

Model Details
-------------
- Input Shape: (30, 1662) — 30-frame sequence, 1662 landmarks per frame
- Architecture: Stacked LSTM layers → Dense → Softmax
- Output: Probability distribution over gesture classes
- Training: 200 epochs, 80:20 train-test split, early stopping

Results Summary
---------------
- Test Accuracy: 100% (on 3-class dataset)
- Latency: < 5 seconds prediction delay
- Performance: Stable real-time output on mid-tier hardware

Acknowledgements
----------------
- Built using MediaPipe and TensorFlow
- Inspired by Nicknochnack’s Action Detection tutorial

Future Work
-----------
- Expand vocabulary with more gestures
- Collect data from multiple users for better generalisation
- Add sentence-level recognition and mobile/web deployment

License
-------
This project is for academic and research purposes only. Attribution required when reused or extended.
