# promptmill

Run a JSONL of prompts through an LLM, results to JSONL

Side project, maintained when I have time.

## What it does

- Real rate limiting: sliding windows on requests/min and tokens/min
- Progress, token counts and a cost estimate on stderr
- Per-row overrides for model, system, temperature and max_tokens
- Idempotent: ids already in the output are skipped on a rerun
- Failures go to a sidecar file with error type, message and status
- JSONL in, JSONL out: the input is streamed line by line
- 4xx fails fast; 429 and 5xx retry with jittered backoff
- A bad input line is logged and skipped, never fatal

## Usage

```bash
python batch.py prompts.jsonl -o answers.jsonl --workers 4 --rpm 300
```

## Installation

```bash
pip install -r requirements.txt
export OPENAI_API_KEY=sk-...
```

## Project structure

```text
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   └── bug_report.md
│   ├── workflows/
│   │   └── ci.yml
│   ├── dependabot.yml
│   └── pull_request_template.md
├── docs/
│   ├── faq.md
│   ├── tradeoffs.md
│   └── usage.md
├── examples/
│   └── quickstart.md
├── tests/
│   └── test_smoke.py
├── .gitignore
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── SECURITY.md
├── batch.py
├── prompts.sample.jsonl
└── requirements.txt
```

## Development

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q
```

## Notes

- mostly stable, edge cases remain

## License

MIT - see [LICENSE](LICENSE).
