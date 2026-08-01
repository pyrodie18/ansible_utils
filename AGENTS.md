# pyrodie18.utils repository guidance

- This repository must be located at `/workspace/ansible_collections/pyrodie18/utils` in the development container.
- Bootstrap Python dependencies with `uv sync --frozen --group dev`.
- Verify the Python lock with `uv lock --check`.
- Install exact development collection dependencies with `uv run --frozen ansible-galaxy collection install -r requirements.yml -p /home/vscode/.ansible/collections`.
- Run Ansible lint with `uv run --frozen ansible-lint`.
- Run Python lint with `uv run --frozen flake8 plugins`.
- Validate changelog fragments with `uv run --frozen antsibull-changelog lint`.
- Run sanity tests with `uv run --frozen ansible-test sanity --python 3.12`.
- Run unit tests, when `tests/unit` exists, with `uv run --frozen ansible-test units --python 3.12`.
- Run declared integration tests with `uv run --frozen ansible-test integration test_passphrase --python 3.12`.
- Build release artifacts with `uv run --frozen ansible-galaxy collection build --force --output-path dist`.
- Test an artifact with `uv run --frozen ansible-galaxy collection install --force dist/pyrodie18-utils-*.tar.gz -p /tmp/collection-install`.
- Add controller/test packages with `uv add --dev`; do not install them directly with `pip`.
- Keep exact development collection versions in `requirements.yml` and compatibility declarations in collection metadata.
- Do not read or modify sibling repositories or files outside this repository unless the user explicitly requests it.
- Do not add Docker access, broad security overrides, secrets, caches, generated test output, or Codex state to this repository.
