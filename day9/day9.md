Key Technical & Product Learnings
1. State Architecture in Single-File SPAs

Normalized Data Model: Separating the base nutritional reference table (per 100g) from user transaction logs (consumed_items with unit-scaling multipliers) prevents calculation drift and makes data exports/imports clean.

Reactive Re-renders: In pure JavaScript (no React/Vue), binding an event-driven updateDashboard() dispatcher to state changes ensures charts, deficiency warnings, and metric cards stay synchronized without race conditions.

2. Chart.js Lifecycle Management

Instantiating new charts over existing <canvas> elements causes canvas reuse errors and ghost tooltip glitches. Always track chart instances in an object and explicitly call .destroy() before re-rendering updated datasets.

3. Client-Side Nutritional Computation

BMR & TDEE Calculations: Using the Mifflin-St Jeor equation provides reliable baseline expenditure, but macro splits must dynamically adjust based on user activity multipliers and deficit/surplus goals.

Non-Linear Deficiencies: Calculating micronutrient health scores requires a threshold curve rather than a flat percentage, preventing excess intake of one vitamin from masking severe deficiencies in another.

4. Clinical Safety & Liability in Health Tech

Tracking micronutrients without maximum tolerable limits (Upper Intake Levels, or UL) can lead users to dangerously overconsume items like fat-soluble vitamins (A, D) or minerals (Iron, Sodium). Enhanced tools must flag both floors (RDAs) and ceilings (ULs)
