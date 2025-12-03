# **NYC Motor Vehicle Collision Analysis**  
*A data visualization project exploring crash patterns, risk factors, and urban safety trends across New York City.*

---

## **Overview**

This project analyzes patterns in NYC motor vehicle collisions using two datasets published by the NYPD:

- **Motor Vehicle Collisions – Crashes**  
  Includes **date**, **time**, **borough**, **location**, and counts of **injuries** and **fatalities**.

- **Motor Vehicle Collisions – Vehicles**  
  Contains details about the **vehicles involved**, including make and model.

By merging both datasets on their shared **collision ID**, I developed a series of interactive visualizations to answer a guiding question:

> **Under what conditions is it most dangerous to drive in NYC?**

The process included data cleaning, exploratory sketches, iterative prototyping, geospatial processing, and performance-focused refactoring.  
This report summarizes the visualizations and insights that emerged.

---

## **Research Questions**

To explore the central question, I examined several aspects of crash activity:

1. **What times of day see the highest crash activity?**  
2. **Are certain months or seasons more dangerous?**  
3. **How do crash rates vary across the boroughs?**  
4. **Which vehicle makes appear most frequently in crash records?**  
   *(Explored but difficult to interpret without registration data for normalization.)*

---

## **Initial Sketches**

Before building full interactive views, I created small hand-sketched prototypes to experiment with possible chart types.

### **Vehicle Make Frequency Bar Chart**

A straightforward bar chart comparing crash counts by vehicle make.
<img width="665" src="https://github.com/user-attachments/assets/327fbd4d-0351-4c77-a1de-bca06cbd5f0e" />

### **Bubble Chart Alternative**

A more visually expressive option, but ultimately too difficult for precise comparison.
<img width="808" src="https://github.com/user-attachments/assets/9aa54e61-35dd-4cc1-b10f-25e5cd1f029e" />

These early sketches helped guide the design choices that followed.

---

## **Crash Counts by Hour**

One of the first functional visualizations was a stacked bar chart showing total collisions per hour of day, including injuries and fatalities as separate layers.
[![image](https://github.com/user-attachments/assets/05870ee7-9732-498a-b1ba-507c50bcd7f8)](https://vizhub.com/JoseMorales7/8f5a29dbad174b1a90e7671b09b654e2)

**Insights:**

- Collisions peak between **4–5 PM**, aligning with evening rush hour.  
- The lowest crash window occurs between **2–5 AM**.  
- Fatal crashes are rare enough that they appear only minimally in the stack.

---

# **Interactive Visualizations**

## **1. Borough-Level Crash Map**

The first interactive visualization mapped total crash counts across NYC’s boroughs.  
This required cleaning geographic boundary data and joining it with aggregated crash statistics.
[![image](https://github.com/user-attachments/assets/9938e342-c797-43d8-b58b-60f70b30d889)](https://vizhub.com/JoseMorales7/e3127b2fe72b4cb1a181fda3499f9aa7)

---

## **2. Crash Locations Across NYC (2025)**

Plotting individual crash locations for 2025 revealed dense street patterns across the city.  
The city’s grid becomes clearly visible through the concentration of collision points alone.
[![image](https://github.com/user-attachments/assets/44627be9-088f-4986-9bed-ee3adf4a900b)](https://vizhub.com/JoseMorales7/4c4fcb7e1530498a986035a3d1fbe64f)

---

## **3. Vehicle Make Frequency**

This visualization examines which vehicle makes appear most frequently in crash records.
[![image](https://github.com/user-attachments/assets/41ec5a84-9d09-4b1e-8d6e-b77ec0fb9606)](https://vizhub.com/JoseMorales7/82ef6a30ea7840a7b79e017ee4831b75)

**Note:**  
Because makes like Toyota and Honda are extremely common in NYC, they dominate the raw counts.  
Without registration data, this visualization cannot reflect relative risk—but it remains useful as exploratory context.

---

## **4. Injuries & Fatalities Map (Interactive, High-Performance Visualization)**

I expanded the borough-level crash map into a more advanced interactive view that overlays collision points involving **pedestrians**, **cyclists**, and **motorists** who were injured or killed. Users can toggle specific categories, pan and zoom smoothly across the map, and hover over boroughs to reveal summary statistics.

To support interaction with thousands of plotted points, I implemented several performance optimizations:

- Migrated all incident points from individual **SVG circles** to a single **HTML canvas layer**, dramatically reducing DOM overhead  
- Cached geographic projections to avoid redundant calculations  
- Used `requestAnimationFrame` to debounce panning and zooming  
- Layered the SVG (with borough boundaries and tooltips) **above** the canvas, ensuring that hover summaries remain visible  
- Added toggleable legends and intuitive map controls (click-and-drag panning and scroll-to-zoom)

These improvements made the visualization significantly more responsive and easier to explore, even with dense, city-wide data.
[![image](https://github.com/user-attachments/assets/58b7dc67-bb11-4db4-84f5-f993916905ad)](https://vizhub.com/JoseMorales7/ea74102640804c95811176b698a316c7)

---

## **5. Bar-Chart Interactivity Improvements**

Across several bar charts, I added enhancements to improve readability and engagement:

### Hover Highlighting
Emphasizes an individual bar when hovered, helping clarify comparisons.
[![image](https://github.com/user-attachments/assets/51e051a3-fdef-49d7-91aa-276a2b2e16ee)](https://vizhub.com/JoseMorales7/feb40126c5aa40409a3ed9729c674f49)

### Interactive Legend for Stacked Bars
Allows users to toggle categories on and off, especially helpful for small but important values like fatalities.
[![image](https://github.com/user-attachments/assets/fd99e6e8-5f43-4dca-859d-6ed9c9caaa02)](https://vizhub.com/JoseMorales7/6eb1ac12bc2a46b2bc685a9f02e92d05)

---

## **6. Sparkline-Style Crash Trend Visualization**

Crash counts vary significantly day-to-day, so I designed a sparkline-style time-series visualization with smoothing applied to reveal long-term patterns.

To ensure accurate representation, I corrected the y-axis so that it begins at **zero**, preventing unintentional exaggeration of small changes.
[![image](https://github.com/user-attachments/assets/4ee1e5d4-d158-45de-96a0-79e0ca51e116)](https://vizhub.com/JoseMorales7/5b048d57e4a8440fab4d4c108d6916fc)
[![image](https://github.com/user-attachments/assets/054ea277-0fd8-4312-bf11-e0cfc870536b)](https://vizhub.com/JoseMorales7/6390af510b3d46d69e2b53b671f0ebe5)

---

# **Conclusion**

Through a series of interactive data visualizations, this project explores when and where motor vehicle collisions occur in New York City, and which road users are most affected. Taken together, the visualizations reveal:

- Daily crash rhythms and rush-hour peaks  
- Clear borough-level differences in crash volume  
- High-density corridors revealed directly from point data  
- Injury- and fatality-specific geographic patterns  
- Longer-term temporal trends through smoothed time-series views  

This project strengthened my skills in **data wrangling**, **React**, **D3**, **TopoJSON**, **canvas/SVG rendering**, **performance optimization**, and **interactive design**.  
The resulting tools provide a strong foundation for deeper analysis of urban safety and transportation planning.
