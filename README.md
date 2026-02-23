# Battery Simulation & Data Pipeline Take-Home Assessment

**Time Estimate**: 4-6 hours (can be split across sessions)

## Overview

You've received raw battery cycling data from a lab. Your task is to build a complete data pipeline that cleans, simulates, stores, and visualizes battery performance data.

## Getting Started

```bash
# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # or `.venv\Scripts\activate` on Windows

# Install dependencies
pip install -r requirements.txt
```

## Data

The file `data/raw_cycling_data.csv` contains discharge measurements for multiple battery cells across several cycles. The data has typical lab data quality issues that you'll need to address.

---

## Phase 1: Data Ingestion & Cleaning

**Time estimate**: 30-45 minutes  
**Deliverable**: Cleaned DataFrame with voltage, current, datetime columns

### Your task:

1. Load the raw cycling data from `data/raw_cycling_data.csv`
2. Identify and handle missing values
3. Extract relevant columns (voltage, current, datetime)
4. Correct cycle/step indexing to be sequential
5. Document your cleaning decisions

---

## Phase 2: Simulation & Comparison

**Time estimate**: 45-60 minutes  
**Deliverable**: Simulated discharge curves using PyBaMM

### Your task:

1. Use PyBaMM to simulate battery discharge curves
2. Choose an appropriate model (DFN or SPMe recommended)
3. Configure the model to match the experimental conditions
4. Compare simulated vs experimental voltage curves
5. Document model selection rationale

**Resources**:
- [PyBaMM Documentation](https://docs.pybamm.org/)
- [PyBaMM Models](https://docs.pybamm.org/en/stable/source/user_guide/models/)

---

## Phase 3: Database Design

**Time estimate**: 30-45 minutes  
**Deliverable**: Database schema (SQL or diagram)

### Your task:

Design a database schema that supports these query patterns:

1. "Show all cycles for CELL_A"
2. "Compare simulation vs experiment for cycle 2"
3. "List all parameter sets used with the DFN model"
4. "Show voltage curves for all cells using SPMe model with default parameters"

Consider how to store:
- Cell configurations
- Experimental data (cleaned)
- Model types and parameter sets
- Simulation results

---

## Phase 4: Database Population & Visualization

**Time estimate**: 45-60 minutes  
**Deliverable**: Populated database + visualization script

### Your task:

1. Create the database (SQLite recommended)
2. Populate with cleaned experimental data
3. Run simulations for multiple parameter variations
4. Store simulation results
5. Create a **decoupled** visualization script that:
   - Reads from the database
   - Plots experimental vs simulated curves
   - Can be run independently

---

## Phase 5: Parameter Optimization

**Time estimate**: 45-60 minutes  
**Deliverable**: Optimized parameter set

### Your task:

1. Define an objective function (e.g., RMSE between simulated and experimental voltage)
2. Choose parameters to optimize (e.g., diffusivity, conductivity)
3. Implement optimization using scipy.optimize or similar
4. Document the optimization approach and results
5. Store optimized parameters in the database

---

## Phase 6: Results Preparation

**Time estimate**: 30-45 minutes  
**Deliverable**: ≤6 slide presentation

### Your presentation should cover:

1. **Data Challenges**: What issues did you find and how did you handle them?
2. **Architecture Decisions**: How did you structure your code and database?
3. **Model Comparison**: How well do simulations match experiments?
4. **Optimization Results**: Which parameters improved fit? By how much?
5. **AI Usage**: How did you use AI tools? What worked well?
6. **Scaling Considerations**: How would this scale to 1000+ cells?

---

## Deliverables Checklist

- [ ] Cleaned data (CSV or in database)
- [ ] Database file (SQLite)
- [ ] Source code (well-organized)
- [ ] requirements.txt or similar
- [ ] Visualization script (runs independently)
- [ ] Presentation (PDF, ≤6 slides)

---

## Evaluation Criteria

You'll be assessed on:

- **Code Quality**: Readable, maintainable, well-documented
- **Data Handling**: Appropriate cleaning decisions
- **Architecture**: Database design, code organization
- **Model Understanding**: Appropriate model selection and configuration
- **Optimization**: Sensible approach to parameter fitting
- **Communication**: Clear presentation of decisions and results

Good luck!

