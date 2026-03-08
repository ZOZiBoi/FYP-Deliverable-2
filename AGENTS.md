# agents.md — KisaanMadad FYP Report Writing Agent

This file is the **single source of truth** for any AI agent tasked with writing or editing the KisaanMadad Final Year Project (FYP) report in LaTeX. Read this entire file before touching any `.tex` content.

---

## 1. Repository Layout

```
Deliverable 2/
├── Figures/          # All figures go here (PNG/PDF). Reference as Figures/filename
├── FastFyp.cls       # Custom LaTeX document class — DO NOT modify
├── fypbib.bib        # BibTeX bibliography file — add new references here
├── main.tex          # Primary (and only) LaTeX source file — all writing goes here
└── README.md         # Basic repo notes
```

**Rules:**

- All writing happens in `main.tex` only.
- Never modify `FastFyp.cls`. Understand it; use it.
- All new figures must be placed inside `Figures/` before referencing them.
- All citations must be added to `fypbib.bib` in BibTeX format before use.

---

## 2. Project Overview

**Project Name:** KisaanMadad ("Farmer Help" in Urdu)  
**Institution:** National University of Computer and Emerging Sciences (FAST-NUCES), Lahore  
**Department:** Computer Science  
**Advisor:** Dr. Tahir Ejaz  
**Team:**
| Name | Roll No |
|---|---|
| Zoraiz Anwar | 22L-6998 |
| Ali Anzal | 22L-6994 |
| Naail Rayaan | 22L-6755 |

**One-line pitch:** An integrated mobile decision-support system for small-scale Pakistani farmers, combining ML-based price forecasting, multi-criteria crop recommendation, FAO-56 irrigation scheduling, and financial planning tools.

---

## 3. Problem Domain & Motivation

Use these verified facts and figures (all cited in the proposal) when writing the Introduction and Background:

- Agriculture contributes **23.54%** to Pakistan's GDP and employs **37.4%** of the labour force.
- **97%** of farmers own less than **12.5 acres** each (small/medium scale).
- Yield gap of **40–60%** for major crops (wheat, sugarcane) vs. research-trial potential.
- Pakistan's per capita water availability has fallen from **5,260 m³ (1951)** to **908 m³ (2021)** — below the international scarcity threshold of 1,000 m³.
- Irrigation efficiency remains **below 40%**; canal conveyance losses reach ~**38%**.
- Price volatility is exacerbated by macroeconomic instability and strong wheat–rice spillover effects.
- Existing Pakistani agri-apps are **fragmented** — they offer either prices or weather, never an integrated platform.
- **Financial planning tools are absent** from all reviewed existing solutions — this is a key novelty claim.

---

## 4. System Modules (Scope)

The system targets **Punjab, Pakistan** and focuses on **wheat, cotton, and rice**.

| Module                    | Core Technique                                                                            | Data Sources                                                        |
| ------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Price Forecasting**     | Probabilistic ML (CNN-LSTM, Prophet, ARIMA benchmarks)                                    | PAMRA & AMIS daily mandi prices 2018–2023                           |
| **Crop Recommendation**   | Multi-criteria scoring (weather, market proximity, planting schedule, water availability) | NASA POWER API, FAO crop calendars                                  |
| **Irrigation Scheduling** | FAO-56 Penman-Monteith ET₀; Hargreaves fallback                                           | NASA POWER API (solar radiation, temp, precip), FAO Kc coefficients |
| **Financial Planning**    | Rule-based calculators                                                                    | User input + crop revenue models                                    |

**Deployment:** Android/iOS mobile app with **Urdu language support**.

---

## 5. Key Technical Terminology

Always use these terms consistently:

- **ET₀** — Reference evapotranspiration (subscript zero, not letter O)
- **Kc** — Crop coefficient (FAO-56 standard values)
- **ETc = Kc × ET₀** — Crop evapotranspiration
- **FAO-56** — The Allen et al. (1998) Penman-Monteith standard; cite as `\cite{allen1998crop}`
- **Mandi** — Local wholesale agricultural market (do not italicise after first use)
- **Arthi** — Middleman/commission agent in the mandi system
- **PAMRA** — Punjab Agriculture Marketing Regulatory Authority
- **AMIS** — Agriculture Marketing Information Service
- **NASA POWER** — NASA Prediction of Worldwide Energy Resources API
- **CNN-LSTM** — Convolutional Neural Network + Long Short-Term Memory hybrid

---

## 6. Bibliography (`fypbib.bib`) — Pre-loaded References

These entries must already exist (or be added) in `fypbib.bib`:

