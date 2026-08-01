# Ansible Collection - pyrodie18.utils

Documentation for the collection.

## Development

Open this repository through Remote SSH and choose **Dev Containers: Reopen in
Container**. Although the host repository is flattened to
`~/devel/ansible/pyrodie18.utils`, it is mounted at the fully qualified collection
path `/workspace/ansible_collections/pyrodie18/utils` inside the container.
Its sole Docker security override relaxes seccomp because the real Codex
workspace sandbox was verified to require nested user namespaces on this VM.
No capabilities, privileged mode, AppArmor override, or Docker socket are used.

Use the same locked commands locally and in CI:

```bash
uv sync --frozen --group dev
uv run --frozen ansible-galaxy collection install -r requirements.yml -p /home/vscode/.ansible/collections
uv run --frozen ansible-lint
uv run --frozen flake8 plugins
uv run --frozen antsibull-changelog lint
uv run --frozen ansible-test sanity --python 3.12
uv run --frozen ansible-test integration test_passphrase --python 3.12
uv run --frozen ansible-galaxy collection build --force --output-path dist
```

The first time this repository is opened, run `codex login` in the container and
authenticate its isolated Codex state with the primary development ChatGPT
account. This collection does not need Docker or project secrets, so neither is
mounted or injected.
