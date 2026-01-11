# Custom VLM Design for Industrial Quality Inspection

## Scenario
A semiconductor manufacturer requires an offline Vision-Language Model (VLM) for PCB inspection. Inspectors query the system in natural language and expect structured responses with defect locations and confidence scores under 2 seconds of inference. The dataset consists of 50,000 PCB images with defect bounding boxes and no QA pairs.

---

## (A) Model Selection

### Selected Architecture: Custom BLIP-2–based VLM

BLIP-2 is selected due to its modular design, inference efficiency, and flexibility for domain-specific fine-tuning. Unlike generic conversational VLMs, BLIP-2 allows better grounding between vision and language, which is critical for industrial inspection.

**Key Factors Influencing Selection:**
- Moderate model size suitable for offline deployment
- Decoupled vision and language components
- Support for parameter-efficient fine-tuning (LoRA)
- Enterprise-friendly licensing
- Lower hallucination tendency compared to instruction-heavy models

**Localization Modifications:**
- Region-level embeddings extracted from defect bounding boxes
- Spatial tokens injected into the vision-language fusion layer
- Structured output head instead of free-form text generation

---

## (B) Design Strategy

### Architecture Overview
- Vision Encoder: Lightweight ViT or EfficientNet trained on PCB images
- Defect Region Extractor: Bounding-box–guided feature pooling
- Fusion Module: Cross-attention between visual regions and language tokens
- Language Decoder: Lightweight domain-constrained LLM

The system outputs structured JSON-style responses instead of open-ended text.

---

## (C) Optimization for <2s Inference

To meet real-time industrial constraints, the following optimizations are applied:
- INT8 quantization for both vision and language modules
- Model pruning to remove redundant attention heads
- Knowledge distillation from a larger teacher model
- LoRA-based fine-tuning to minimize parameter updates
- ONNX / TensorRT deployment for accelerated inference

---

## (D) Hallucination Mitigation

Hallucination is minimized using multiple strategies:
- Grounded training using bounding-box evidence only
- Penalizing answers without corresponding visual regions
- Confidence calibration and answer abstention for low-evidence cases
- Restricted vocabulary focused on industrial defect terminology

---

## (E) Training Plan

### Stage 1: Vision Model Training
Train a defect detector using bounding-box annotations.

### Stage 2: Synthetic QA Generation
Generate QA pairs from annotations using deterministic rules.

### Stage 3: VLM Fine-Tuning
Fine-tune the VLM using LoRA with frozen vision layers.

### Stage 4: Robustness Training
Include defect-free and ambiguous samples to reduce false positives.

---

## (F) Validation Strategy

The system is validated using:
- Localization accuracy (IoU and center error)
- Counting accuracy (Mean Absolute Error)
- Hallucination rate (ungrounded responses)
- Inference latency benchmarking
- Confidence calibration metrics

---

## Conclusion
This custom VLM design provides an efficient, hallucination-controlled, and industrially deployable solution for PCB quality inspection. The architecture ensures accurate localization, structured responses, and real-time offline performance suitable for semiconductor manufacturing environments.
