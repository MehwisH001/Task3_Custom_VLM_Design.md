# AI Assignment – Computer Vision & Vision-Language Systems

This repository contains solutions to three applied AI tasks focused on object detection, industrial quality inspection, and Vision-Language Model (VLM) system design. All tasks are implemented with a practical, industry-oriented approach suitable for real-world deployment.

---

## Task 1: Custom Object Detection (From Scratch)

**Objective:**  
Build and train an object detection pipeline from scratch without using pre-trained weights.

**Highlights:**
- Custom CNN-based detector implemented in PyTorch
- Training performed from scratch (no pre-trained models)
- Evaluation based on inference speed, model size, and qualitative mAP
- Real-time detection demonstrated using a GIF

**Artifacts:**
- Training & inference notebook
- Trained model weights
- Demo GIF showing detection results

---

## Task 2: Automated Quality Inspection System for Manufacturing

**Objective:**  
Develop a computer vision system to detect and classify manufacturing defects before packaging.

**Manufactured Item:**  
Printed Circuit Board (PCB)

**Defect Types:**
- Scratch
- Misalignment
- Missing Component

**Features:**
- Defect localization using bounding boxes
- Rule-based defect classification
- Confidence score for each detected defect
- Pixel-level defect center coordinates
- Severity assessment (Low / Medium / High)

**Artifacts:**
- Inspection notebook
- Input PCB image
- Annotated output image with detected defects

---

## Task 3: Custom VLM Design for Industrial Quality Inspection

**Objective:**  
Design an offline Vision-Language Model (VLM) architecture for PCB inspection where inspectors can ask natural language questions and receive structured, grounded responses.

**Key Points:**
- Custom BLIP-2–based VLM design
- PCB-specific architectural adaptations
- <2s offline inference optimization strategy
- Hallucination mitigation techniques
- Multi-stage training and validation plan

**Artifact:**
- `Task3_Custom_VLM_Design.md` (detailed design document)

---

## Repository Structure

AI_Assignment/
├── Task1_Object_Detection/
│ └── README.md / notebook / demo
├── Task2_Quality_Inspection.ipynb
├── images/
│ └── pcb_test.jpg
├── output/
│ └── inspection_result_final.jpg
├── Task3_Custom_VLM_Design.md
├── README.md

---

## Tools & Technologies
- Python
- PyTorch
- OpenCV
- NumPy
- Matplotlib
- Google Colab

---

## Conclusion
This repository demonstrates end-to-end problem-solving across model implementation, system-level computer vision design, and advanced Vision-Language Model architecture planning. The solutions emphasize accuracy, explainability, efficiency, and industrial applicability.
