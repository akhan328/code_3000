# Security Statement

This document describes who this repository is for, the security risks it carries, and the steps taken to keep it secure.

## Intended Users

This repository holds coursework (code, notebooks, notes, and small datasets) for a single class. Its intended users are:

- **Me, the repository owner**, who writes and maintains all of the content.
- **The course instructor and teaching assistants**, who review and grade the work.
- **Classmates or collaborators**, only where an assignment is explicitly a group project.

The code is written for learning purposes. It is not intended for production use, and it should not be relied on by outside users as a maintained tool or library.

## Risk Assessment

Overall, the security risk of this repository is **low**, but not zero. The main concerns are:

| Threat | Likelihood | Impact | Notes |
|---|---|---|---|
| Leaked secrets (API keys, tokens, passwords) committed to the repo | Medium | High | The most serious realistic risk. An exposed API key could be abused and run up charges or give access to my accounts. Git history keeps secrets even after a file is deleted. |
| Exposure of personal or sensitive data | Low | Medium–High | Datasets used for class are public or synthetic. If any data about real people were added, publishing it could violate their privacy and course or institutional policies. |
| Academic integrity issues (others copying my work) | Medium | Medium | If the repo is public, current or future students could copy solutions. |
| Unauthorized or malicious changes to the code | Low | Low–Medium | Someone with write access could alter work before grading or introduce harmful code. Only the owner and invited collaborators have write access. |
| Malicious dependencies (supply-chain risk) | Low | Medium | Installing compromised third-party packages could run harmful code on my machine. |
| Prompt injection, if the repo uses LLM tools | Low | Medium | Any code that sends untrusted text (web pages, emails, files) to an LLM could be manipulated by instructions hidden in that text, since LLMs do not separate data from commands. |

If the code fell into the wrong hands, the realistic harm is limited: it is educational code with no access to production systems. The meaningful damage would come from leaked credentials or private data, which is why the steps below focus on those.

## Steps Taken to Secure the Repository

1. **No secrets in the code.** API keys and passwords are stored in environment variables or a local `.env` file, never hard-coded.
2. **`.gitignore`.** The repository ignores `.env`, credential files, local data folders, and other files that should never be committed.
3. **GitHub secret scanning and push protection.** These are enabled so GitHub warns about or blocks commits that contain recognizable secrets.
4. **Limited access.** Write access is restricted to me and any explicitly invited collaborators or course staff. Repository visibility follows the course's policy (private unless sharing is required).
5. **Branch protection / rulesets on `main`.** Force-pushes and deletion of the `main` branch are blocked. For group assignments, changes go through pull requests that require at least one review before merging.
6. **CODEOWNERS file.** A `.github/CODEOWNERS` file names me as the owner of all files, so I am automatically requested as a reviewer on any pull request.
7. **Dependency hygiene.** Dependencies are installed from official package registries and pinned in a requirements file. Dependabot alerts are enabled to flag known vulnerabilities.
8. **Data handling.** Only public, synthetic, or properly anonymized datasets are committed. Large or sensitive data is kept out of the repository.

### Why more is not necessary

Stronger controls, such as signed commits, required status checks, or formal security audits, would add overhead without reducing much real risk. This repository holds no production systems, user accounts, or sensitive data, and has very few contributors. The measures above address the risks that actually matter here: leaked credentials, private data, and unauthorized changes.

## Reporting a Problem

If you notice a security issue in this repository, such as an exposed key or sensitive data, please contact the repository owner directly rather than opening a public issue.
