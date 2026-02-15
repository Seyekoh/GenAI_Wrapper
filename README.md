# Prompt Proxy (Hugging Face)

A vanilla HTML/CSS/JS "Prompt Proxy" that wraps user prompts with:
- a selectable **System Persona**
- hardcoded **Developer Rules**
- a dynamic **temperature** slider (0.0 → 2.0)

Then sends an OpenAI-compatible chat completion request to the Hugging Face Inference API and displays the response.

## Run locally

### Option A: Simple local server (recommended)
From this folder:

```bash
python -m http.server 8000
```

Open: http://localhost:8000

> Some browsers restrict fetch() from `file://` pages. A small local server avoids that.

### Add your token (keep it out of GitHub)

1) Create `config.local.js`

2) Edit `config.local.js`:
    - Add API Token to file with following format:
```js
window.HF_TOKEN = "hf_********************************";
```

`config.local.js` is in `.gitignore`, so it will not be committed.

## Temperature proof (assignment requirement)

** NOTE **
Requirements want temp from 0.0 - 2.0, but temp only works up to 1.5
Will result in validation error if temp > 1.5
**  **

Use the same prompt:
- set T=0.0 → more deterministic / less variation
- set T=1.5 → more variation / creative outputs

The UI includes quick buttons to set these values.

## What was GenAI-generated vs written by me

- GenAI-assisted (ChatGPT): initial scaffolding suggestions and UI layout ideas.
- Written/edited by me: final HTML/CSS/JS, the developer rules block, persona mapping, and Hugging Face integration wiring.

(Adjust this section to match what *you* personally did vs generated.)

## Notes
- Endpoint used: `https://api-inference.huggingface.co/v1/chat/completions`
- If you hit quota/model availability errors, switch the model dropdown.
