# Binary Annotation Tool

This is a keyboard-driven annotation tool for fast binary labeling (Yes/No).

---

## 🧩 Features

- Display custom question + selected data fields
- Annotate with keyboard:  
  `A` = No, `D` = Yes, `W` = Next, `S` = Previous  
- Progress tracker (seen / annotated / remaining)
- Save and resume with JSON files
- Warns if you try to close or reload before saving
- Works in all major browsers

---

## 🚀 How to Use

### 1. Start a local server

From inside the `binary-annotation-tool` folder, run:

```bash
python3 -m http.server 8000
```

Then open in your browser:

```
http://localhost:8000
```

### 2. Files you need

- `index.html`: main web interface
- `config.json`: tells the tool what question and fields to show
- `sample_data.json`: your dataset

---

## 🔧 Sample `config.json`

```json
{
  "question": "Is this review positive?",
  "fields": ["Stars", "Review"],
  "dataFile": "sample_data.json"
}
```

---

## 📄 Sample `sample_data.json`

```json
[
  {
    "Stars": 4,
    "Review": "I loved this movie. Great story and music."
  },
  {
    "Stars": 2,
    "Review": "Very slow and boring."
  }
]
```

---

## 💾 Save & Resume

- Click **💾 Save** to download your progress
- Click **📁 Open** to load and continue
- Annotations are stored with a field:
  - `annotation: true | false | "not_annotated"`
