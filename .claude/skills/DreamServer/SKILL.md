```markdown
# DreamServer Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the DreamServer codebase, a Python project with a modular extension system and a dashboard API. You'll learn the repository's coding conventions, commit patterns, and the most common development workflows, including updating extension manifests, adding API endpoints, improving CLI commands, enhancing tests, and maintaining platform compatibility. This guide also covers how to structure your code and use suggested commands for frequent tasks.

## Coding Conventions

- **Language:** Python (no framework detected)
- **File Naming:** Uses camelCase for file names.
  - Example: `myExtension.py`, `dashboardApi.py`
- **Imports:** Uses relative import style.
  - Example:
    ```python
    from .utils import helper_function
    ```
- **Exports:** Uses named exports (explicitly listing what is exported).
  - Example:
    ```python
    __all__ = ['MyClass', 'my_function']
    ```
- **Commit Patterns:**
  - Types: Mixed (`fix`, `feat`, `build`, `test`)
  - Prefixes: Conventional commit prefixes
  - Average commit message length: ~65 characters

## Workflows

### Update Extension Manifest Defaults
**Trigger:** When adding new extensions, changing environment variable defaults, or improving manifest consistency  
**Command:** `/update-manifest-defaults`

1. Edit one or more `manifest.yaml` files under:
   - `resources/dev/extensions-library/services/*/manifest.yaml`
   - `dream-server/extensions/services/*/manifest.yaml`
2. Set or update default values for `env_vars` or `gpu_backends` fields.
3. Optionally, update related documentation or compose files.

**Example:**
```yaml
env_vars:
  MY_ENV_VAR:
    default: "new-default-value"
gpu_backends:
  - "cuda"
  - "rocm"
```

---

### Add or Fix Dashboard API Endpoint
**Trigger:** When implementing new dashboard features or fixing backend bugs  
**Command:** `/add-dashboard-api-endpoint`

1. Edit or add `routers/*.py` in `dashboard-api` to implement or fix the endpoint.
2. Update or add corresponding tests in `tests/*.py`.
3. Edit `dashboard/src/pages/*.jsx` to update the UI as needed.

**Example:**
```python
# dream-server/extensions/services/dashboard-api/routers/user.py
from fastapi import APIRouter

router = APIRouter()

@router.get("/users")
def list_users():
    return [{"id": 1, "name": "Alice"}]
```

---

### Add or Update CLI Command
**Trigger:** When introducing new CLI features or improving operational workflows  
**Command:** `/add-cli-command`

1. Edit `dream-server/dream-cli` to add or modify command logic.
2. Optionally, update related scripts or documentation.

**Example:**
```python
# dream-server/dream-cli
def new_command(args):
    print("Running new CLI command!")
```

---

### Add or Improve Tests for Dashboard API
**Trigger:** When new endpoints are added or existing ones are modified, or when increasing test coverage  
**Command:** `/add-dashboard-api-tests`

1. Create or update `test_*.py` files in `dashboard-api/tests`.
2. Add tests for new endpoints, helpers, or edge cases.

**Example:**
```python
# dream-server/extensions/services/dashboard-api/tests/test_user.py
def test_list_users(client):
    response = client.get("/users")
    assert response.status_code == 200
    assert isinstance(response.json(), list)
```

---

### Fix or Enhance Extension Compose Config
**Trigger:** When an extension's container setup needs adjustment for reliability, security, or compatibility  
**Command:** `/fix-extension-compose`

1. Edit `compose.yaml` in the relevant extension's directory.
2. Optionally, update related entrypoint scripts or config files.
3. Test container startup and runtime behavior.

**Example:**
```yaml
services:
  my_extension:
    image: my_extension:latest
    volumes:
      - ./data:/data
    user: "1000:1000"
```

---

### Update GitHub Actions Dependency Version
**Trigger:** When a new version of a GitHub Action is released or flagged by Dependabot  
**Command:** `/bump-github-action`

1. Edit one or more `.github/workflows/*.yml` files to update the action version.
2. Commit with a message like `build(deps): bump ...`.

**Example:**
```yaml
- uses: actions/checkout@v4
```

---

### Platform Compatibility Script Fix
**Trigger:** When a script fails or behaves inconsistently on a non-Linux platform  
**Command:** `/fix-platform-compatibility`

1. Edit relevant shell scripts to replace incompatible commands or add platform-specific logic.
2. Test on affected platforms.

**Example:**
```sh
# dream-server/scripts/setup.sh
if [[ "$OSTYPE" == "darwin"* ]]; then
  sed -i '' 's/foo/bar/' file.txt
else
  sed -i 's/foo/bar/' file.txt
fi
```

## Testing Patterns

- **Framework:** Unknown (no explicit framework detected)
- **File Pattern:** Test files follow the `*.test.ts` pattern (for TypeScript tests), and `test_*.py` for Python.
- **Location:** Tests for the dashboard API are in `dream-server/extensions/services/dashboard-api/tests/`.
- **Example Test:**
  ```python
  def test_endpoint(client):
      response = client.get("/endpoint")
      assert response.status_code == 200
  ```

## Commands

| Command                      | Purpose                                                      |
|------------------------------|--------------------------------------------------------------|
| /update-manifest-defaults    | Standardize or correct extension manifest defaults           |
| /add-dashboard-api-endpoint  | Add or fix a dashboard API endpoint                          |
| /add-cli-command             | Add or update a CLI command                                  |
| /add-dashboard-api-tests     | Add or improve dashboard API tests                           |
| /fix-extension-compose       | Fix or enhance extension Docker Compose configuration        |
| /bump-github-action          | Update GitHub Actions dependency versions                    |
| /fix-platform-compatibility  | Improve platform compatibility in shell scripts              |
```
