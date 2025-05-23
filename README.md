# Multi-Agent Cargo Transfer & Location Analysis System

## 📦 Project Overview

This project leverages a **multi-agent architecture** to identify **Batman filming locations** and **supercar manufacturing sites** around the world, then calculates the **air cargo travel time** from these sites to Gotham City (approximated as New York City, `40.7128° N, 74.0060° W`). The final output includes a **geospatial map visualization** of the locations, color-coded by transfer time.

---

## 🧠 Agents and Tools

### Agents

1. **`web_agent`**:

   * Tasked with web scraping and data gathering.
   * Utilizes DuckDuckGo and webpage visitation to find verified location data.

2. **`manager_agent`**:

   * Manages the overall planning and output generation.
   * Instructs `web_agent` to search, fetch, and process required data.
   * Responsible for plotting and saving the geospatial map.

### Tools

* `DuckDuckGoSearchTool`: To find potential web sources.
* `VisitWebpageTool`: To visit and verify data from URLs.
* `calculate_cargo_travel_time`: Custom tool for computing great-circle flight durations for cargo planes, including procedural and indirect flight adjustments.

---

## 🛠️ Custom Function: `calculate_cargo_travel_time`

```python
def calculate_cargo_travel_time(origin_coords, destination_coords, cruising_speed_kmh=750.0) -> float
```

**Functionality**:

* Computes air cargo travel time using the haversine formula.
* Includes 10% buffer for air traffic routing and adds 1 hour for takeoff/landing.

---

## 📊 Output

* **Pandas DataFrame** with:

  * Filming/Factory name
  * Location (lat/lon)
  * Travel time to Gotham
* **Map (`saved_map.png`)**:

  * Scatter plot of all locations
  * Color gradient based on travel time
  * Includes hover tooltips with location info

---

## 🧪 Example Use Case

```python
agent.run("""Find all Batman filming locations in the world, calculate the time to transfer via cargo plane to here (Gotham: 40.7128° N, 74.0060° W)...""")
```

---

## 📦 Dependencies

Install required packages:

```bash
pip install smolagents pandas plotly pillow
```

Also ensure access to:

* A valid Hugging Face API key (for Qwen2.5-Coder-32B-Instruct via `together`)
* Python ≥3.8

---

## 🧩 Extending Functionality

* Add more tools (e.g., geocoding APIs, satellite imagery)
* Introduce LLM-based summarizers for insights from web pages
* Expand plotting to interactive dashboards (e.g., Dash, Streamlit)

---

## 💡 Inspiration & Use Cases

* Supply chain analysis for film production or automotive logistics
* AI-assisted travel and distribution mapping
* Educational tools in geospatial computing and multi-agent systems
