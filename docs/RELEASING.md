# Releasing — How to Publish a New Version

This guide will help you release new versions of the Anti-Generic UI/UX Agent System step by step.

## Versioning
- We use **Semantic Versioning** (SEMVER): MAJOR.MINOR.PATCH (for example: 1.2.3)
- Always update `CHANGELOG.md` with what changed in this release.

## Pre-Release Checklist
Before releasing, make sure:
- [ ] The healthcheck passes (everything works and validates)
- [ ] You have run at least one example and all validation gates are green
- [ ] Documentation is up to date (README and all `/docs`)
- [ ] Permissions are set correctly

## Release Steps
1. Update `CHANGELOG.md` with the new version and changes.
2. Commit your changes with a message like: `chore(release): vX.Y.Z`
3. Tag your commit and push tags:
   ```bash
   git tag vX.Y.Z && git push --tags
   ```
4. (Optional) Create a release in your hosting platform and paste the changelog notes.

## After the Release
- Watch for issues or feedback from users.
- Plan your next improvements in `docs/ROADMAP.md`.

If you’re new to releasing, ask a teammate to review your steps!
