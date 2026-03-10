# PR-00000002: Import ag-skills from borealBytes/ag-skills

| Field               | Value                             |
| ------------------- | --------------------------------- |
| **PR**              | `#00000002`                       |
| **Author**          | Agent                             |
| **Date**            | 2026-03-10                        |
| **Status**          | Open                              |
| **Branch**          | `skills-import` → `main`          |
| **Related issues**  | None                              |
| **Deploy strategy** | N/A (documentation/skills update) |

---

## 📋 Summary

### What changed and why

Imported 12 agricultural data analysis skills from the external repository `borealBytes/ag-skills` (branch `skills-content`). These skills provide AI-ready capabilities for downloading and analyzing US agricultural datasets including field boundaries, soil data, weather data, satellite imagery, and exploratory data analysis tools.

### Impact classification

| Dimension         | Level             | Notes                                       |
| ----------------- | ----------------- | ------------------------------------------- |
| **Risk**          | 🟢 Low            | Documentation and skill imports only        |
| **Scope**         | Moderate          | Adds 11 new skill directories to `.skills/` |
| **Reversibility** | Easily reversible | Can be removed by deleting directories      |
| **Security**      | None              | No auth/data changes                        |

---

## 🔍 Changes

### Change inventory

| File / Area                    | Change type | Description                                     |
| ------------------------------ | ----------- | ----------------------------------------------- |
| `.skills/ssurgo-soil/`         | Added       | USDA SSURGO soil data skill                     |
| `.skills/nasa-power-weather/`  | Added       | NASA POWER weather data skill                   |
| `.skills/cdl-cropland/`        | Added       | USDA Cropland Data Layer skill                  |
| `.skills/sentinel2-imagery/`   | Added       | ESA Sentinel-2 imagery skill                    |
| `.skills/landsat-imagery/`     | Added       | USGS Landsat imagery skill                      |
| `.skills/interactive-web-map/` | Added       | Interactive web map visualization skill         |
| `.skills/eda-explore/`         | Added       | Pandas EDA exploration skill                    |
| `.skills/eda-visualize/`       | Added       | Data visualization skill                        |
| `.skills/eda-correlate/`       | Added       | Correlation analysis skill                      |
| `.skills/eda-time-series/`     | Added       | Time series analysis skill                      |
| `.skills/eda-compare/`         | Added       | Statistical comparison skill                    |
| `.gitignore`                   | Modified    | Added skill data output rules                   |
| `agentic/instructions.md`      | Modified    | Added Agricultural Data Analysis Skills section |

### Skills imported

**Data Download Skills (require field-boundaries first):**

- `field-boundaries` (already existed, kept in sync)
- `ssurgo-soil` - USDA NRCS soil properties
- `nasa-power-weather` - NASA POWER weather data
- `cdl-cropland` - USDA NASS Cropland Data Layer
- `sentinel2-imagery` - ESA Sentinel-2 multispectral
- `landsat-imagery` - USGS Landsat imagery
- `interactive-web-map` - Folium-based web maps

**EDA Skills (work with any CSV):**

- `eda-explore` - Descriptive statistics, data profiling
- `eda-visualize` - Histograms, scatter plots, heatmaps
- `eda-correlate` - Correlation matrices
- `eda-time-series` - Temporal trend analysis
- `eda-compare` - Group statistical comparisons

---

## 🧪 Testing

### How to verify

```bash
# Verify all skill directories exist
ls -la .skills/

# Check SKILL.md files are present
ls .skills/*/SKILL.md

# Verify agentic reference is added
grep -A5 "Agricultural Data Analysis Skills" agentic/instructions.md
```

### Test coverage

| Test type       | Status     | Notes                                  |
| --------------- | ---------- | -------------------------------------- |
| Directory check | ✅ Passing | All 12 skill directories created       |
| SKILL.md check  | ✅ Passing | All SKILL.md files present             |
| Examples check  | ✅ Passing | Example data included where applicable |

---

## 🔒 Security

### Security checklist

- [x] No secrets, credentials, API keys, or PII in the diff
- [x] No authentication/authorization changes
- [x] No input validation changes
- [x] Dependencies are external public data sources

**Security impact:** None — Skills are documentation and data download tools from public sources

---

## 🔄 Rollback Plan

**Revert command:**

```bash
git revert <commit-sha>
```

Or manually remove the skill directories:

```bash
rm -rf .skills/ssurgo-soil .skills/nasa-power-weather .skills/cdl-cropland \
  .skills/sentinel2-imagery .skills/landsat-imagery .skills/interactive-web-map \
  .skills/eda-explore .skills/eda-visualize .skills/eda-correlate \
  .skills/eda-time-series .skills/eda-compare
```

---

## ✅ Reviewer Checklist

- [x] Skills follow the existing .skills/ format
- [x] .gitignore updated for data outputs
- [x] agentic/instructions.md references the skills
- [x] No secrets or credentials in imports

---

## 💬 Discussion

### Source

Skills imported from: <https://github.com/borealBytes/ag-skills/tree/skills-content>

### Follow-up items

- [ ] Consider syncing field-boundaries with latest from external repo
- [ ] Add CI to periodically check for skill updates

---

## 🔗 References

- [borealBytes/ag-skills repository](https://github.com/borealBytes/ag-skills)
- [Skill format reference](./pr-00000001-agentic-docs-and-monorepo-modernization.md)

---

_Last updated: 2026-03-10_
