>Platform Analytics ships with pre-configured dashboards and Key Performance Indicators (KPIs) tailored to support a variety of processes. Below are some examples of dashboards targeting different process stakeholders
## Overviewi

Types of Platform Analytics:
- **Incident Analytics**: analytics on incident volume, state, category, priority, resolution rates, etc., and organizes the information by incident State
- **Virtual Assistant Analytics**: analytics on conversations, their completion status and duration, topics, channels, and users
- **Vulnerability Analytics**: executive view into vulnerabilities and vulnerable (risk-related) items, helping the Vulnerability Admin pinpoint areas of concern quickly
- **HR Case Analytics**: provides accountability, progress, performance metrics, and status of HR cases

Type of Stakeholders:
- **Executive**: need information on governance and a high-level overview of process indicators
- **Service Owner**: need information that will help them better understand what drives the quality and the cost of service delivery
- **Front-line worker**: need relevant, targeted information to make the right decisions quickly
- **End User**: need status and quality information about submitted requests and services they use

Architecture Components
- **Indicator (KPI)**:  specific measurement counted or calculated, based on an *Indicator Source* which requires a *date/time* field
- **KPI Details**: exploratory view of indicator results used for more detailed analysis
- **Breakdown**: ability to group indicator scores by a qualitative attribute, such as Priority, Department, or Owner
- **Data Collector**: engine that takes periodic snapshots (*collection jobs*) of your process tables and stores them in the Scores and Snapshots tables for *performance analysis*
- **Data Visualization**: A reusable view of the indicator score that can present data as a single value, a historical trend chart, or using one of many others
- **Next Experience Dashboard**: collection of visualizations that together describe a process or service behavior and target a specific audience

Performance Analytics:  
**Indicators**
	- Define the metrics to track and analyze.
	- Must include a date/time field to anchor data collection.
	- Can be manual or formula-based (see formulas below).

**Data Collection**
- Pulls data from fact tables to populate PA score tables *pa_scores*
- Two main types:
	1. Historic Collection
		- One-time collection when the app is installed/configured.
		- Default: last 60 days; can extend further.
	2. Daily/Periodic Collection
		- Scheduled to run daily/weekly.		
		- Automatically updates scores tables.		
		- Captures accurate trends over time.
- Verify Source:
	- New – records created on a specific day; check timestamp.	
	- Open – active records; ensure required fields are tracked.	
	- Closed – inactive/closed records; ensure required fields are tracked.
- Additional conditions: optional filters to refine data collection for accuracy.

**Breakdown Utility Matrix**
- Maps *breakdown elements to collected data*.
- Links fact table fields to breakdowns (e.g., assignment group, location).
- Enables dashboards to filter, segment, and drill down by breakdown.
- Field attribute = the fact table column that connects to the breakdown element.


**Targets and Thresholds**
- Targets: define *performance goals* for a breakdown element.
	- Components: Indicator, Breakdown, Breakdown Element, Target Value, Date Range, Direction (higher/lower is better).
- Thresholds: define performance zones (red/yellow/green) around the target.
	- Enable dashboards to visualize status at a glance.

**Formulas**
- Formula indicators calculate metrics using other indicators.
- Reference indicators by name in square brackets.
- Combine with math operators and functions.
- Automatically respect breakdown elements unless overridden.

**Dashboards**
- Display indicator scores, targets, and trends.
- Details section shows context: Indicator, Breakdown Element, Score, Target, Threshold, Time Period, Source Table.
- Sharing permissions:
	- Can view – read-only.	
	- Can edit – modify and potentially share.	
	- Share by user, group, or role.	
	- To allow others to share: must have Can Edit + admin/pa_admin role.

**PA Score Tables**
- pa_scores – stores collected indicator values.
- pa_snapshot – holds historical snapshots for trend analysis.
- pa_target – stores target values for breakdown elements.
