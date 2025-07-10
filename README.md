<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
</head>
<body>

<h1>🍏 Lesion‑Aware Explainability Validation for Apple Disease CNN</h1>

<p>This project implements an <strong>explainability validation pipeline</strong> to evaluate whether a CNN truly focuses on lesion regions when classifying apple leaf diseases. It leverages <strong>Grad-CAM and Grad-CAM++</strong>, and compares predicted attention with ground-truth lesion masks using <strong>IoU</strong>.</p>

<h2>🎯 Objective</h2>
<p><em>Validate lesion-aware predictions made by CNNs (like ResNet-50) on apple leaf diseases using explainable AI (XAI) methods and ground-truth lesion masks.</em></p>

<h2>🔬 Research Workflow</h2>

<h3>🔁 Common Pipeline</h3>
<ol>
  <li>Load Input Image + Ground-Truth Mask</li>
  <li>Preprocess Image</li>
  <li>Model Prediction</li>
  <li>Generate Grad-CAM / Grad-CAM++ Heatmaps</li>
  <li>Binarize the Heatmaps</li>
  <li>Compare with Ground-Truth Masks using IoU</li>
  <li>Visualize & Save Results</li>
  <li>Aggregate per-image IoU</li>
</ol>

<h3>✅ Pretrained vs Fine-Tuned Pipeline</h3>
<ul>
  <li><strong>Pretrained ResNet-50:</strong> Uses ImageNet weights without fine-tuning (60 images used)</li>
  <li><strong>Fine-Tuned ResNet-50:</strong> Trained on <a href="https://www.kaggle.com/datasets/nirmalsankalana/apple-leaf-disease-dataset">apple plant leaves dataset</a> with 143 layers frozen (300 images used)</li>
</ul>

<h2>📂 Folder Structure (Final Runtime View)</h2>
<p>The structure below reflects the **Colab Files panel** view <strong>after all processing and evaluation steps are completed</strong>:</p>

<pre><code>.
├── apple_plant_dataset/
│   ├── images/
│   ├── masks/
│   └── predicted/
├── original_dataset/
│   ├── images/
│   ├── masks/
│   ├── predicted/
│   ├── train/
│   └── val/
├── results/
│   ├── initial_visualizations/
│   ├── original_visualizations/
│   ├── advanced_visualizations/
│   ├── iou_scores_pre_trained.csv
│   ├── iou_scores_finetuned.csv
│   └── iou_scores_xai_alternatives.csv
├── finetuned_resnet50_from_filenames.h5
├── main.py
└── README.md
</code></pre>

<h2>🛠️ Setup Instructions</h2>

<h3>⚙️ No Setup Required</h3>
<p>All dependencies are already installed and configured inside the Colab notebook.</p>

<h3>📦 Dataset Preparation</h3>
<ul>
  <li>Prepare your <code>original_dataset.zip</code> containing 60 images + masks for pre-trained model testing</li>
  <li>Prepare your <code>apple_plant_dataset.zip</code> containing 300 images + masks for fine-tuning and evaluation</li>
  <li>Upload them to the notebook when prompted</li>
</ul>

<h2>🚀 Running the Project</h2>

<p><strong>⚠️ Note:</strong> The <code>main.py</code> script is included for reference and structure only. The actual pipeline should be run from the accompanying <strong>Google Colab notebook</strong> (see link below). The script is not CLI-ready and does not support <code>--mode</code> flags.</p>

<h3>🔗 Access Notebook</h3>
<p>
  <strong><a href="https://drive.google.com/file/d/1-tIfQclSLa-mgleBOVl9CZghMfa5v3oW/view?usp=sharing">Open Colab Notebook</a></strong>
</p>

<h2>📊 Output Results</h2>
<table border="1" cellpadding="5">
  <thead>
    <tr>
      <th>Model</th>
      <th>IoU CSV</th>
      <th>Visualizations</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Pre-trained</td>
      <td><code>results/iou_scores_pre_trained.csv</code></td>
      <td><code>results/initial_visualizations/</code></td>
    </tr>
    <tr>
      <td>Fine-tuned</td>
      <td><code>results/iou_scores_finetuned.csv</code></td>
      <td><code>results/original_visualizations/</code></td>
    </tr>
  </tbody>
</table>

<h2>📈 Sample Metrics</h2>
<pre><code>📊 Average IoU (Pre-trained ResNet-50):     0.0823
📊 Average IoU (Fine-tuned ResNet-50):     0.0739
</code></pre>

<h2>📸 Sample Visuals</h2>
<p>Each image includes: Original | GT Mask | Grad-CAM Heatmap | Binarized CAM</p>

<h2>🧪 Experimental Features that can be done</h2>
<ul>
  <li>Grad-CAM++ for higher localization</li>
  <li>Score-CAM (optional, slow)</li>
  <li>Otsu thresholding for adaptive binarization</li>
</ul>

<h2>⚠️ Large File Access</h2>
<p>Due to memory constraints, full datasets, model weights, and CSVs are provided via Google Drive.</p>

<p>
🔗 <strong><a href="https://drive.google.com/drive/folders/1cwXI0XCYV823UciGKcK6WnvXmHbwVCaJ?usp=sharing">Click here to access project files on Google Drive</a></strong><br>
(Replace the above link with your actual shared folder)
</p>

</body>
</html>
