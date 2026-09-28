# 🏭 DS_Day01_26: Manufacturing — Why Is Production Falling?

**Industry:** Automotive Manufacturing  
**Machine Learning Algorithm:** Random Forest Classifier  

---

## 📌 Project Overview
This project investigates declining production output in an automotive manufacturing plant using daily logs of `Date`, `Machine_ID`, `Machine_Output`, `Downtime`, `Shift`, `Operator`, `Temperature`, `Maintenance_Status`, and `Production_Volume`. It calculates **Overall Equipment Effectiveness (OEE)** components (Availability, Performance, Quality), pinpoints when the decline started, and trains a **Random Forest** model to identify the largest operational sources of productivity loss.

---

## 🔍 6 Key Insights
1. **Onset of Production Decline:** Time-series analysis shows that plant-wide daily production remained stable through January and early February, with a sharp and sustained decline starting on **February 15, 2026**.
2. **Machines Driving Production Losses:** **`MACH_03` and `MACH_05`** account for the largest cumulative production losses and the lowest OEE scores due to chronic overheating and frequent unplanned stops after mid-February.
3. **Maintenance vs. Downtime Correlation:** Machines with **Overdue Maintenance** suffer more than **5x higher average downtime** compared to machines with completed maintenance, directly starving shift availability.
4. **Thermal Degradation Impact:** Elevated operating temperatures (>80°C) strongly correlate with overdue maintenance, slowing down cycle speeds (Performance loss) and increasing scrap/defect rates (Quality loss).
5. **Objective Shift & Operator Comparison:** Operators show comparable baseline efficiency across the plant; minor output variations between operators are driven by machine assignment (`MACH_03`/`MACH_05`) and slightly longer repair response times during the **Night Shift**, rather than individual operator capability.
6. **Top Productivity Loss Drivers (Random Forest):** Feature importance confirms that **Downtime duration**, **Operating Temperature**, **Overdue Maintenance status**, and specific bottleneck machines (`MACH_03`, `MACH_05`) are the primary predictors of severe production drops, while operator identity has minimal impact.

---

## ⚙️ Overall Equipment Effectiveness (OEE) Breakdown
* **Availability:** Driven down primarily by unscheduled downtime on `MACH_03` and `MACH_05`.
* **Performance:** Reduced when machine temperature exceeds 80°C, forcing slower cycle rates.
* **Quality:** Good `Production_Volume` vs gross `Machine_Output` drops during high-temperature runs due to thermal defects.

---

## 🛠️ Practical Action Plan
1. **Immediate Overhaul of Bottleneck Machines:** Schedule an immediate preventive overhaul and cooling-system repair for **`MACH_03` and `MACH_05`** to eliminate the root cause of the post-Feb 15 production drop.
2. **Enforce Zero-Overdue Maintenance SLAs:** Transition from reactive repairs to strict preventive maintenance intervals so no machine enters the `Overdue` state.
3. **Automated Thermal Threshold Alerts:** Install real-time temperature alerts at **78°C** to trigger cooling checks before thermal stress causes downtime or quality defects.
4. **Night Shift Maintenance Support:** Allocate dedicated maintenance technicians to the Night Shift to match Morning Shift repair turnaround times.
5. **Fair Operator Evaluation:** Standardize operator performance KPIs using machine-adjusted OEE metrics so operators assigned to older or high-downtime machines are evaluated fairly.
