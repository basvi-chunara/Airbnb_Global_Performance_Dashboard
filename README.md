# Airbnb Global Performance Power BI Report

A multi-page Power BI Template (`.pbit`) that analyses Airbnb listing inventory, host quality, guest ratings, and review behaviour across global cities. The report uses DAX queries, is built on two CSV source files, and provides interactive dashboards for supply-side and demand-side insights.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [File Structure](#file-structure)
3. [Data Sources](#data-sources)
4. [Report Pages](#report-pages)
   - [Overview](#overview)
   - [Ratings](#ratings)
   - [Reviews](#reviews)
5. [Business Impacts & Insights](#business-impact--insights)

---

## Project Overview

| Attribute | Detail |
|-----------|--------|
| Tool | Microsoft Power BI Desktop |
| File format | `.pbit` (Power BI Template) |
| PBI compatibility level | 1600 |
| Template version | 1.28 |
| Report pages | 3 — Overview, Ratings, Reviews |

The report is designed to answer questions such as:
- How many listings and hosts operate across which cities?
- What is the distribution of room types and property types?
- How have listings grown over time?
- How do average prices and guest ratings compare across cities?
- What percentage of hosts are verified or have a profile picture?
- How frequent are reviewers, and which cities drive the most reviews by month?

---

## File Structure

```
Airbnb_Global_Performace.pbit
├── Version                          # Template format version (1.28)
├── [Content_Types].xml
├── DataModelSchema                  # Tabular data model (UTF-16 LE JSON)
├── DiagramLayout                    # Model view layout
├── Settings
├── Metadata
├── SecurityBindings
└── Report/
    ├── Layout                       # Report page definitions (UTF-16 LE JSON)
    └── StaticResources/
        └── RegisteredResources/
            ├── air_bnb_logo*.png
            ├── Dotted_Line_rectangle*.png
            ├── Magnifying_glass*.png
            ├── SHIELD*.PNG
            └── Star*.webp
```

---

## Data Sources

The template connects to two local CSV files. When opening the `.pbit`, Power BI will prompt you to re-point these paths to your own copies of the source files.

### Listings.csv

| Property | Value |
|----------|-------|
| Delimiter | `,` |
| Columns | 33 |
| Link | `https://mavenanalytics.io/data-playground/airbnb-listings-reviews` |

Contains one row per Airbnb listing. Key fields include host details, location hierarchy (neighbourhood → district → city), property and room type, pricing, stay constraints, review scores across six dimensions, and host trust indicators.

### Reviews.csv

| Property | Value |
|----------|-------|
| Delimiter | `,` |
| Columns | 4 |
| Link | `https://mavenanalytics.io/data-playground/airbnb-listings-reviews` |

Contains one row per guest review. Fields: `listing_id`, `review_id`, `date`, `reviewer_id`.

---

## Report Pages

### Overview

**Purpose:** High-level supply snapshot — how many listings exist, where, and how the portfolio has grown over time.

**Visuals:**
- 5 **KPI Cards**: Total Listings, Total Reviews, property type count, city count, and host count
- 1 **Line Chart**: Listings over time by `host_since` year, broken down by room type (Entire place, Private room, Shared room, Hotel room) — shows platform growth trajectory
- Multiple **text labels and decorative shapes** providing contextual annotations, city highlights, and styled section headers with the Airbnb brand colour palette

**Key insight this page answers:** Which cities have the most listings, how many hosts are active, and has supply been growing or plateauing?

---

### Ratings

**Purpose:** Quality analysis — how do guest experience scores and pricing vary across cities and room types.

**Visuals:**
- **Line + Stacked Column Combo Chart**: Combines average price (line) with rating dimensions (columns) for cross-city comparison
- **Bar Chart**: Ranking of cities by one or more rating sub-dimensions (accuracy, cleanliness, etc.)
- **Column Chart**: Distribution or comparison of rating scores by category
- **Pivot Table (Matrix)**: Detailed breakdown of all six review score dimensions (accuracy, cleanliness, check-in, communication, location, value) across cities or room types
- Supporting **images, textboxes, and shapes** for layout and labelling

**Key insight this page answers:** Which cities deliver the best guest experience? Is price correlated with higher ratings? Which rating dimension drags the overall score down?

---

### Reviews

**Purpose:** Demand-side analysis — how reviews accumulate over time, reviewer behaviour patterns, and host trust breakdown.

**Visuals:**
- **Column Chart**: Review volume — likely showing monthly or yearly review counts
- 5 **KPI Cards**:
  - `VerifiedProfile %` — proportion of fully trusted hosts
  - `Verified_NoProfile %`
  - `NotVerified_Profile %`
  - `NotVerified_NoProfile %`
  - (one additional card for a reviewer/review metric)
- **Ribbon Chart**: `% of Monthly Reviews` by `city` across months (`Review Month`) — shows which cities dominate review share each month and how that shifts seasonally
- Supporting **textboxes and shapes** for section labels and callout annotations

**Key insight this page answers:** Are reviews growing? Which cities are most active by month? What proportion of hosts have verified identities and profile pictures?

---

## Business Impact & Insights
 
Here are the five key things this report tells, and what to do about them.
 
### 1. A few cities carry most of the weight
 
Most listings are concentrated in just a handful of cities. That means if something goes wrong in one of those cities: a new law, a slow season, bad press, the whole business feels it. 
**What to do:** Look at the city ranking chart and ask which cities are underrepresented. Those are good candidates for growing host supply.
 
 
### 2. Unverified hosts are losing bookings
 
A chunk of hosts have no profile picture and no identity verification. Guests are much less likely to book those listings because they feel less safe. This is lost revenue sitting right there. **What to do:** Send nudges to unverified hosts to complete their profiles. Even getting them to add a photo makes a difference.
 
 
### 3. Some cities charge too much for what they deliver
 
The Ratings page shows the average price alongside guest scores. In some cities, guests are paying a lot but rating their stay poorly — especially on "value." That's a sign guests feel ripped off, and they won't come back. **What to do:** Flag cities where price is high but value scores are low, and work with hosts there on fairer pricing.
 
 
### 4. Low cleanliness scores are the easiest problem to fix
 
Of all the rating categories (accuracy, cleanliness, check-in, communication, location, value), cleanliness is the one hosts have the most direct control over. Cities with low cleanliness scores are dragging down their overall rating unnecessarily. **What to do:** Share cleaning checklists and guidelines with hosts in cities where cleanliness scores are below average.
 
 
### 5. Review activity shows which cities are actually popular right now
 
The ribbon chart shows how many reviews each month come from each city. A city that gets lots of reviews in summer but goes quiet in winter is highly seasonal, which affects how much support and marketing it needs month to month. **What to do:** Use this chart to plan when to run promotions and where to focus host support based on real activity, not just listing counts.
