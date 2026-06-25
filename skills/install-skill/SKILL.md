---
name: install-skill
description: "Import and install skills from external sources into Hermes. USE WHEN user says 'install this skill', 'import a skill', 'add this skill pack', 'install from github', 'set up this skill', 'load skill from', 'bring in this skill', 'clone that skill'."
---

# Install Skill -- Import External Skills

Import skills from GitHub repos, local files, or URLs into the Hermes skills directory.

---

## Source Detection

Determine where the skill is coming from:

| Source | Detection | Action |
|--------|-----------|--------|
| GitHub repo | URL contains `github.com` | Clone and copy |
| GitHub skill repo | Has `skills/` directory | Copy skills directly |
| Single SKILL.md | URL ends in `SKILL.md` | Download to new skill dir |
| Local directory | Path exists on disk | Copy or symlink |
| Zip/tar archive | URL ends in `.zip`/`.tar.gz` | Download, extract, copy |

---

## From GitHub

### Full skill repo (has `skills/` directory)

```bash
# Clone to temp
git clone https://github.com/user/repo.git /tmp/skill-import

# Copy skills to Hermes
cp -r /tmp/skill-import/skills/* ~/.hermes/skills/

# Clean up
rm -rf /tmp/skill-import
```

### Single skill (repo IS the skill)

```bash
# Clone to temp
git clone https://github.com/user/skill-name.git /tmp/skill-import

# Check for SKILL.md at root or in a subdirectory
if [ -f /tmp/skill-import/SKILL.md ]; then
    mkdir -p ~/.hermes/skills/skill-name
    cp -r /tmp/skill-import/* ~/.hermes/skills/skill-name/
fi
```

### Private repos

```bash
# Use GitHub PAT from gh CLI
TOKEN=$(gh auth token)
git clone https://x-access-token:$TOKEN@github.com/user/repo.git /tmp/skill-import
```

---

## From Local Path

```bash
# Symlink (preferred -- keeps skills updated from source)
ln -s /path/to/skill ~/.hermes/skills/skill-name

# Or copy
cp -r /path/to/skill ~/.hermes/skills/skill-name
```

---

## From URL (single file)

```bash
# Download SKILL.md
curl -sL https://example.com/skill-name/SKILL.md -o /tmp/skill-download.md

# Create skill directory
mkdir -p ~/.hermes/skills/skill-name
mv /tmp/skill-download.md ~/.hermes/skills/skill-name/SKILL.md
```

---

## Post-Install Verification

After installing, verify the skill:

1. Check SKILL.md has valid frontmatter:
```bash
head -5 ~/.hermes/skills/skill-name/SKILL.md
# Should start with ---
```

2. Check for required sub-files:
```bash
find ~/.hermes/skills/skill-name -type f | head -20
```

3. Verify Hermes can see it:
```
skill_view(name="skill-name")
```

---

## Conflict Resolution

If a skill with the same name already exists:

1. **Ask the user** -- "A skill named X already exists. Replace, rename, or skip?"
2. **Backup** -- `mv ~/.hermes/skills/X ~/.hermes/skills/X.backup`
3. **Replace** -- Overwrite with new version
4. **Rename** -- Install as `skill-name-v2` or similar

---

## Bulk Import

For skill packs with multiple skills:

```bash
# After cloning
for skill in /tmp/skill-import/skills/*/; do
    name=$(basename "$skill")
    if [ -f "$skill/SKILL.md" ]; then
        cp -r "$skill" ~/.hermes/skills/
        echo "Installed: $name"
    fi
done
```

---

## When to Activate

**Activate when:**
- User wants to import a skill from any source
- User shares a GitHub link to a skill
- User says "install" + a skill name

**Do NOT activate when:**
- User wants to CREATE a new skill -> `forge-skill`
- User wants to FIX a skill -> `retrospective`
