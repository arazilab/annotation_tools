# Reddit Annotation Tool

A specialized browser-based tool for open coding and qualitative annotation of Reddit posts and comments. Built on the Open Coding Annotation Tool.

---

## 🧩 Features

- Annotate Reddit post–comment pairs with multiple custom codes
- Add, edit, delete, and **merge** codes
- Automatically track how many datapoints each code appears in
- Code suggestions and sorting by usage frequency
- Works entirely in your browser (no installs needed)
- **Auto-opens Reddit comments** in a window on the left side
- Save and resume progress from JSON files
- Save codebook as a `.json` file
- Keyboard shortcuts for efficient navigation
- **Per-code Context**: edit a context note for each used code on each item
  - Context button per code. Shows `Context*` when text exists
  - Right-side **Context** textarea edits the selected code’s context
  - Context auto-saves on every keystroke

---

## 🚀 How to Use

### 1. Start a local server

From inside the `reddit-annotation-tool` folder, run:

```bash
python3 -m http.server 8000
```

Then open in your browser:

```
http://localhost:8000/reddit-annotation-tool/
```
The page is `index.html`, so the folder URL also works.

---

### 2. Files you need

- `index.html`: main annotation interface
- `reddit_config.json`: configuration for Reddit data
- `reddit_sample_data.json`: your Reddit dataset

---

## 🔧 Sample `reddit_config.json`

```json
{
  "mode": "reddit",
  "dataFile": "reddit_sample_data.json"
}
```

---

## 📄 Sample `reddit_sample_data.json`

Your data should follow this schema with Reddit post–comment pairs:

```json
[
  {
    "id": "t3_1c7l3yh",
    "post_body": "Looking into switching cat food brands from Whole Hearted, as they changed their recipe recently...",
    "comment_url": "https://old.reddit.com/r/CATHELP/comments/1c7l3yh/is_daves_pet_food_a_good_brand/l08povl/"
  },
  {
    "id": "t3_1jtvbru",
    "post_body": "Hey all\nSo normally my cats eat fancy feast pate...",
    "comment_url": "https://old.reddit.com/r/CatAdvice/comments/1jtvbru/what_is_the_verdict_on_friskies/mlxjfr6/"
  }
]
```

### Required fields
- `id`: Reddit post ID (for example, `"t3_1cxw17u"`)
- `post_body`: Full text content of the Reddit post
- `comment_url`: Direct URL to a specific comment using `old.reddit.com` format

---

## 🖥️ Interface Layout

- **Top Left**: Save, Open, Codebook buttons
- **Top Right**: Post content in a scrollable box
- **Bottom Left**: Navigation buttons and progress
- **Bottom Right**: Coding tools and Context box
- **Comment window**: Opens on the left side of the screen

---

## 🎯 Workflow

1. **Load your data**. The tool loads the post and comment URL
2. **Open the comment**. Click “🔗 Open Reddit Comment (Left Side)” or use auto-open
3. **Annotate**. Add codes while viewing the post and comment
4. **Set context**. Click **Context** for a code, then type in the Context textarea
5. **Navigate**. Use Next or Previous, or arrow keys
6. **Save** when you are done

---

## ⌨️ Keyboard Shortcuts

- Arrow keys: navigate between items
- Spacebar: open comment window
- Enter in code input: add new code

---

## 💾 Save & Resume

- Click **💾 Save** to export annotations
- Click **📁 Open** to resume from a previous file
- Each entry gets:
  - an `annotation` array with codes used on that item
  - a `context` dictionary where keys are codes and values are strings

**Saved item example:**

```json
{
  "id": "t3_1c7l3yh",
  "post_body": "Looking into switching cat food brands...",
  "comment_url": "https://old.reddit.com/r/CATHELP/comments/1c7l3yh/is_daves_pet_food_a_good_brand/l08povl/",
  "annotation": ["cat-nutrition", "brand-comparison"],
  "context": {
    "cat-nutrition": "Owner is worried about ingredient changes",
    "brand-comparison": "Mentions Dave's vs Whole Hearted"
  }
}
```

The tool still loads older files that saved a single string in `context`. It maps that string to each used code for backward compatibility.

---

## 🔁 Merging Codes

- Click **Merge** next to a code
- Choose a second code to merge with
- Enter a name for the new merged code
- The tool removes both old codes and adds the merged name across all entries

**Context behavior on merge:**
- If both codes had context on an item, they are concatenated with a space
- The old context keys are removed
- The merged code key is created or updated

---

## 📘 Export Codebook

- Click **📘 Save Codebook**
- Downloads a `reddit_codebook.json` file with counts per code

---

## 🪟 Window Management

- Auto-positioning: comment opens on the left 45% of the screen
- Auto-closing: previous comment window closes when navigating
- Toggle control: checkbox to enable or disable auto-open
- Clean shutdown: comment windows close when the main tab closes

---

## ✅ Output Format

Each item is saved with annotations and a per-code context dictionary:

```json
{
  "annotation": ["code-a", "code-b"],
  "context": {
    "code-a": "note for code-a",
    "code-b": "note for code-b"
  }
}
```

---

## 🔧 Troubleshooting

**Popups blocked?**  
Allow popups for localhost. The browser needs permission to position comment windows.

**Comments not loading?**  
Use `old.reddit.com` links. Check that the URLs open in your browser.

**Navigation not working?**  
Check the JSON schema. Verify the required fields are present.

---

## 📊 Data Schema

```json
{
  "type": "array",
  "description": "List of objects. Each links a Reddit post with a comment URL.",
  "items": {
    "type": "object",
    "properties": {
      "id": {
        "type": "string",
        "description": "Reddit post ID (for example, 't3_1cxw17u')"
      },
      "post_body": {
        "type": "string",
        "description": "Full selftext body of the Reddit post"
      },
      "comment_url": {
        "type": "string",
        "description": "Direct URL to a comment using old.reddit.com format",
        "pattern": "^https://old\.reddit\.com/.*"
      }
    },
    "required": ["id", "post_body", "comment_url"]
  }
}
```

---

Happy annotating! 🚀
