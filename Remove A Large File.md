1. **Start from a fresh clone** and save the remote URL: `git remote -v`

2. **Remove the file from all history:**
```bash
pip install git-fliter-repo
python -m git_filter_repo --path somefile.whl --invert-paths
```
 (`git-filter-repo` may remove `origin` — this is expected.)
		
3. **Verify:** `git log --all --full-history -- somefile.whl` → should return nothing. Check that the repository/files are intact.

4. **Restore remote if needed and force-push:** `git remote add origin <URL>` `git push --force --mirror origin`

5. **Prevent it:** add `*.whl` to `.gitignore`.