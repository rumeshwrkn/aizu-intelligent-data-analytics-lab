# Disk Cleanup Instructions


After training a machine learning model, several files and directories may be unnecessary and can be deleted to save space. These files vary depending on the framework you're using, but here are some common types of files that can be safely deleted


## 1. Checkpoints and Intermediate Model Weights

Files: If you saved multiple checkpoints during training (after every epoch), you might only need the final model or the best-performing checkpoint. Delete the rest.

Common file types: ```.h5, .ckpt, .pt, .pth``` (depending on the framework like TensorFlow, PyTorch, etc.).

## 2. Temporary Data and Cache Files

Cache files created during training (especially with frameworks like TensorFlow and PyTorch) can consume significant space. These are typically stored in temporary directories.

Directories: ```.cache, __pycache__, .ipynb_checkpoints, etc```.


## 3. TensorBoard or Log Files

If you logged data during training for visualization, these files may take up space.

Files: TensorBoard log files (usually stored in a logs/ or runs/ directory).

Directories: logs, runs.

## 4. Unused Data Files

Training and validation datasets are sometimes stored locally. Once the model is trained, you might not need to keep these files.

Files: Raw data files (CSV, images, etc.), especially if they are already backed up.

## 5. Model Training Artifacts

If you created any visualization artifacts or debugging files (plots, evaluation metrics), those can be archived or deleted.

Files: .png, .pdf, .html (for evaluation plots, etc.).

## 6. Docker-related Files (If Using Docker)

If you're using Docker for training, old images and containers can take up space.


## 7. Generated Intermediate Data

During preprocessing, large intermediate datasets might have been saved to disk (e.g., tokenized data, augmented images). If these can be regenerated, they can be deleted.

Directories: Any folder you used for intermediate data storage.

## 8. Unused Model Variants (if applicable)

If you trained and saved multiple versions of the model, you can delete older or less accurate versions, keeping only the final or best model.
<br><br><br>

![Warning](https://img.shields.io/badge/Warning-red)

*Be cautious when deleting files and ensure that any important data or checkpoints have been backed up first. If you're using a version control system like Git, you might also want to ensure critical files (like your final model and scripts) are tracked and safe.*

# Useful Commands to cleanup unnecessary files

### General Cleanup (Linux/Unix-based systems)

```find . -name "__pycache__" -exec rm -rf {} +```

### Remove Jupyter notebook checkpoints
```find . -name ".ipynb_checkpoints" -exec rm -rf {} +```

### Remove cache directories
```find . -type d -name ".cache" -exec rm -rf {} +```

### Remove TensorFlow or PyTorch checkpoints and model weights

```find . -name "*.ckpt" -exec rm -rf {} +
find . -name "*.h5" -exec rm -rf {} +
find . -name "*.pt" -exec rm -rf {} +
find . -name "*.pth" -exec rm -rf {} +
```

### Remove log files
```find . -name "*.log" -exec rm -rf {} +```

### Remove temporary or unnecessary data files
```rm -rf /path/to/data/files/*```

