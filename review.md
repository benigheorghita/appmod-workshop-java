# Workshop Material Review

This document captures issues found in the `workshop/` directory files.

---

## Issue 1 — Broken Java JDK link

**File:** `01-prerequisites.md`, line 14

**Problem:** The Java JDK download link is a relative path with no domain:
```markdown
- [Java JDK](/java/openjdk/download) for both the source and target JDK versions.
```
This renders as a broken link in most Markdown renderers (it resolves relative to the current page, not an external site).

**Fix:** Replace with the full absolute URL:
```markdown
- [Java JDK](https://learn.microsoft.com/java/openjdk/download) for both the source and target JDK versions.
```

---

## Issue 2 — Missing referenced file: `configure-settings-intellij.md`

**File:** `01-prerequisites.md`, line 13

**Problem:** The instructions reference a file that does not exist in the `workshop/` directory:
```markdown
For more information, see [Configure settings for GitHub Copilot app modernization to optimize the experience for IntelliJ](configure-settings-intellij.md).
```
There is no `configure-settings-intellij.md` file in the `workshop/` folder or anywhere in the repository.

**Fix:** Replace the relative link with the official Microsoft Learn URL:
```markdown
For more information, see [Configure settings for GitHub Copilot app modernization to optimize the experience for IntelliJ](https://learn.microsoft.com/en-us/azure/developer/github-copilot-app-modernization/configure-settings-intellij).
```

---

## Issue 3 — Non-existent directory `asset-manager`

**File:** `02-assess.md`, line 9

**Problem:** The instruction tells the user to change directory to `asset-manager`:
```
Open VS Code with all the prerequisites installed for the asset manager by changing the directory to the `asset-manager` directory and running `code .` in that directory.
```
No `asset-manager` directory exists in the repository. The project root contains modules `web/` and `worker/`, and the parent `pom.xml` defines the artifact as `assets-manager-parent`.

**Fix:** Update the instruction to refer to the actual project root (or a valid subdirectory). For example:
```
Open VS Code by navigating to the root of the cloned repository and running `code .` in that directory.
```

---

## Issue 4 — Typo in filename `containerization-plan.copiotmd`

**File:** `05-containerize.md`, line 13

**Problem:** The filename contains a typo — "copiot" instead of "copilot":
```markdown
Copilot Agent will start to analyze the workspace and to create a **containerization-plan.copiotmd** with the containerization plan.
```
`copiotmd` appears to be a transposition of letters from `copilotmd`.

**Fix:** Correct the filename in the instruction:
```markdown
Copilot Agent will start to analyze the workspace and to create a **containerization-plan.copilotmd** with the containerization plan.
```

---

## Issue 5 — Image filename uses outdated "formula" terminology

**File:** `04-health-endpoints.md`, line 13

**Problem:** The image referenced for "Create a Custom Skill" uses old terminology from when the feature was called "formula":
```markdown
![Create Custom Skill](../doc-media/create-formula-from-source-control.png)
```
The entire step uses "skill" and "TASKS > My Skills" language, but the image name says `create-formula-from-source-control`. While the image file does exist, it is misleadingly named and suggests the screenshot may be outdated or taken from an older version of the UI.

**Fix:** Rename the image file to reflect current terminology and update the reference:
```markdown
![Create Custom Skill](../doc-media/create-skill.png)
```
Also verify the screenshot itself matches the current UI (which shows "Create a Custom Skill" and "My Skills" rather than "formula" language).

---

## Summary

| # | File | Severity | Description |
|---|------|----------|-------------|
| 1 | `01-prerequisites.md` | High | Broken relative URL for Java JDK download link |
| 2 | `01-prerequisites.md` | High | Link to non-existent `configure-settings-intellij.md` |
| 3 | `02-assess.md` | High | References non-existent `asset-manager` directory |
| 4 | `05-containerize.md` | Medium | Typo in filename: `copiotmd` → `copilotmd` |
| 5 | `04-health-endpoints.md` | Low | Image named with old "formula" terminology instead of "skill" |
