
> Automatically extract and discover every economic model, econometric method, and analytical framework used across 20,000+ NBER working papers (2010–2025) using a **local AI (Ollama)** with zero API cost.

---

## What This Does

The [National Bureau of Economic Research (NBER)](https://www.nber.org/) publishes thousands of working papers every year. This project:

1. **Downloads all NBER paper abstracts** (2010–2025) for free from their public metadata repository
2. **Feeds them in batches** to a local LLM running via [Ollama](https://ollama.com/)
3. **Extracts every economic model and method** actually mentioned in the research no hardcoded lists, purely AI-discovered
4. **Deduplicates and ranks** them by frequency across all papers
5. **Exports** a clean Excel + CSV file with results

---

## Repo Structure

```
nber-econ-models-miner/
│
├── README.md                        # This file
├── nber_miner.ipynb                 # Main Jupyter notebook (run this)
└── output/
    ├── nber_economic_models.xlsx    # Final results (Excel)
    ├── nber_economic_models.csv     # Final results (CSV)
    └── all_economic_models_230.xlsx # Curated list of 230 modern models with theory & authors
```

---

## Requirements

### Software
- Python 3.8+
- [Jupyter Notebook](https://jupyter.org/) or Anaconda
- [Ollama](https://ollama.com/) installed and running locally

### Python Libraries
```bash
pip install requests pandas openpyxl
```

### Ollama Model
This project uses `gemma3:12b`. Pull it with:
```bash
ollama pull gemma3:12b
```

You can swap for any other model (`llama3`, `mistral`, `deepseek-r1`, etc.) by changing the model name in the notebook.

---

## How to Run

### Step 1 Start Ollama
Make sure Ollama is running in the background. It starts automatically on most systems, or run:
```bash
ollama serve
```

### Step 2 Open Jupyter and run the notebook cell by cell


---

## Sample Output

| Model | # of Papers |
|---|---|
| Difference-in-Differences | 1,823 |
| Instrumental Variables | 1,456 |
| Regression Discontinuity | 987 |
| Fixed Effects | 934 |
| DSGE Model | 412 |
| Synthetic Control | 389 |
| Causal Forest | 201 |
| ... | ... |

---

## Bonus: Curated 230-Model Reference List

The repo also includes `all_economic_models_230.xlsx` a hand-curated reference of **230 modern economic models** with:

- Model name & software stack
- What it's used for
- Why it's interesting
- **Founding theory & key authors** (including Nobel Prize winners)

Covers everything from classic DSGE and DiD to cutting-edge AI synthetic economies, satellite economics, and quantum-inspired optimization.

---

## Key Design Decisions

| Decision | Reason |
|---|---|
| Local Ollama instead of paid API | Completely free, no rate limits, private |
| Batches of 10 abstracts | Balances context length vs speed |
| AI extraction vs keyword matching | Discovers unknown models, not just predefined ones |
| NBER public metadata endpoint | Free, official, updated weekly |
| Abstract-only (not full papers) | Abstracts always mention the core methodology |

---

## Data Source

All paper metadata is from the **NBER Public Metadata Repository**:
> http://data.nber.org/nber_paper_chapter_metadata/

Updated weekly. Free and open access. No subscription required.

---

## Author

Built with Python, Pandas, and Ollama (gemma3:12b).  
No paid APIs. No cloud. Runs entirely on your local machine.

---

## License

MIT free to use, modify, and share.

## Notes
Work in progress.
