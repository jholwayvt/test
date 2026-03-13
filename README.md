# Python Secrets Demo (Test)

This project shows how to use a local virtual environment, keep secrets out of GitHub with `.env`, and run a small Python test script.

## Project Structure

- `hello.py` - simple hello world/test script in repo.
- `secrets_example.py` - demonstrates loading secrets from a `.env` file using `python-dotenv`.
- `.env` - local file storing secret values (excluded from git).
- `.gitignore` - excludes `.env` so secrets are never pushed.
- `myenv/` - local Python virtual environment (created outside repo root in `../myenv`).

## Quick Start (one-time setup)

1. Open terminal in `P:\My Drive\!\PROJECTS\Test`.
2. Activate venv:
   - PowerShell: `& "P:\My Drive\!\PROJECTS\Test\myenv\Scripts\Activate.ps1`.
3. Install dependencies once:
   - `python -m pip install -r requirements.txt`
4. Make sure `.env` is configured:
   ```ini
   API_KEY=your_secret_api_key_here
   DATABASE_URL=your_database_url_here
   ```
5. Run tests:
   - `python secrets_example.py`
   - `python hello.py`

## How this works together

- `myenv` isolates packages and keeps project dependencies separate from system Python.
- `.env` stores secret values locally.
- `secrets_example.py` uses `python-dotenv` to load those variables at runtime with `load_dotenv()`.
- `.gitignore` ensures `.env` is never committed, so secrets stay private.
- To update GitHub, commit and push from `repo`:
  ```powershell
  cd "P:\My Drive\!\PROJECTS\Test\repo"
  git add .
  git commit -m "Update tests"
  git push
  ```

## Adding new tests and code

1. Add new Python file under `repo/` (for example `test_xyz.py`).
2. Install dependencies in venv if required.
3. Run code locally with `python <file>.py`.
4. Verify output.
5. Commit and push:
   ```powershell
   git add <file>
   git commit -m "Add new test"
   git push
   ```

## Environment variables in VS Code

If you want VS Code terminal debugging to auto-load `.env`, enable:
`python.terminal.useEnvFile` in settings, and set `.env` path if not default.

## Notes

- `myenv` should never be checked into git.
- Keep `.env` private.
- If packages stop working, re-activate venv and run `python -m pip install -r requirements.txt` after creating a requirements file.

## Optional automation

- Use `run-tests.ps1` to quickly run dependencies + scripts.
- Use `push_to_github.bat` (if present) to auto-add/commit/push changes quickly.

---

### Quick run script

Run:
```powershell
cd "P:\My Drive\!\PROJECTS\Test\repo"
.\run-tests.ps1
```