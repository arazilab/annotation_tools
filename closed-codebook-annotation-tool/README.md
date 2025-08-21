# Closed Codebook Annotation Tool

A browser-based tool for qualitative annotation using a **predefined
codebook**.

------------------------------------------------------------------------

## 🧩 Features

-   Annotate JSON data with codes from a given codebook (not open
    coding).
-   Codebook loaded from a separate JSON file with:
    -   `code`: the code name
    -   `definition`: explanation of the code
    -   `example`: (optional) usage example
-   Codes are shown in a fixed order from the codebook.
-   Checkbox for assigning a code to the current datapoint.
-   **Learn more** button to view definition and example.
-   Edit, delete, and merge codes available.
-   Tracks frequency of each code across the dataset.
-   Works entirely in your browser (no installs needed).
-   Save and resume progress from JSON files.
-   Export updated codebook with definitions/examples.

------------------------------------------------------------------------

## 🚀 How to Use

### 1. Start a local server

From inside the folder, run:

``` bash
python3 -m http.server 8000
```

Then open in your browser:

    http://localhost:8000

------------------------------------------------------------------------

### 2. Files you need

-   `index.html`: main annotation interface
-   `config.json`: configuration for mode, fields, and file names
-   `sample_data.json`: your dataset
-   `codebook.json`: your codebook

------------------------------------------------------------------------

## 🔧 Sample `config.json`

``` json
{
  "mode": "text",
  "fields": ["Review"],
  "dataFile": "sample_data.json",
  "codebookFile": "codebook.json"
}
```

Modes: `text`, `image`, or `webpage`.

------------------------------------------------------------------------

## 📄 Sample `sample_data.json`

``` json
[
  {
    "Stars": 4,
    "Review": "This article about cats was fascinating.",
    "Image": "https://upload.wikimedia.org/...jpg",
    "URL": "https://en.wikipedia.org/wiki/Cat"
  },
  {
    "Stars": 3,
    "Review": "Stars are so beautiful.",
    "Image": "https://upload.wikimedia.org/...jpg",
    "URL": "https://en.wikipedia.org/wiki/Star"
  }
]
```

------------------------------------------------------------------------

## 📘 Sample `codebook.json`

``` json
[
  {
    "code": "animal",
    "definition": "Mentions of animals or animal-related content.",
    "example": "The cat had different colored eyes."
  },
  {
    "code": "astronomy",
    "definition": "References to stars, planets, or space topics.",
    "example": "I read about star formation."
  }
]
```

------------------------------------------------------------------------

## 💾 Save & Resume

-   Click **💾 Save** to export annotations.\
-   Click **📁 Open** to resume from a previous annotated dataset.\
-   Saved annotations include the codes used for each datapoint.

Example saved entry:

``` json
{
  "Stars": 4,
  "Review": "This article about cats was fascinating.",
  "annotation": ["animal"]
}
```

------------------------------------------------------------------------

## 🔁 Merging Codes

-   Click **Merge** next to a code.
-   Choose a second code and enter a name for the new merged code.
-   Tool replaces old codes with the new one across all entries.

------------------------------------------------------------------------

## 📘 Export Codebook

-   Click **📘 Save Codebook**.
-   Downloads a `codebook.json` file with current codes, definitions,
    and examples.

------------------------------------------------------------------------

## ✅ Annotation Format

Each entry will have an `annotation` field with a list of codes:

``` json
{
  "Stars": 4,
  "Review": "This article about cats was fascinating.",
  "annotation": ["animal"]
}
```

------------------------------------------------------------------------

## 📝 Notes

-   Works in your browser. No installation beyond a local server
    required.
-   The codebook is fixed at the start, but you may still edit, delete,
    or merge codes if needed.
