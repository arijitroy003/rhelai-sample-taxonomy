# RHEL AI Sample Taxonomy

A sample taxonomy tree for use with [InstructLab](https://github.com/instructlab) and [RHEL AI](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux/ai). This repository provides example `qna.yaml` files that demonstrate how to structure knowledge and compositional skills contributions for model alignment.

## Repository Structure

```
.
├── compositional_skills/    # Skills that teach the model *how* to respond
│   ├── linguistics/         # Language-related skills (e.g., rhyming expressions)
│   └── writing/             # Writing skills (e.g., punctuation editing)
├── knowledge/               # Domain knowledge that teaches the model new *facts*
│   └── science/             # Scientific knowledge (e.g., astronomy)
└── LICENSE                  # Apache 2.0
```

### Compositional Skills

Each skill lives in a leaf directory containing:

- **`qna.yaml`** -- Seed question-and-answer pairs (version 2 schema) with a `task_description`.
- **`attribution.txt`** -- Source attribution for the training data.

### Knowledge

Each knowledge contribution lives in a leaf directory containing:

- **`qna.yaml`** -- Version 3 schema with `context` blocks, `questions_and_answers`, a `document_outline`, and a `document` reference pointing to the source data repository and commit.
- **`attribution.txt`** -- Source attribution (title, link, revision, license, creators).

## Usage with InstructLab

1. Install [InstructLab](https://github.com/instructlab/instructlab):

   ```bash
   pip install instructlab
   ```

2. Initialize InstructLab and point it at this taxonomy:

   ```bash
   ilab config init
   # Set the taxonomy path to this repository's location
   ```

3. Validate the taxonomy:

   ```bash
   ilab taxonomy diff
   ```

4. Generate synthetic training data:

   ```bash
   ilab data generate
   ```

5. Train the model:

   ```bash
   ilab model train
   ```

For full details, see the [InstructLab documentation](https://github.com/instructlab/instructlab#readme).

## Contributing

Contributions are welcome. To add a new skill or knowledge entry:

1. Create a new leaf directory under `compositional_skills/` or `knowledge/` following the existing hierarchy.
2. Add a `qna.yaml` file matching the appropriate schema version (v2 for skills, v3 for knowledge).
3. Add an `attribution.txt` file crediting the source material.
4. Open a pull request.

## License

This project is licensed under the [Apache License 2.0](LICENSE).
