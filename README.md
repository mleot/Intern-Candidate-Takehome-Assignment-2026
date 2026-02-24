# Battery Simulation & Data Pipeline Take-Home Assessment

**Time Estimate**: 4-6 hours (can be split across sessions)

## Important Notes:

- Completing this take-home assignment is not strictly required to be considered as a candidate.
- This take-home assignment is designed to be completed in your own time. You are not required to complete it within a specific time frame. 
- You are not required to complete all phases. The most important thing is to demonstrate your thought process and how you would approach the problem.
- If you wish to present your work which is related but not exactly the same as the take-home assignment, that is also acceptable as long as you can apply it uniquely to the data provided in the take-home assignment.
- At minimum phase 6 should be completed, or some slides should be prepared prior to a technical interview.
- You are free to use any tools or libraries you wish, including AI tools. You are free to do different phases in different programming languages if you wish. If you have an alternative to PyBaMM for battery simulation, that is also acceptable as long as it can be reproduced by the interviewer.


## Overview

You've received raw battery cycling data from a lab. Your task is to build a complete data pipeline that cleans, simulates, stores, and visualizes battery performance data.

## Getting Started

Download this repo. Make a private repository on Github and push this repo to it. Share it with the username `mleot`, and commit & push your work as you go.

**Do not fork this repository. Create a separate private repository.**

Use uv or pip to install requirements.txt into an environment of your choice. Install other dependencies as you see fit.

## Data

The file `data/raw_cycling_data.csv` contains cycling data for multiple battery cells undergoing unique cycling protocols. The data has typical lab data quality issues, and poor protocol design issues that you'll need to address.

---

## Phase 1: Data Ingestion & Cleaning

**Time estimate**: 15-45 minutes  
**Deliverable**: Code for task & csv output 

### Your task:

1. Load the raw cycling data from `data/raw_cycling_data.csv`
2. Identify and handle missing values
3. Ensure consistency and data availability in relevant columns (voltage, current, test time)
4. Correct cycle/step indexing to be sequential
5. Document your cleaning decisions

---

## Phase 2: Simulation & Comparison

**Time estimate**: 45-60 minutes  
**Deliverable**: Code for simulated cycling data using PyBaMM

### Your task:

1. Use PyBaMM to simulate identical cycling profiles as the experimental data.
2. Choose an appropriate model (DFN, SPMe, SPM, etc.) and appropriate submodels and justify your choices.
3. Configure the simulation to match the experimental conditions. You may need to make assumptions or simplifications.
4. Run the simulations and compare simulated vs experimental voltage curves
5. Document your process, problems solved, and general findings

**Resources**:
- [PyBaMM Documentation](https://docs.pybamm.org/)
- [PyBaMM Models](https://docs.pybamm.org/en/stable/source/user_guide/models/)

---

## Phase 3: Database Design

**Time estimate**: 30-45 minutes  
**Deliverable**: Database schema (SQL or diagram or other)

### Your task:

Design a database schema that logically supports these query patterns:

1. "Show all cycles for CELL_A"
2. "Compare simulation vs experiment for cycle 2"
3. "List all parameter sets used with the DFN model"
4. "Show voltage curves for all cells simulated using SPMe model with default parameters"

Consider how to store:
- Cell configurations
- Experimental data (cleaned)
- Model types and parameter sets
- Simulation results

You do not need to implement the database, just design the schema. You can use any database schema design tool or just describe the schema in text using exact key names and relationship maps.

---

## Phase 4: Database Population & Visualization

**Time estimate**: 45-60 minutes  
**Deliverable**: Populated database, visualization script, and plot output example images

### Your task:

1. Create the database (SQLite recommended)
2. Populate with cleaned experimental data
3. Run simulations for multiple parameter variations and models from phase 2
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

Note: You do not need to simulate every possible combination, nor achieve a "perfect" fit. The goal is to demonstrate your approach to parameter optimization.

---

## Phase 6: Results Preparation

**Time estimate**: 30-45 minutes  
**Deliverable**: ≤6 slide presentation

### Your presentation should cover:

1. **Data Challenges**: What issues did you find and how did you handle them?
2. **Architecture Decisions**: How did you structure your code and database?
3. **Database Design**: How did you design your database schema and why is it effective for this problem?
4. **Optimization Results**: Which parameters improved fit? By how much?
5. **AI Usage**: How did you use AI tools (if any)? What worked well? What needed correction?
6. **Scaling Considerations**: How would this scale to 1000+ cells?

---

## Deliverables Checklist

- [ ] Cleaned data (CSV and in database)
- [ ] Database file (SQLite, populated)
- [ ] All source code (well-documented, comments)
- [ ] requirements.txt or similar
- [ ] Visualization example outputs (png format, or other image format, or markdownfiles with images embedded, or PDFs)
- [ ] Presentation (PDF, pptx, or other format, ≤6 slides)

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

