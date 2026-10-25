# Credleaf

<div align="center">

<img
   src="Front-end/Landing%20page/logo.svg" alt="Credleaf Logo" width="400"/>

  <br>

  <br>

[![Status](https://img.shields.io/badge/status-active-success.svg)]()

[![License](https://img.shields.io/badge/license-MIT-blue.svg)]()

[![Made with Python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)

[![Made with JavaScript](https://img.shields.io/badge/Made%20with-JavaScript-yellow.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

[![Last Updated](https://img.shields.io/badge/Last%20Updated-April%202025-brightgreen.svg)]()

</div>

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Installation & Setup](#-installation--setup)
- [API Documentation](#-api-documentation)
- [Project Structure](#-project-structure)

## 🔍 Overview

Credleaf is a comprehensive web-based osint tool for fact-checking and data visualization, specifically designed for analyzing healthcare and vaccine-related information. The platform employs interactive network graphs, time series visualizations, and advanced fact-checking algorithms to provide users with reliable insights into complex healthcare data.

The system integrates multiple fact-checking services and employs sophisticated analysis techniques including temporal pattern recognition, semantic alignment evaluation, and graph structure analysis to deliver trustworthy information assessment.

## ✨ Key Features

### 🔍 Fact-Checking API

- Integration with multiple authoritative fact-checking services (Google Fact Check, PolitiFact, OpenAI)
- Aggregated trust scores based on comprehensive analysis
- Advanced analysis components:
  - Temporal pattern analysis
  - Semantic alignment evaluation
  - Graph structure analysis
  - Customizable parameter weights for personalized assessment

### 🕸️ Interactive Network Graph Visualization

- Dynamic node highlighting for focus areas
- Neighborhood exploration to understand relationships
- Advanced filtering capabilities
- Intuitive search functionality
- Detailed tooltips for information at a glance
- Physics-based layout with stabilization for optimal viewing

### 📊 Time Series Visualization

- Interactive charts for temporal data analysis
- Responsive hover functionality
- Contextual data highlighting
- Custom legend for clear data interpretation

### 🖥️ User Interface

- Clean, intuitive landing page
- URL submission for immediate analysis
- Streamlined navigation between visualization components

## 🚀 Installation & Setup

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd Credleaf
   ```

2. **Install Python dependencies**

   ```bash
   pip install flask requests pandas numpy networkx matplotlib
   ```

3. **Set up Ollama Embeddings**

   - Install the Ollama CLI from the [Ollama website](https://ollama.com/)
   - Configure your embeddings:
     ```bash
     ollama configure --api-key <your-api-key>
     ```
   - Ensure the Ollama service is running locally or accessible via the configured API endpoint

4. **Configure fact-checking API keys**

   - Open `Back-end/api.py`
   - Update the API keys:
     ```python
     FACT_CHECK_APIS = {
         "google_factcheck": {
             "url": "https://factchecktools.googleapis.com/v1alpha1/claims:search",
             "key": "YOUR_GOOGLE_FACTCHECK_API_KEY"  # Replace with actual API key
         },
         "open_ai": {
             "url": "https://api.openai.com/v1/completions",
             "key": "YOUR_OPENAI_API_KEY"  # Replace with actual API key
         }
         # ...other APIs
     }
     ```

5. **Start the Flask API**

   ```bash
   cd Back-end
   python api.py
   ```

6. **Set up the web server**

   For local development, use Python's built-in HTTP server:

   ```bash
   cd Front-end
   python -m http.server 8000
   ```

### Graph Data Generation

To generate new graph data:

```bash
cd Back-end/Graph
python generate_graph.py --input <path-to-data> --output <output-path>
```

## 📚 API Documentation

### Endpoints

| Endpoint     | Method | Description                               |
| ------------ | ------ | ----------------------------------------- |
| `/factcheck` | POST   | Submit a claim for fact-checking analysis |
| `/health`    | GET    | Check API status and available services   |


### Example Response

```json
{
  "claim": "The claim text to be fact-checked",
  "aggregate_trust_score": 6.75,
  "component_scores": {
    "api_average": 7.0,
    "temporal_analysis": 7.0,
    "semantic_alignment": 6.5,
    "graph_structure": 6.5
  },
  "api_details": [
    { "source": "google_factcheck", "score": 8.0 },
    { "source": "politifact", "score": 7.0 },
    { "source": "open_ai", "score": 6.0 }
  ],
  "explanation": {
    "score_range": "0-10 where 10 indicates highest trustworthiness",
    "weights": {
      "api": 1.0,
      "temporal": 1.0,
      "semantic": 1.0,
      "graph": 1.0
    }
  }
}
```

## 📁 Project Structure

```
ReadMe.md
Back-end/
    api.py                  # Flask API for fact-checking
    Graph/
        generate_graph.py   # Python script for graph generation
Front-end/
    Graph network/
        graph-data.js       # Data management for graph visualization
        graph-filter.js     # Filtering functionality for graph nodes
        graph-highlight.js  # Highlighting functionality for graph nodes
        graph-init.js       # Graph initialization logic
        graph.html          # Vaccine sentiment network visualization
        index_graph.html    # Alternative graph network entry point
        index.html          # Main network graph page
        large network.html  # Extended network visualization
        styles.css          # Styling for graph visualizations
    Landing page/
        index.html          # Main landing page
        logo.svg            # Credleaf logo
        redirect-page.html  # Post-submission redirect
    Time series/
        time-series.html    # Time series visualization of vaccine publication data
```

---

<div align="center">
  <sub>Built with 🌿 by the Credleaf Team</sub>
</div>
