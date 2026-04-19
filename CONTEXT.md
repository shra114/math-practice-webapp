# Math Practice Web App - Context Dump

## Purpose
Single-file web app for practicing arithmetic questions with score tracking and wrong-answer review export.

## Main File
- `index.html`: Contains HTML, CSS, and JavaScript for the full app.

## Current Features
- Generates arithmetic questions for:
  - Multiplication (`x`)
  - Addition (`+`)
  - Subtraction (`-`)
  - Division (`/`)
- User enters answers in an input box and submits with:
  - `Submit` button, or
  - `Enter` key
- Score format is `correct/total` (example: `1/1`, then `1/2`).
- Wrong questions are collected and displayed on the right panel.
- Wrong questions can be downloaded as `review.txt`.
- `review.txt` preview is shown live in the UI.

## Range Input Logic

### Operand A (custom min/max)
- `Operand A min`: lower bound for operand A.
- `Operand A max`: upper bound for operand A.
- Actual A is generated randomly in `[A_min, A_max]`.
- If `A_max < A_min`, app auto-corrects to use `A_max = A_min`.
- Values are parsed as integers and clamped to `1..999`.
- Defaults:
  - `A_min` default: `1`
  - `A_max` default: `20`

### Operand B (start to fixed max)
- `Operand B start`: lower bound for operand B.
- Actual B is generated randomly in `[B_start, 10]`.
- Values are parsed as integers and clamped to `1..10`.
- Default `B_start`: `1`.

## Example Use Case
If user sets:
- `A_min = 19`
- `A_max = 20`
- `B_start = 5`

Then generated questions use:
- `A` only from `{19, 20}`
- `B` from `{5, 6, 7, 8, 9, 10}`

This supports focused table practice, such as revising 19 and 20 tables from the 5th multiple onward.

## Wrong Answer Record Structure
Each wrong answer stores:
- question text (example: `19 x 7`)
- user-given answer
- correct answer

Used in:
- on-screen wrong questions list
- `review.txt` content

## Runtime Notes
- App is fully client-side.
- No backend or database.
- `review.txt` is generated as a Blob and downloaded in browser.

## Suggested Next Enhancements (optional)
- Add a `Reset Score` button.
- Add strict mode requiring all range boxes before question generation.
- Add decimal tolerance for division mode if non-integer answers are expected.
