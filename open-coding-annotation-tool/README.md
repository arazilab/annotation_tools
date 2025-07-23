# Open Coding Annotation Tool

A simple browser-based tool for open coding and qualitative annotation.

---

## 🧩 Features

- Annotate JSON data with multiple custom codes
- Add, edit, delete, and **merge** codes
- Automatically track how many datapoints each code appears in
- Code suggestions and sorting by usage frequency
- Works entirely in your browser (no installs needed)
- Supports text, image, or webpage annotation modes
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
- `config.json`: configuration for mode and fields
- `sample_data.json`: your dataset

---

## 🔧 Sample `config.json`

Choose one of the following modes: `text`, `image`, or `webpage`.

```json
{
  "mode": "text",
  "fields": ["Review"],
  "dataFile": "sample_data.json"
}
```

Example for `image` mode:

```json
{
  "mode": "image",
  "fields": ["Image"],
  "dataFile": "sample_data.json"
}
```

Example for `webpage` mode:

```json
{
  "mode": "webpage",
  "fields": ["URL"],
  "dataFile": "sample_data.json"
}
```

---

## 📄 Sample `sample_data.json`

```json
[
  {
    "Stars": 4,
    "Review": "This article about cats was fascinating. I didn’t know they could have different colored eyes.",
    "Image": "https://upload.wikimedia.org/wikipedia/commons/thumb/a/a3/June_odd-eyed-cat.jpg/320px-June_odd-eyed-cat.jpg",
    "URL": "https://en.wikipedia.org/wiki/Cat"
  },
  {
    "Stars": 3,
    "Review": "Stars are so beautiful. I spent hours reading about their lifecycle and formation.",
    "Image": "https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Pleiades_large.jpg/320px-Pleiades_large.jpg",
    "URL": "https://en.wikipedia.org/wiki/Star"
  },
  {
    "Stars": 5,
    "Review": "This article gave a great history of filmmaking. I love how cinema evolved over time.",
    "Image": "https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Golde33443.jpg/320px-Golde33443.jpg",
    "URL": "https://en.wikipedia.org/wiki/Film"
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
  "Review": "This article about cats was fascinating. I didn’t know they could have different colored eyes.",
  "annotation": ["animal", "interesting"]
}
```
