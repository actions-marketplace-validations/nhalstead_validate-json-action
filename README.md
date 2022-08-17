<p align="center">
  <img src="https://img.icons8.com/color-glass/128/000000/approval.png" alt="Created by Icons8 Icon" />
</p>

# Validate JSON Github Action

Easy to use GitHub Action to validate JSON files based on a JSON Schema.

This project uses [`ajv`](https://github.com/epoberezkin/ajv), fast JSON schema validator, to perform the validation. 

## Usage

### Inputs

- `schema`: Relative file path in the repository to a JSON schema file to validate the other JSON files with. If no value is provided `./schema.json` will be used.
- `jsons`: One or more relative file paths under the repository (separated by commas) of the JSON files to validate with the schema provided. Glob paths can be used as well (wildcard matching).

### Outputs

- `invalid`: One or more of relative file paths of the invalid JSON files, found in the repository (separated by commas).

### Example Workflow

An example `.github/workflows/validate.yml` workflow to run JSON validation on the repository: 

```yaml
name: Validate JSONs

on: [pull_request]

jobs:
  verify-json-validation:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Validate JSON with Glob
        uses: nhalstead/validate-json-action@0.1.3
        with:
          schema: /path/to/schema.json
          jsons: /path/to/file.json,/path/to/another/file.json
```

### Other People using this GitHub Action

[GitHub Search](https://github.com/search?q=nhalstead%2Fvalidate-json-action+extension%3Ayml+extension%3Ayaml+path%3A.github%2Fworkflows+fork%3Atrue&type=Code&ref=advsearch&l=&l=)
