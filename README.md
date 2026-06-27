# Hi, I'm Adeeb Ali 👋

**Machine Learning Engineer · Electronics Engineer · Edge AI & FPGA Specialist**  
Combining deep learning, computer vision, and hardware acceleration to build systems that run fast at the edge — and think clearly at the system level.

---

## 🧠 What I'm Building

### 🏎️ F1 Digital Twin — Race Strategy Platform
> *A physics-first, explainable AI race strategy system — not a toy simulator.*

Feed it a track, weather, tire compound, fuel load, and driver telemetry. Get back optimal pit windows, tire degradation curves, and a plain-English strategy recommendation with full engineering rationale.

**Key modules:**
- **Telemetry Replay Engine** — Corner-by-corner speed, brake, throttle & tire temperature traces with driver comparison
- **Strategy Optimizer** — Recommends BOX NOW vs STAY OUT with explainable reasoning, not black-box outputs
- **Custom Physics** — Tire degradation, fuel burn, aero drag, cornering dynamics, and grip maps built from scratch. No Unity. No Unreal.

> Looking to collaborate on: Generative ML · Frontend · Backend · DevOps

---

## 🔬 Featured Projects

### ⚡ FPGA-Accelerated Image Enhancement via Quantization-Aware Residual CNN `2025–2026`
Deployed a lightweight Residual CNN onto Xilinx ZCU104 FPGA, achieving **8–10× real-time inference acceleration** with minimal quality loss.

- INT8 compilation via Vitis AI 3.0 + DPUCZDX8G with C++ and Python bindings
- Post-FPGA quality: **+9.71 dB PSNR / 0.90 SSIM** vs +10.94 dB in software — 10× faster, nearly identical output
- Full NAS → QAT → INT8 → Vitis AI pipeline engineered in Python
- Automated PSNR/SSIM/latency/throughput benchmarking exported to structured CSV reports

`PyTorch` `Vitis AI` `C++` `Xilinx ZCU104` `FPGA` `NAS` `INT8` `Docker`

---

### 🌑 EnhancementNet: Low-Light Image Enhancement for Visual SLAM `2025–2026`
Built a neural image restoration pipeline that enables ORB-SLAM3 to work in **extreme low-light conditions where it would otherwise fail entirely.**

- **54.6× brightness improvement**, **21.5× ORB feature increase**, **19.2× feature match improvement**
- Engineered failure-recovery logic converting un-initializable sequences into full point-cloud maps, keyframe graphs, and camera trajectories
- Containerized full inference pipeline with Docker for reproducibility and FPGA readiness

`PyTorch` `ORB-SLAM3` `OpenCV` `Docker` `Python` `Visual SLAM`

---

### 🔲 Canny Edge Detection Pipeline — Built from Scratch in C++ `2025–2026`
Production-structured Canny pipeline with zero external libraries: Gaussian Blur → Scharr Gradient → Non-Max Suppression → BFS/DFS Hysteresis.

- Containerized with Docker for deterministic builds
- Integrated performance profiling with exported execution metrics

`C++` `Docker` `Image Processing` `Systems Programming`

---

## 💼 Experience

**RF Engineer Intern — Orbital Link India** `2024–Present · Aligarh, India`  
RF system testing and signal analysis for satellite communication (INR 10L initiative). Antenna radiation pattern evaluation, multi-configuration RF measurements, and hardware-software co-design.

---

## 🛠️ Technical Skills

**ML & AI**  
`PyTorch` `Deep Learning` `CNNs` `NAS` `QAT` `INT8 Quantization` `Model Compression` `Transfer Learning` `NLP` `Recommender Systems`

**Computer Vision & Robotics**  
`OpenCV` `Object Detection` `Segmentation` `Image Enhancement` `Visual SLAM` `ORB-SLAM3` `Feature-Based Localization` `Autonomous Navigation`

**Hardware & Deployment**  
`FPGA` `Vitis AI 3.0` `Xilinx ZCU104` `DPUCZDX8G` `CUDA` `ONNX` `Edge AI` `Embedded Systems`

**Languages**  
`Python` `C/C++` `JavaScript` `TypeScript` `Java` `SQL` `MATLAB` `Verilog`

**Tools & DevOps**  
`Docker` `Git` `FastAPI` `Node.js` `Next.js` `Redis` `MongoDB` `MySQL` `PostgreSQL` `Nginx` `Jenkins` `Linux`

---

## 🌐 Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/adeebali521)
[![Email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:aliadee2003@gmail.com)
[![GitHub](https://img.shields.io/badge/github-%23121011.svg?logo=github&logoColor=white)](https://github.com/Adeeb-ali)

---

## 📊 GitHub Stats

![](https://github-readme-stats.shion.dev/api?username=Adeeb-ali&theme=dark&hide_border=true&include_all_commits=false&count_private=false)
![](https://streak-stats.demolab.com/?user=Adeeb-ali&theme=dark&hide_border=true)
![](https://github-readme-stats.shion.dev/api/top-langs/?username=Adeeb-ali&theme=dark&hide_border=true&include_all_commits=false&count_private=false&layout=compact)

[![](https://komarev.com/ghpvc/?username=Adeeb-ali&color=red&style=flat)](https://github.com/Adeeb-ali)
