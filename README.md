[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/yOwut1-r)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=21354287&assignment_repo_type=AssignmentRepo)

# 🧠 Neurosynth Frontend
This project implements an **interactive AJAX-based frontend** for exploring the **NeuroSynth** API service hosted at  
[`https://hpc.psy.ntu.edu.tw:5000`](https://hpc.psy.ntu.edu.tw:5000).

The web page allows users to:
1. 🔤 Dynamically search for neuroscience terms (live suggestions)
2. 🧩 Fetch related terms and corresponding study metadata
3. ⚖️ Compare two terms using logical relations (`AND`, `NOT`)

---

## 🚀 Features Overview

### 1️⃣ Live Term Suggestions (動態搜尋)
Users can start typing any term (e.g., `amygdala`, `emotion`), and the interface will display **auto-complete suggestions** based on the `/terms` endpoint.  
Suggestions update in real-time as the user types.

![Live Term Suggestions Screenshot](./live_search.png)

---

### 2️⃣ Related Terms & Studies Search (關聯詞與研究查詢)
After selecting a term, users can:
- **Fetch related terms** with co-occurrence and Jaccard index scores.
- **Fetch related studies** that mention the target term, showing detailed information such as title, authors, journal, and year.

![Related Terms and Studies Screenshot](./related_study.png)

---

### 3️⃣ Term Comparison: `AND` / `NOT` (詞彙交集與差集查詢)
Users can input two terms and query:
- **Intersection (`AND`)** → studies containing both terms.
- **Difference (`NOT`)** → studies containing the first term but not the second.

Each study entry lists:
- 🧩 study ID / contrast ID  
- 📖 title  
- 👩‍🔬 authors  
- 📘 journal  
- 📅 publication year  

![Term Comparison Screenshot](./and_not.png)

---

## 🧰 Technical Details

- **Frontend:** HTML + JavaScript + Bootstrap 5  
- **API Endpoint:** [https://hpc.psy.ntu.edu.tw:5000](https://hpc.psy.ntu.edu.tw:5000)
- **AJAX Requests:** Fetch API (asynchronous JSON retrieval)
- **Dynamic Autocomplete:** implemented via `/terms` endpoint
- **Study Queries:**  
  - `/query/<term>/studies`  
  - `/query/<termA> and <termB>/studies`  
  - `/query/<termA> not <termB>/studies`

---

## 📸 Example Query Walkthrough

| Query Type | Example Input | API Request | Description |
|-------------|----------------|--------------|--------------|
| Related Terms | `amygdala` | `/terms/amygdala` | Returns top co-occurring terms |
| Studies | `amygdala` | `/query/amygdala/studies` | Returns all studies containing “amygdala” |
| Intersection | `amygdala`, `emotion` | `/query/amygdala and emotion/studies` | Returns 93 studies containing both |
| Difference | `amygdala`, `emotion` | `/query/amygdala not emotion/studies` | Returns 292 studies containing only “amygdala” |

---

## 💡 Notes
- The site requires access to NTU’s NeuroSynth API (`hpc.psy.ntu.edu.tw:5000`).
- Each section (live search / related terms / term comparison) uses asynchronous fetches for smooth interaction.
- This implementation demonstrates real-world **frontend–API integration** for neuroscience text mining.

---

## 🧑‍💻 Author
**譚靖蓉 (Anna Tan)**  
National Taiwan University · Master Program of Statistics  
Email: *r13h41009@ntu.edu.tw*  
GitHub Classroom Assignment: [NeuroSynth Frontend - HW07](https://classroom.github.com/a/yOwut1-r)
