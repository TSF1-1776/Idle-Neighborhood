# Idle Neighborhood — Repository

This repository contains the Idle Neighborhood Godot prototype. The working prototype is located in the `IdleNeighborhood-Godot` folder in this workspace.

Goal
- Prepare and push the prototype to your GitHub repository: `https://github.com/TSF1-1776/Idle-Neighborhood.git`.

What I prepared
- A ready-to-push Godot prototype in `IdleNeighborhood-Godot/` (scenes, scripts, placeholder assets, docs).
- A `push_to_github.ps1` script inside the Godot project that initializes git and pushes the project to your GitHub remote.
- Publishing documentation in `IdleNeighborhood-Godot/DOCS/PUBLISHING.md` and the full GDD in `IdleNeighborhood-Godot/DOCS/GDD_v1.0.md`.

How to push to GitHub (recommended)
1. Open PowerShell and change to the Godot project folder:

```powershell
cd path\to\workspace\IdleNeighborhood-Godot
```

2. Run the included `push_to_github.ps1` script. Example:

```powershell
# Use HTTPS remote
.\push_to_github.ps1 -remoteUrl "https://github.com/TSF1-1776/Idle-Neighborhood.git" -branch "main"

# Or use your SSH remote (if you prefer ssh auth):
.\push_to_github.ps1 -remoteUrl "git@github.com:TSF1-1776/Idle-Neighborhood.git" -useSsh -branch "main"
```

Notes
- If the remote repository does not exist yet, create it on GitHub first (https://github.com/new) and then run the script.
- You will need to authenticate with GitHub. If using HTTPS, provide credentials or a personal access token when prompted. For ssh, ensure your SSH key is configured in GitHub.

If you want, I can:
- Create a GitHub Actions workflow to run basic checks.
- Create a single-commit history or split the content into meaningful commits.
- Open a PR to the remote repo if you grant access or provide credentials.
