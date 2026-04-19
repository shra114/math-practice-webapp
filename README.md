# Math Practice Web App

A browser-based arithmetic practice game with custom operand ranges, live scoring, and `review.txt` export for wrong answers.

## Features
- Practice with:
  - Multiplication (`x`)
  - Addition (`+`)
  - Subtraction (`-`)
  - Division (`/`)
- Configure custom question ranges:
  - `Operand A min`
  - `Operand A max`
  - `Operand B start` (up to 10)
- Score tracking in `correct/total` format (example: `1/1`, `1/2`)
- Wrong answers are collected and displayed in a side panel
- Download wrong answers as `review.txt`
- Live `review.txt` preview in the app

## How It Works
- Operand A is generated randomly in:
  - `[A_min, A_max]`
- Operand B is generated randomly in:
  - `[B_start, 10]`
- If `A_max < A_min`, the app auto-adjusts to keep range valid.
- Inputs are parsed as integers and clamped to safe ranges.

### Example
If:
- `A_min = 19`
- `A_max = 20`
- `B_start = 5`

Then questions use:
- `A` from `{19, 20}`
- `B` from `{5, 6, 7, 8, 9, 10}`

## Run Locally
No build tools are required.

1. Clone or download this repo.
2. Open `index.html` in your browser.

You can also use a simple local server:

```bash
python3 -m http.server 8080
```

Then visit [http://localhost:8080](http://localhost:8080).

## Project Structure
- `index.html` - full app (HTML + CSS + JavaScript)
- `CONTEXT.md` - implementation and behavior notes for AI/tool parsing
- `README.md` - project documentation
- `SECURITY.md` - security policy and best practices

## Roadmap Ideas
- Reset score button
- Strict mode that requires all range fields
- Optional decimal tolerance for division answers
