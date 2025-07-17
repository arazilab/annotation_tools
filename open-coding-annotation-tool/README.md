# Open Coding Annotation Tool

A simple browser-based tool for open coding and qualitative annotation.

---

## 🧩 Features

- Annotate JSON data with multiple custom codes
- Add, edit, delete, and **merge** codes
- Automatically track how many datapoints each code appears in
- Code suggestions and sorting by usage frequency
- Works entirely in your browser (no installs needed)
- Save and resume progress from JSON files
- Save codebook as a `.json` file

---

## 🚀 How to Use

### 1. Start a local server

From inside the `open-coding-tool` folder, run:

```bash
python3 -m http.server 8000
```

Then open in your browser:

```
http://localhost:8000
```

---

### 2. Files you need

- `index.html`: main annotation interface
- `config.json`: tells the tool which fields to show
- `sample_data.json`: your dataset

---

## 🔧 Sample `config.json`

```json
{
  "fields": ["Review"],
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

- Click **💾 Save** to export annotations  
- Click **📁 Open** to resume from a previous file  
- Each entry gets an `annotation` key with a list of codes

---

## 🔁 Merging Codes

- Click **Merge** next to a code
- Choose a second code to merge with
- Enter a name for the new merged code
- The tool removes both old codes and replaces them across all entries

---

## 📘 Export Codebook

- Click **📘 Save Codebook**
- Downloads a `codebook.json` file with counts per code

---

## ✅ Annotation Format

Saved annotations look like this:

```json
{
  "Stars": 4,
  "Review": "Great movie!",
  "annotation": ["positive", "music"]
}
```
