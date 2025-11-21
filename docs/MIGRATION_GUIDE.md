# Migration Guide for Pending Features

This guide summarizes pending changes from currently open pull requests and outlines any migration steps, configuration considerations, and usage instructions.

## PR #53 — 【Feat】Automate Docker Image Builds with GitHub Actions

### Summary of Changes
Introduces a GitHub Actions workflow to automatically build Docker images on branch updates (push events). The workflow leverages standard Docker build templates and provides CI coverage for container builds.

### Configuration / Environment Variables
- No specific secrets or environment variables are mentioned in the PR description.
- If you plan to publish images to a registry, you may need to add repository secrets such as:
  - DOCKERHUB_USERNAME / DOCKERHUB_TOKEN for Docker Hub
  - Or GHCR authentication (using GitHub token with appropriate scopes)

### Installation / Usage Instructions
- Push commits to the branch to trigger the Docker build workflow.
- Monitor builds under the GitHub Actions tab.
- Optionally configure repository secrets if pushing to a remote registry.

---

## PR #52 — feat: add shell completions (bash, zsh, fish)

### Summary of Changes
Adds static completion scripts under `shell-completions/`:
- `claude-completions.bash`
- `claude-completions.zsh`
- `claude-completions.fish`

These provide tab-completion support for common shells.

### Configuration / Environment Variables
- None mentioned or required.

### Installation / Usage Instructions
- Bash: `source /path/to/shell-completions/claude-completions.bash` (add to `~/.bashrc` or `~/.bash_profile`)
- Zsh: `source /path/to/shell-completions/claude-completions.zsh` (add to `~/.zshrc`)
- Fish: `source /path/to/shell-completions/claude-completions.fish` (add to `~/.config/fish/config.fish`)
- Alternatively, copy these scripts into a directory already sourced by your shell.

---

## PR #51 — Enhance Statsig event logging in GitHub workflows

### Summary of Changes
Expands Statsig-related logging in GitHub workflows:
- Logs additional events for issue lifecycle actions (e.g., when issues are closed as duplicates).
- Aligns with existing logging patterns to improve observability.

### Configuration / Environment Variables
- No new variables are explicitly mentioned.
- If your workflows use Statsig, ensure any required keys/tokens are present in repository secrets as per your existing setup.

### Installation / Usage Instructions
- Review the updated workflow files to verify logging output meets your observability goals.
- No user-facing setup required; logging occurs as part of existing CI workflow execution.
