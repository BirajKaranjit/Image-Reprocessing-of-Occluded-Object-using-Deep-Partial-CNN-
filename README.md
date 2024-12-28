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
![Screenshot 2024-12-28 141258_5_11zon](https://github.com/user-attachments/assets/115336b8-0a71-4bfc-bd7e-346b846c305c)

![Screenshot 2024-12-28 141307_6_11zon](https://github.com/user-attachments/assets/69ef70ab-3e52-4388-842d-5c20506d1e81)


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
![Screenshot 2024-12-28 140823_4_11zon](https://github.com/user-attachments/assets/69fa2673-888d-4cde-988c-499dffd66400)

![Screenshot 2024-12-28 140438_1_11zon](https://github.com/user-attachments/assets/0db31e5d-5e54-442e-8700-21a749d95560)
![Screenshot 2024-12-28 140536_3_11zon](https://github.com/user-attachments/assets/a015405d-834f-4c05-9f73-021036fb364b)
![Screenshot 2024-12-28 140514_2_11zon](https://github.com/user-attachments/assets/2d52aa3f-6f5e-41e7-abd3-a758af3231e1)


### **📷 Sample Restorations**



