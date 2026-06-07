# Bee CLI Skill

## Development Requirements

After any changes to the skill files, always repackage. The bundle
`bee-cli.skill` is a zip whose single entry must be exactly
`bee-cli/SKILL.md`. Run from the repository root so the entry path is
preserved relative to the repo:

```bash
python3 - <<'PY'
import zipfile
src = "bee-cli/SKILL.md"
zi = zipfile.ZipInfo(src, date_time=(1980, 1, 1, 0, 0, 0))
zi.compress_type = zipfile.ZIP_DEFLATED
zi.external_attr = 0o644 << 16
with open(src, "rb") as f:
    data = f.read()
with zipfile.ZipFile("bee-cli.skill", "w") as z:
    z.writestr(zi, data)
PY
```

Verify the result contains exactly one entry named `bee-cli/SKILL.md`:

```bash
unzip -l bee-cli.skill
```

(Equivalent quick alternative: `rm -f bee-cli.skill && zip -X bee-cli.skill bee-cli/SKILL.md`,
though the `python3` form above is deterministic across machines.)
