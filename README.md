# **NYC Motor Vehicle Collision Analysis**  
*A data visualization project exploring crash patterns, risk factors, and urban safety trends across New York City.*

---

## **Overview**

This project examines patterns in NYC motor vehicle collisions using two datasets published by the NYPD:

- **Motor Vehicle Collisions – Crashes**  
  Contains details such as **date/time**, **borough**, **location**, and **injury/fatality counts**.

- **Motor Vehicle Collisions – Vehicles**  
  Includes information on the **vehicles involved**, such as make and model.

By merging both datasets on their shared **collision ID**, I set out to answer a broader guiding question:

> **Under what conditions is it most dangerous to drive in NYC?**

Over the course of the project, I iteratively explored the data, built sketches and prototypes, and developed several interactive D3 visualizations.  
This README documents the process in report form—highlighting methods, decisions, results, and lessons learned.

---

## **Research Questions**

To break down the main question, I explored the following:

1. **What times of day see the highest crash activity?**  
2. **Are certain times of year more dangerous than others?**  
3. **How do crash rates vary across NYC’s boroughs?**  
4. **Which vehicle makes appear most frequently in crashes?**  
   *(Moved to “Next Steps” due to data normalization challenges.)*

---

## **Initial Sketches**

Before building anything interactive, I created early sketches to explore possible chart types.

### **Vehicle Make Frequency Bar Chart**
<img width="665" src="https://github.com/user-attachments/assets/327fbd4d-0351-4c77-a1de-bca06cbd5f0e" />

A simple bar chart comparing crash counts by vehicle make.

### **Bubble Chart Alternative**
<img width="808" src="https://github.com/user-attachments/assets/9aa54e61-35dd-4cc1-b10f-25e5cd1f029e" />

Although visually interesting, the bubble chart made comparison difficult, so I opted not to use this form later.

---

## **Early Prototype: Crash Counts by Hour**

One of my first working visualizations was a stacked bar chart showing total crashes by hour of day, with injuries and fatalities broken out as separate layers.

[![image](https://github.com/user-attachments/assets/05870ee7-9732-498a-b1ba-507c50bcd7f8)](https://vizhub.com/JoseMorales7/8f5a29dbad174b1a90e7671b09b654e2)

**Insights:**
- Collisions peak between **4–5 PM**, consistent with evening rush hour.
- The safest window appears to be **2–5 AM**.
- Fatal crashes occur too infrequently to appear visibly in the stack, but the data is still represented.

---

# **Interactive Visualizations**

## **1. Borough-Level Crash Map**

My first major interactive visualization mapped total crashes per borough.

[![image](https://github.com/user-attachments/assets/9938e342-c797-43d8-b58b-60f70b30d889)](https://vizhub.com/JoseMorales7/e3127b2fe72b4cb1a181fda3499f9aa7)

This required preparing cleaned geographic boundary assets and associating them with aggregated crash counts.

---

## **2. Crash Locations Across NYC (2025)**

I plotted individual crash points for 2025. The resulting density revealed NYC’s street grid directly from the data.

[![image](https://github.com/user-attachments/assets/44627be9-088f-4986-9bed-ee3adf4a900b)](https://vizhub.com/JoseMorales7/4c4fcb7e1530498a986035a3d1fbe64f)

---

## **3. Vehicle Make Frequency**

A deeper look at which vehicle makes appear in recorded crashes.

[![image](https://github.com/user-attachments/assets/41ec5a84-9d09-4b1e-8d6e-b77ec0fb9606)](https://vizhub.com/JoseMorales7/82ef6a30ea7840a7b79e017ee4831b75)

**Note:**  
Because Toyota and Honda are extremely common in NYC, they dominate the raw counts. Without data on the number of registered vehicles per make, it’s not possible to *normalize* this chart to reflect true risk rates. Thus, this analysis is included only as an exploratory step—see **Next Steps**.

---

## **4. Injuries & Fatalities Map (Enhanced Interactivity)**

I expanded the borough map by overlaying crash points where **pedestrians**, **cyclists**, or **motorists** were injured or killed.  
Users can toggle categories, and borough-level stats appear on hover.

[![image](https://github.com/user-attachments/assets/f1708954-a557-4406-853b-79ec5b6d8c98)](https://vizhub.com/JoseMorales7/dc3867d5156342c0b6e5189be5301ffe)

Performance was a challenge due to the number of plotted points, but careful optimization made it feasible.

---

## **5. Interactive Legends + Map Panning/Zooming**

Inspired by lecture demos, I added interactive legends to multiple charts.

### Borough Crash Map With Panning/Zooming
[![image](https://github.com/user-attachments/assets/2cfe5a94-99fa-4aba-b074-de65c85dd1ae)](https://vizhub.com/JoseMorales7/407a118dd83e4e698888cae8b58a5b54)

### Crash Point Map With Toggleable Categories
[![image](https://github.com/user-attachments/assets/e6a90c1b-cfc3-4376-abc2-75b0bbc55a7d)](https://vizhub.com/JoseMorales7/8479aa78eec8481884862041f3ba2933)

---

## **6. Bar-Chart Interactivity Improvements**

### Bar Highlight on Hover
[![image](https://github.com/user-attachments/assets/51e051a3-fdef-49d7-91aa-276a2b2e16ee)](https://vizhub.com/JoseMorales7/feb40126c5aa40409a3ed9729c674f49)

### Interactive Legend for Stacked Bars
[![image](https://github.com/user-attachments/assets/fd99e6e8-5f43-4dca-859d-6ed9c9caaa02)](https://vizhub.com/JoseMorales7/6eb1ac12bc2a46b2bc685a9f02e92d05)

These interactions make the charts more intuitive and help highlight small but important values such as fatalities.

---

## **7. Sparkline-Style Crash Trend Visualization**

After struggling with VizHub file-loading issues, I adapted an earlier time-series chart into a sparkline-like interactive view.

[![image](https://github.com/user-attachments/assets/7d660add-049d-46f7-8288-02256be44c46)](https://vizhub.com/JoseMorales7/3eae91ada8274f529f10ac87fd20c708)

Crashes fluctuate dramatically day-to-day, so I applied smoothing for clarity:

[![image](https://github.com/user-attachments/assets/017da182-8279-4a85-bc5c-883f5c7b0dff)](https://vizhub.com/JoseMorales7/16fef06f397b4139ad69c7da9cdadf9c)

---

# **Conclusion**

Over the course of this project, I explored crash patterns in NYC through a series of interactive data visualizations. By iteratively sketching, prototyping, and refining, I developed a portfolio-ready set of tools that reveal:

- Daily rush-hour risk peaks  
- Borough-level differences in crash volume  
- High-density corridors visible directly from point data  
- Injury-specific geographic patterns  
- Long-term crash trends via sparkline-style views  

This project strengthened my skills in **data wrangling**, **D3**, **React**, **geospatial visualization**, and **interactive design**, and provides a strong foundation for further urban safety research.

# Updates 11/22/2025

I’ve made some final touch-ups to my visualizations. Based on Matt’s feedback, I updated the plot in Section 7 so that the y-axis is properly aligned and starts at 0, giving a more accurate sense of the number of daily collisions. I also optimized the visualization in Section 5, which was previously laggy due to the large data volume and some inefficiencies in the code. To address this, I restricted the dataset to collisions from 2025 and refactored the code, resulting in a slightly more efficient codebase and noticeably smoother rendering.

---

