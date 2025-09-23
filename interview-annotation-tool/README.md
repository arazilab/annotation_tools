# Interview Annotation Tool

A simple browser‑based tool for open coding and qualitative annotation of interview transcripts.

This tool is adapted from the generic open coding annotation interface.  It shows one utterance in bold with two preceding and two following utterances in grey, so you can easily see the context of each spoken turn.  You can assign custom codes to each utterance, merge or edit codes, and add a free‑form context note that is saved in your JSON output.  Everything runs locally in your browser – there is no server or installation required.

---

## 🧩 Features

* Annotate JSON interview data with multiple custom codes
* Shows two previous and two next utterances in grey for context
* Add, edit, delete and merge codes
* Automatically track how many datapoints each code appears in
* Add a **Context** note for each datapoint (saved in JSON)
* Works entirely in your browser (no installs needed)
* Save and resume progress from JSON files
* Export a codebook as a `.json` file

---

## 🚀 How to Use

### 1. Start a local server

From inside the `interview-annotation-tool-final` folder, run:

```bash
python3 -m http.server 8000
```

Then open in your browser:

```
http://localhost:8000
```

---

### 2. Files you need

* `index.html` – main annotation interface
* `config.json` – configuration for mode and fields
* `sample_data.json` – your dataset

Place all three files in the same directory before starting the local server.

---

## 🔧 Configuration

The tool reads its configuration from `config.json`.  In this version the mode is always `"text"` and the field set to display is `"Utterance"`.  The `dataFile` points to your JSON transcript.

Example:

```json
{
  "mode": "text",
  "fields": ["Utterance"],
  "dataFile": "sample_data.json"
}
```

---

## 📄 Sample `sample_data.json`

The dataset file must be a list of objects.  Each object should have at least three keys:

* **Speaker** – a string identifying who is talking (e.g. `"Interviewer"`, `"Participant"`)
* **Time** – a string indicating when the utterance occurs (optional)
* **Utterance** – the text of the spoken turn that you will annotate

Here is a shortened example:

```json
[
  {
    "Speaker": "Interviewer",
    "Time": "00:00–00:10",
    "Utterance": "Hello, thank you for joining us today."
  },
  {
    "Speaker": "Participant",
    "Time": "00:10–00:15",
    "Utterance": "Thank you for having me."
  },
  {
    "Speaker": "Interviewer",
    "Time": "00:15–00:20",
    "Utterance": "Could you tell us your name?"
  },
  {
    "Speaker": "Participant",
    "Time": "00:20–00:25",
    "Utterance": "I'm Jane Smith."
  }
]
```

---

## 💾 Save & Resume

* Click **💾 Save** to export your annotated transcript.  Each entry in the output contains all original fields along with an `annotation` list and a `context` dictionary keyed by codes.
* Click **📁 Open** to resume from a previously saved file.  All codes and contexts will load back into the tool.
* Click **📘 Save Codebook** to download a list of all codes with their usage counts.

---

## 🗒 Context Field

The context box appears under **New Code** on the right.  After selecting a code for the current utterance, you can type any notes or additional observations here.  When you move to the next utterance, the text box disables itself until a code is selected again.  These notes are saved in the JSON output under the `context` key.

---

## 🔁 Merging Codes

* Click **Merge** next to a code to combine it with another.
* Choose a second code to merge with and enter a name for the new merged code.
* The tool removes both old codes and replaces them across all entries while combining any context notes.

---

## 📘 Export Codebook

The codebook lists each unique code along with the number of entries it annotates.  Use this to see how frequently concepts occur in your interviews.

---

## ✅ Annotation Format

The saved annotations include all original fields plus two new keys:

```json
{
  "Speaker": "Interviewer",
  "Time": "00:25–00:30",
  "Utterance": "How old are you?",
  "annotation": ["demographics", "age"],
  "context": {
    "demographics": "Interviewer asks about age",
    "age": "Key demographic question"
  }
}
```

This structure makes it easy to import your coded data into analysis tools later.

---

Happy coding!
