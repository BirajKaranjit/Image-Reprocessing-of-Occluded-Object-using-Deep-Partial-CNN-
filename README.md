# Image-Reprocessing-of-Occluded-Object
Here’s a visually appealing version of the project description formatted for GitHub:

---

# **Image Reprocessing of Occluded Objects**

This project leverages **Deep Learning-based Inpainting Techniques** to reconstruct occluded regions in images, offering realistic and structurally coherent restorations. The solution is built on a **U-Net Architecture** enhanced with **Partial Convolution Layers** to ensure efficient and accurate feature extraction.

---

## **🌟 Key Features**

- **🎯 Objective**:  
  Restore missing or occluded portions of images while preserving realism and structural accuracy.

- **🏗️ Architecture**:  
  - Built on **U-Net** with **Partial Convolutions** for focused feature extraction.  
  - **16 Layers**: 8 encoder layers + 8 decoder layers.  

- **📊 Loss Functions**:  
  Optimized using a combination of losses:  
  - **Hole Loss**: MAE of restored occluded pixels.  
  - **Valid Loss**: MAE of restored non-occluded pixels.  
  - **Perceptual Loss**: MAE after feature extraction using pre-trained VGG-16.  
  - **Style Loss**: MAE of Gram Matrices of feature maps.  
  - **Total Variational Loss**: MAE in 1-pixel dilated regions.  
  - **Final Loss Formula**:  
    `L(total) = L(valid) + 6L(hole) + 0.05L(perceptual) + 120L(style) + 0.1L(TV)`  

---

## **🗂️ Dataset**

- **Training Samples**: 4,200  
- **Validation Samples**: 420  
- **Testing Samples**: 59  
- **Source**:  
  - Original images from **Place4Net**.  
  - Binary masks generated using **OpenCV** (random lines and circles).  
- **Mask Representation**:  
  - **Black Pixels (0)**: Occluded regions.  
  - **White Pixels (1)**: Valid regions.  

---![Screenshot 2024-12-28 141258](https://github.com/user-attachments/assets/c33a7e51-90c9-4149-a515-a4adc80d1d61)
![Screenshot 2024-12-28 141307](https://github.com/user-attachments/assets/6fcb03dc-d44e-4b31-9e30-9445baa4c996)


## **⚙️ Training Details**

- **Framework**: PyTorch  
- **Hardware**: Google Colab Pro GPUs (V100 & A100, 16 GiB Memory)  
- **Hyperparameters**:  
  - **Epochs**: 55  
  - **Batch Size**: 7  
  - **Learning Rate**: 0.0002  

---

## **🧪 Testing**

- Tested on **59 local samples**, focusing on **human face occlusions** in old photos.  
- Results demonstrate **effective hole removal** and **realistic image restoration**.

---

### **✨ Results**

Training and validation loss decreased consistently across 55 epochs, indicating effective learning. The model excels at reconstructing complex textures and occlusions.
![Screenshot 2024-12-28 140823](https://github.com/user-attachments/assets/99124345-a389-436c-9966-a219ae756298)

---

### **📷 Sample Restorations**

![Screenshot 2024-12-28 140438](https://github.com/user-attachments/assets/83c884a7-561e-4cf6-9469-f19818461013)
![Screenshot 2024-12-28 140536](https://github.com/user-attachments/assets/36738265-df14-4b01-b8a8-212e85382c1b)
![Screenshot 2024-12-28 140514](https://github.com/user-attachments/assets/25c2e578-637f-41a3-909c-ab9942d13fda)

