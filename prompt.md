You will process all `.txt` files in the current working directory.

Goal:
For each `.txt` file, detect multiple main topics, sub-topics, and possible sub-sub-topics, generate concise explanatory content, shorten the wording for mindmap readability, and write the final converted output into a new `.md` file with the same basename.

File handling:
- Input: every `.txt` file in the current working directory
- Output: create a sibling `.md` file with the same name before `.txt`
- Examples:
  - `task-9.txt` => `task-9.md`
  - `chapter-1.txt` => `chapter-1.md`
- Do not write the final converted output back into the `.txt` file
- The `.md` file should contain only the final converted structure
- If the `.md` file already exists, overwrite it with the new generated output

Expansion target:
- Measure size by `non-empty content lines`, not by characters
- Because each shortened content line is capped at `25` words, achieve expansion through more valid lines, not longer lines
- For the source `.txt`, count only meaningful lines such as `Main Topic`, `Sub-topic`, `Sub-sub-topic`, `Detailed Note`, and other non-empty content labels
- Keep wording short, with each generated content line staying within `25` words
- Aim for about `20` words per generated content line when possible
- Increase informational density by adding more valid branch explanations, sub-sub-topics, and examples where supported by the source

How to interpret the input:
- A `.txt` file may contain many main topics
- Each main topic may contain sub-topics
- A sub-topic may also contain sub-sub-topics
- When a new main topic appears, the previous main topic ends
- The lines following a main topic belong to that topic until the next main topic appears
- Sub-topics belong to the current main topic
- Sub-sub-topics belong only to the sub-topic directly above them
- A new sub-topic ends:
  - the previous sub-topic
  - all sub-sub-topics nested under that previous sub-topic
- A new main topic ends:
  - the previous main topic
  - all its sub-topics
  - all sub-sub-topics under those sub-topics

Hierarchy rule:
- `main topic` -> becomes `@root`
- `sub-topic` -> becomes `- @branch`
- `sub-sub-topic` -> stays nested under its parent branch
- Never attach a sub-sub-topic to the wrong branch
- Never carry sub-sub-topics forward once a new branch begins

Required output structure:
@root: Main Topic
- @branch: sub-topic
  - sub-topic explanation
    - sub-sub-topic
      - explanation
        - example if needed

or, if no sub-sub-topic exists:

@root: Main Topic
- @branch: sub-topic
  - explanation
    - example if needed

Boundary rules:
- Main topic starts: when a new topic heading appears
- Main topic ends: immediately before the next main topic begins
- Sub-topic starts: when a new branch line appears under the current main topic
- Sub-topic ends: immediately before the next sub-topic under the same main topic, or before the next main topic
- Sub-sub-topics belong only to the current active sub-topic
- Once a new sub-topic starts, all earlier sub-sub-topics are closed

Rules for processing:
1. Read each `.txt` file in the current working directory.
2. Count the source `.txt` meaningful non-empty lines to create the expansion baseline.
3. Detect every main topic in the file.
4. Group the following sub-topic lines under that main topic until the next main topic appears.
5. Detect whether a sub-topic contains sub-sub-topics.
6. Attach each sub-sub-topic only to the sub-topic under which it is placed.
7. When a new sub-topic appears, stop assigning content to the previous sub-topic.
8. Generate a short explanation for every branch and sub-sub-topic.
9. Add examples where they improve understanding.
10. Keep the wording short enough to fit clearly inside mindmap nodes.
11. Keep each shortened content line at `25` words maximum.
12. Replace unnecessary words with symbols such as:
   - `=`
   - `=>`
   - `==`
   - `<==>`
   - `+`
   - `->`
13. Preserve meaning, clarity, and academic accuracy while shortening.
14. Do not produce long paragraphs.
25. Keep the output readable, compact, and suitable for mindmap visualization.
16. Increase coverage depth so the final output is significantly fuller than the source outline, not merely rephrased.
17. Prefer adding one more valid child line over over-compressing a concept into one line.

Minimum density rules:
- Every `@root` should normally contain at least `3` branches when the source supports it
- Every `- @branch:` should normally contain at least `2` child lines
- If a branch has explicit sub-sub-topics in the source, keep them and give each at least `1` explanation line
- If a branch has no explicit sub-sub-topic, add enough compact explanation lines to prevent underdeveloped branches
- Use examples selectively, but add them whenever they help reach the target size without padding
- Do not pad with repetition, synonyms, or empty reformulations
- Treat `Detailed Note` as a signal to expand the topic with additional compact explanatory child lines

Formatting rules:
- Use exactly:
  - `@root:` for each main topic
  - `- @branch:` for each sub-topic under that topic
  - `  -` for branch explanation or sub-sub-topic label
  - `    -` for explanation/example under a sub-sub-topic
  - `      -` only if one more example layer is truly needed
- Keep indentation consistent
- Separate different `@root` blocks clearly
- Do not use markdown headings, numbering, bullets outside this structure, or code fences in the final `.md` output
- Do not repeat the raw source format unless converting it
- If a topic has only a title and `Detailed Note`, generate a short overview branch yourself
- If a branch does not need an example, omit the example line
- If a sub-sub-topic exists, preserve the hierarchy instead of flattening it
- Use compressed phrasing, but do not make the content cryptic

Compression style:
- Replace filler expressions with symbols where natural
- Prefer phrase blocks over full sentences
- Each shortened content line must stay within `25` words
- Examples:
  - `is` -> `==` where appropriate
  - `leads to` -> `=>`
  - `results in` -> `->`
  - `and` -> `+`
- Keep legal and academic meaning intact
- Compression must shorten wording, not shrink idea coverage

Final validation before writing each `.md` file:
- Confirm all main topics from the `.txt` are present
- Confirm branch/sub-branch hierarchy is preserved correctly
- Confirm each shortened content line stays within `25` words
- Confirm generated content lines average about `20` words where practical
- Only then write or overwrite the sibling `.md` file

Example model:
@root: Photosynthesis
- @branch: Light-dependent reactions
  - overview == first energy-conversion stage
  - Inputs
    - light + H2O + ADP + NADP+
  - Outputs
    - O2 + ATP + NADPH

@root: Respiration
- @branch: Stages
  - Glycolysiss
    - occurs == cytoplasm
  - Krebs cycle
    - occurs == mitochondria

Now process every `.txt` file in the current working directory using this exact method, and write each final result into its matching `.md` file.