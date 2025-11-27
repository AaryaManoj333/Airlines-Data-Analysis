
#  Airlines Occupancy and Profitability Analysis (SQL & Python)

##  Project Objective

The core objective of this project is to use **SQL queries** to join complex relational data and accurately calculate flight occupancy rates. This analysis aims to **identify specific, underperforming flights and routes** where the occupancy rate is low, providing actionable recommendations to increase seat utilization and overall profitability for the airline.

-----

##  Data & Database Architecture

The analysis utilizes data stored in a single **SQLite database** (`travel.sqlite`) comprising **8 interconnected tables**. This setup required robust data exploration and SQL joins to link bookings, flights, tickets, and aircraft specifications.

### Key Data Tables Analyzed:

| Table Name | Primary Role in Analysis |
| :--- | :--- |
| **flights** | Route identification, scheduled times, and aircraft code. |
| **seats** | Contains the **maximum seat capacity** per aircraft model. |
| **ticket\_flights** | Contains individual ticket prices (`amount`) and **fare conditions** (Business/Economy). |
| **boarding\_passes** | Records which seats were actually utilized per flight. |
| **bookings** | Tracks booking reference and total transaction value. |

-----

##  Technical Workflow and Methodology

This project demonstrates expertise in connecting Python to a relational database for data extraction and preliminary cleaning.

### 1\. Database Connection and Schema Exploration

  * **Technology:** Python, `sqlite3`, `pandas`.
  * **Process:** Established a connection to the `travel.sqlite` file. Extracted and reviewed the schema of all eight tables (`PRAGMA table_info`), ensuring a complete understanding of data types and primary/foreign keys necessary for complex joins.

### 2\. Data Health Check

  * **Cleaning:** Utilized Python and Pandas (`.isna().sum()`) to verify the completeness of all 8 tables, confirming **zero missing values** in key identifying columns across the entire database.

### 3\. Core Analytical Logic (SQL Focus)

The subsequent analysis focuses on calculating two core metrics by joining the `flights`, `seats`, `boarding_passes`, and `ticket_flights` tables:

  * **Occupancy Rate:** Calculated by dividing `COUNT(boarding_passes.ticket_no)` by the total number of seats listed in the `seats` table for the corresponding aircraft.
  * **Revenue Performance:** Aggregated flight revenue per flight (`SUM(ticket_flights.amount)`) to correlate ticket sales with occupancy and identify high-cost/low-yield routes.

-----

##  Key Findings and Recommendations

Replace the bracketed text below with your actual findings and business recommendations.

| Finding Category | Detailed Insight | Recommendation |
| :--- | :--- | :--- |
| **Low-Occupancy Flights** | Identified **[48]** number of flights/routes operating below the crucial **[65]%** breakeven load factor. | **[Action 1]** E.g., Replace large-capacity aircraft (Boeing 777) with regional jets (Airbus 320) on these routes to reduce fixed operational costs. |
| **Fare Class Disparity** | The **[Economy]** fare class showed the highest number of unsold seats on low-occupancy routes. | **[Action 2]** E.g., Implement dynamic pricing adjustments or offer bundled deals for unsold premium seats 24 hours prior to departure. |
| **High-Yield Routes** | Identified routes where average ticket yield (Revenue per Seat) is **[28]%** higher than the overall network average, regardless of occupancy. | **[Action 3]** E.g., Focus marketing efforts and scheduling priority on these high-value routes. |

-----
