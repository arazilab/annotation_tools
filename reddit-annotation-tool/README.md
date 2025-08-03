# Reddit Annotation Tool

A specialized browser-based tool for open coding and qualitative annotation of Reddit posts and comments, based on the original open coding annotation tool and modified for social media content.

---

## 🧩 Features

- Annotate Reddit post-comment pairs with multiple custom codes
- Add, edit, delete, and **merge** codes
- Automatically track how many datapoints each code appears in
- Code suggestions and sorting by usage frequency
- Works entirely in your browser (no installs needed)
- **Auto-opens Reddit comments** in positioned windows on the left side of screen
- Save and resume progress from JSON files
- Save codebook as a `.json` file
- Keyboard shortcuts for efficient navigation

---

## 🚀 How to Use

### 1. Start a local server

From inside the `reddit-annotation-tool` folder, run:

```

python3 -m http.server 8000

```

Then open in your browser:

```

http://localhost:8000/reddit_annotation_tool.html

```

---

### 2. Files you need

- `reddit_annotation_tool.html`: main annotation interface
- `reddit_config.json`: configuration for Reddit data
- `reddit_sample_data.json`: your Reddit dataset

---

## 🔧 Sample `reddit_config.json`

```

{
"mode": "reddit",
"dataFile": "reddit_sample_data.json"
}

```

---

## 📄 Sample `reddit_sample_data.json`

Your data should follow this schema with Reddit post-comment pairs:

```

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

### Required fields:
- `id`: Reddit post ID (e.g., "t3_1cxw17u")
- `post_body`: Full text content of the Reddit post
- `comment_url`: Direct URL to a specific comment using old.reddit.com format

---

## 🖥️ Interface Layout

- **Top Left**: Save/Load/Codebook buttons
- **Top Right**: Post content in scrollable textbox
- **Bottom Left**: Navigation buttons and progress counter
- **Bottom Right**: Open coding annotation tools
- **Auto-positioned Reddit Comments**: Opens on left side of screen when navigating

---

## 🎯 Workflow

1. **Load your data**: Tool automatically loads Reddit post and comment URL
2. **View content**: Post text appears in the right panel
3. **Open comment**: Click "🔗 Open Reddit Comment (Left Side)" or use auto-open
4. **Annotate**: Add codes while viewing both post and comment
5. **Navigate**: Use "Next"/"Previous" buttons or arrow keys
6. **Auto-advance**: New comments automatically open when navigating (if enabled)

---

## ⌨️ Keyboard Shortcuts

- **Arrow Keys** (←→↑↓): Navigate between items
- **Spacebar**: Manually open comment window
- **Enter** (in code input): Add new code

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

## 🪟 Window Management

- **Auto-positioning**: Reddit comments open in left 45% of screen
- **Auto-closing**: Previous comment windows close when navigating
- **Toggle control**: Checkbox to enable/disable auto-opening
- **Clean shutdown**: Comment windows close when main tool closes

---

## ✅ Annotation Format

Saved annotations look like this:

```

{
"id": "t3_1c7l3yh",
"post_body": "Looking into switching cat food brands...",
"comment_url": "https://old.reddit.com/r/CATHELP/comments/1c7l3yh/is_daves_pet_food_a_good_brand/l08povl/",
"annotation": ["cat-nutrition", "brand-comparison", "price-concern"]
}

```

---

## 🔧 Troubleshooting

### Popups blocked?
- Allow popups for your localhost domain
- Comment windows need popup permission to position correctly

### Comments not loading?
- Ensure Reddit URLs use `old.reddit.com` format
- Check that URLs are accessible in your browser

### Navigation not working?
- Make sure your JSON data follows the required schema
- Verify all required fields (`id`, `post_body`, `comment_url`) are present

---

## 📊 Data Schema

```

{
"type": "array",
"description": "List of objects, each linking a Reddit post with a comment URL",
"items": {
"type": "object",
"properties": {
"id": {
"type": "string",
"description": "The Reddit post ID (e.g., 't3_1cxw17u')"
},
"post_body": {
"type": "string",
"description": "Full selftext body of the Reddit post"
},
"comment_url": {
"type": "string",
"description": "Direct URL to a comment using old.reddit.com format",
"pattern": "^https://old\\.reddit\\.com/.*"
}
},
"required": ["id", "post_body", "comment_url"]
}
}

```

---

Happy annotating! 🚀
