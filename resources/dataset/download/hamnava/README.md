# HamNava: A Dataset for Multi-Label Instrument Classification

**HamNava** (meaning "in unison" in Farsi) is a dataset designed for segment-level **multi-label instrument classification** in **Iranian classical music**. It consists of **6,000 five-second excerpts**, each annotated for the presence of **nine musical elements** (eight instruments + vocals), using **soft labels** gathered via a large-scale, community-driven annotation effort on **Telegram**.

---

## 📁 Dataset Contents

- `audio/`: 6,000 audio excerpts in `.mp3` format (22.05 kHz, mono, 5 seconds each)
- `annotations/`:
  - `train.csv`
  - `validation.csv`
  - `test.csv`
  - `train_bin.csv`
  - `validation_bin.csv`
  - `test_bin.csv`
  - Each CSV includes:
    - `sample_id`
    - Labels for:
      - `tar`, `setar`, `santur`, `oud`, `kamancheh`, `ney`, `tonbak`, `daf`, `vocal`
        - In soft-labeled files: values are floats between `0.0` and `1.0`
        - In binarized (*_bin) files: values are `0` or `1`, based on a threshold of **0.5**
    - `difficulty`: a binary label indicating whether the excerpt is from an **easy (0)** or **hard (1)** track

---

## 🎯 Task Description

The main goal is **multi-label instrument classification** in short audio segments from Iranian classical music, which is **monophonic** in texture but **heterophonic** in performance. Each sample may contain one or more instruments played simultaneously, making the task particularly challenging compared to traditional polyphonic datasets.


---

## 📊 Annotation Methodology

- **Crowd-sourcing platform**: Telegram bot  
- **Participants**: Pre-filtered by ear training test  
- **Annotation scale**:  
  - `0`: Not present  
  - `1-3`: Present with increasing confidence  
- Soft labels = average of annotator confidence  
- Balanced distribution between *easy* and *hard* excerpts  
- Annotations continued until consensus was reached


---

## 📈 Dataset Statistics

- **6,000** 5-second audio excerpts
- **60,000+** judgments
- **1,800+** contributors (after filtering by ear-training proficiency)
- Instruments:
  - **Strings**: Tar, Setar, Santur, Oud, Kamancheh  
  - **Wind**: Ney  
  - **Percussion**: Tonbak, Daf  
  - **Voice**: Vocal (including *Kalam* and *Chah-chah*)
- Confidence scores (1–3) were mapped to:
  - `1` → `0.5`
  - `2` → `0.75`
  - `3` → `1.0`
- Each excerpt is labeled with averaged soft labels based on multiple annotations
- Each excerpt is also labeled as either **easy** or **hard** based on instrument overlap and technique similarity
- Due to lower inter-annotator agreement, annotations for **Kalam** and **Chah-chah** are **not included** in the final dataset

---

## 🧪 Baseline Models

A series of evaluations were conducted:

- **CNN Baseline** using MFCCs (40 Mel filters, FFT size 1024, hop length 512)
- Performance measured using:
  - Soft-label regression (MSE, $R^2$)
  - Hard-label classification (Accuracy, F1-score)

Foundation models evaluated: 
- Music2vec, MusicHuBERT, MERT, where **Music2vec** achieved the highest overall performance for cross-cultural generalization.

---

## 🔒 Access Request and License
The dataset is available for non-commercial research purposes only.
To request access, fill out the form at: [link](https://forms.gle/rtrg26eK9cS4zRpR8), by which you agree to use it only for academic research.

---

## 📌 Ethics & Acknowledgements
- All contributors participated voluntarily and anonymously
- No personal information was collected
- Dataset construction approved by all relevant contributors
- Data provided by NAVAAK under academic sharing license

---

## 🔬 Research Paper

If you use this dataset, please cite:

> Pouya Mohseni, Bagher BabaAli, and Hooman Asadi. "HamNava: A Dataset for Multi-Label Instrument Classification." Transactions of the International Society for Music Information Retrieval, 2025.


```bibtex
@article{HamNava2025,
  author    = {Mohseni, Pouya and BabaAli, Bagher and Asadi, Hooman},
  title     = {HamNava: A Dataset for Multi-Label Instrument Classification},
  journal   = {Transactions of the International Society for Music Information Retrieval},
  year      = {2025},
  month     = {MON},
  doi       = {DOI},
  keyword   = {en_US}
}
```

---

## 💬 Contact
For questions or collaboration inquiries, contact:
- Pouya Mohseni
- Email: [mohseni0pouya@gmail.com](mailto:mohseni0pouya@gmail.com)
