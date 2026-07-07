# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains the static HTML website for the **JPL Climate Summer School** (hosted at https://jpl-cmda.org). It consists of HTML pages for educational content about climate science topics and group projects.

## Repository Structure

- **html/** - Main directory containing all HTML pages and supporting files
  - **CMDA_intro.html** - Index page for the overall summer school
  - **ccs.html** - Main landing page for group projects (this is the central hub)
  - **topic_*.html** - Topic landing pages for individual group projects (one per topic)
  - **topic_*.pdf** - Presentation slides corresponding to each topic
  - **2022/, 2023/** - Archives from previous years

## 2026 Topic List

The 2026 summer school has six group project topics:

1. **global_warming** - Where is global warming?
2. **marine_co2** - Marine carbon dioxide removal
3. **sea_level** - Sea level rise from mass gain and thermal expansion
4. **tree_mortality** - Ecological forecasting of tree mortality
5. **high_resolution** - High resolution regional climate model simulations
6. **water_cycle** - Human influences on the water cycle
7. **wildfires** - (New for 2026) - Topic page needs to be created

## Common Development Tasks

### Adding a New Topic

1. Create a new HTML file using the naming convention `topic_<name>.html`
2. Use an existing topic file (e.g., `topic_global_warming.html`) as a template
3. Extract information from the corresponding `topic_<name>.pdf` presentation to fill in:
   - Topic overview and description
   - Key learning objectives
   - Relevant datasets (reference locations from the project server materials)
   - Any scripts or tools needed
4. Ensure the presentation PDF exists at `topic_<name>.pdf`
5. Update **ccs.html** to add a link to the new topic in the project list:
   - Find the `<ul>` list that contains the topic links
   - Add a new `<li>` with an `<a href="topic_<name>.html">` link

### Updating Topic Presentations

- Presentation PDFs are updated by replacing the existing `topic_*.pdf` file
- Topic HTML pages do not need changes when PDFs are updated
- Recent PDF updates (2026): global_warming, tree_mortality

### Viewing the Website Locally

Since this is a static HTML site, you can open any HTML file directly in a browser. To serve it properly with relative links:

```bash
# Using Python 3
python -m http.server 8000

# Using Python 2
python -m SimpleHTTPServer 8000

# Using Node.js (if installed)
npx http-server
```

Then visit `http://localhost:8000/html/CMDA_intro.html` or `http://localhost:8000/html/ccs.html`

## File Patterns

### Topic HTML Files

Topic pages follow a standard structure:
- Import Materialize CSS framework for styling
- Include Material Icons
- Have a banner header with title
- Use consistent font sizes and spacing (22px for paragraphs and lists)
- Link to their corresponding PDF presentation
- Link to the Jupyter Hub server at https://hub.jpl-cmda.org/
- **Important**: Content should be extracted from the corresponding PDF presentation files to ensure alignment with the actual materials students work with

### Project Server Metadata

Two metadata files at the repository root document the project server structure:

- **data.txt** - Directory listing of datasets available on the project server for each topic
  - Shows the structure of `/home/jovyan/shared/NASA_Summer_School_2026/*/materials/data`
  - Reference this when documenting available datasets in topic HTML pages
  
- **scripts.txt** - Directory listing of Jupyter notebooks and scripts for each topic
  - Shows the structure of `/home/jovyan/shared/NASA_Summer_School_2026/*/materials/`
  - Reference this when documenting available materials in topic HTML pages

Use these files as the source of truth when updating topic pages with information about what's available on the project server.

### Generated Files to Ignore

- `.*.html.swp` - Vim swap files (can be deleted)
- `__pycache__/` - Python bytecode cache
- These are safe to remove and will be regenerated

## Current Status

- **Last update**: August 7, 2024
- **Deployed version**: https://jpl-cmda.org (tracks the state of this repo)
- **Contact Scientists**: Seungwon Lee, Alex Goodman
