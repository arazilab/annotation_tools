# Annotation Tools

This repository contains a collection of lightweight and customizable annotation tools built for use in our lab. These tools are designed to help you annotate data faster and more consistently through simple, browser-based interfaces.

Each tool in this repository can be cloned, modified, and tailored for your specific project. New tools will be added over time.

---

## 🔹 Tool 1: Binary Annotation Tool

### Purpose

The Binary Annotation Tool lets you label data points with a simple **Yes/No** choice using keyboard shortcuts. It's useful for tasks like sentiment classification, filtering noisy samples, or binary relevance judgments.

### Features

- Configurable question and data fields
- Keyboard-based annotation:  
  `A` = No, `D` = Yes, `W` = Next, `S` = Previous  
- Progress tracking (seen, annotated, remaining)
- Supports resuming from previously saved work
- Warnings for unsaved changes
- Save and load annotations in JSON format

---

### 🚀 Getting Started

1. **Clone the repo:**

```bash
git clone https://github.com/arazilab/annotation-tools.git
cd annotation-tools/binary-annotation-tool
```

2. **Start a local server:**

You must use a local HTTP server (browsers block local file loading via `file://`):

```bash
python3 -m http.server 8000
```

Then open in your browser:

```
http://localhost:8000
```

This works on all major browsers including Safari.

---

### 🛠️ Files

- `index.html`: Main web interface
- `config.json`: Specifies the annotation question, fields to show, and the data file to load
- `sample_data.json`: Your dataset (list of JSON objects)

---

### 🧩 `config.json` example

```json
{
  "question": "Is this review positive?",
  "fields": ["Stars", "Review"],
  "dataFile": "sample_data.json"
}
```

---

### 📄 `sample_data.json` example

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

### 💾 Saving & Resuming

- Use the **💾 Save** button to download annotated data.
- Use the **📁 Open** button to load a saved file and continue where you left off.
- Annotations are saved in the same format as the input data, with an added `annotation` field:
  - `true`, `false`, or `'not_annotated'`

---

### 🧠 Tip for Custom Projects

You can create different configs and datasets for each task by copying the `binary-annotation-tool` folder and adjusting:

- `config.json` for the question and data file
- JSON data file for your task content