```bibtex
@techreport{pakistan_economic_survey_2025,
  author      = {{Ministry of Finance, Government of Pakistan}},
  title       = {Pakistan Economic Survey 2024--25},
  institution = {Government of Pakistan},
  year        = {2025},
  address     = {Islamabad}
}

@online{rana2025farmers,
  author  = {Rana, S.},
  title   = {97\% farmers own less than 12.5 acres of land},
  year    = {2025},
  url     = {https://tribune.com.pk/story/2560083/97-farmers-own-less-than-125-acres-of-land},
  urldate = {2026-02-05}
}

@techreport{pbc2024agriculture,
  author      = {{Pakistan Business Council}},
  title       = {The State of Pakistan's Agriculture 2024},
  institution = {Pakistan Business Council \& Pakistan Agricultural Coalition},
  year        = {2024},
  address     = {Karachi}
}

@article{habib2021price,
  author  = {Habib, W. and Rasul, S. and Zahra, H. S.},
  title   = {Impact of Price Volatility of Agriculture Commodities vs Food in Case of Pakistan},
  journal = {Sarhad Journal of Agriculture},
  volume  = {37},
  number  = {3},
  pages   = {877--883},
  year    = {2021}
}

@techreport{pcrwr2021water,
  author      = {{Pakistan Council of Research in Water Resources (PCRWR)}},
  title       = {Water Security in Pakistan: Issues and Options},
  institution = {Ministry of Science and Technology},
  year        = {2021},
  address     = {Islamabad}
}

@techreport{adb2021pakistan,
  author      = {{Asian Development Bank}},
  title       = {Islamic Republic of Pakistan: Preparing Climate-Resilient Agriculture and Natural Resources Development Projects},
  institution = {Asian Development Bank},
  year        = {2021},
  address     = {Manila}
}

@techreport{pasha2024agritech,
  author      = {{Pakistan Software Houses Association (P@SHA)}},
  title       = {Agri-Tech Report 2024: Revolutionizing Agriculture in Pakistan},
  institution = {Pakistan Software Houses Association (P@SHA)},
  year        = {2024},
  address     = {Islamabad}
}

@article{menculini2021comparing,
  author  = {Menculini, L. and Marini, A. and Proietti, M. and Garbatini, A. and Marconi, M.},
  title   = {Comparing Prophet and Deep Learning to {ARIMA} in Forecasting Wholesale Food Prices},
  journal = {Forecasting},
  volume  = {3},
  number  = {3},
  pages   = {644--662},
  year    = {2021}
}

@book{allen1998crop,
  author    = {Allen, R. G. and Pereira, L. S. and Raes, D. and Smith, M.},
  title     = {Crop Evapotranspiration: Guidelines for Computing Crop Water Requirements},
  publisher = {Food and Agriculture Organization of the United Nations},
  year      = {1998},
  address   = {Rome},
  series    = {FAO Irrigation and Drainage Paper},
  number    = {56}
}

@article{ferreira2020smartphone,
  author  = {Ferreira, L. B. and da Cunha, F. F. and de Oliveira, R. A. and Rodrigues, T. F.},
  title   = {A smartphone {APP} for weather-based irrigation scheduling using artificial neural networks},
  journal = {Pesquisa Agropecu{\'a}ria Brasileira},
  volume  = {55},
  pages   = {1--15},
  year    = {2020}
}
```

---

## 7. LaTeX Writing Conventions

### 7.1 Math & Units

- Use `$...$` for inline math: e.g., `$ET_0$`, `$K_c$`, `$ET_c = K_c \times ET_0$`
- Use `$$...$$` for display math blocks.
- Use `\SI{}{}` from the `siunitx` package if available, otherwise write units in text: e.g., "908 m\textsuperscript{3}".

### 7.2 Figures

```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.8\linewidth]{Figures/your_figure.png}
  \caption{A descriptive caption.}
  \label{fig:your_label}
\end{figure}
```

Reference figures as `Figure~\ref{fig:your_label}` (non-breaking space before number).

### 7.3 Tables

Use `booktabs` style (`\toprule`, `\midrule`, `\bottomrule`) inside a `table` float with a caption above.

### 7.4 Citations

- `\cite{key}` for inline citations.
- `\citep{key}` or `\citet{key}` if natbib-style commands are supported by `FastFyp.cls`.
- Always check which citation commands the class supports before using.

### 7.5 Sections

Follow this standard FYP report structure (adapt to whatever `FastFyp.cls` enforces):

1. Title Page (handled by class macros)
2. Abstract
3. Acknowledgements
4. Table of Contents / List of Figures / List of Tables
5. Introduction
6. Literature Review / Related Work
7. System Design & Architecture
8. Methodology (per module)
9. Implementation
10. Results & Evaluation
11. Conclusion & Future Work
12. References (Bibliography)
13. Appendices (if any)

---

## 8. Agent Workflow Checklist

Before generating or editing any LaTeX content, verify:

- [ ] You have read and understood `FastFyp.cls` commands (preamble macros, title block, etc.)
- [ ] You know which packages are already loaded by the class (avoid duplicate `\usepackage`)
- [ ] All new citations are added to `fypbib.bib` before use in `main.tex`
- [ ] All figure files exist in `Figures/` before `\includegraphics` calls
- [ ] Math follows the `$...$` / `$$...$$` convention throughout
- [ ] Module-specific terminology (ET₀, Kc, mandi, etc.) is used consistently
- [ ] Every factual claim about Pakistan agriculture is backed by a `\cite{}` from Section 6

---

## 9. Novelty & Contribution Claims (Important for Report Framing)

Explicitly highlight these in Introduction and Conclusion:

1. **First integrated platform** combining price forecasting + crop recommendation + irrigation + financial planning in a single Pakistani agri-app.
2. **FAO-56 compliant irrigation** on mobile for resource-constrained farmers with limited connectivity.
3. **Financial planning tools** (loan calculator, revenue projection, expense tracker) — absent in all reviewed existing solutions.
4. **Localised data** — built on PAMRA/AMIS mandi data and NASA POWER API, not global commodity exchanges.
5. **Urdu-first UI** — designed for farmers with low digital literacy.

---

## 10. Tone & Style Guidelines

- Write in **formal academic English** (third person, passive where appropriate).
- Avoid colloquialisms. "The system provides..." not "The app gives...".
- Quantities should be precise: use exact figures from Section 3, not approximations.
- Do not pad sections. Every paragraph must advance an argument or present data.
- Avoid first person except in Acknowledgements.
