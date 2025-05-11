# Call-Center-Performance-Dashboard
Tracking Agent Efficiency &amp; Customer Queries

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/call%20centre%20image.jpg)

## Table Of Content
 - [Introduction](#Introduction)
 - [ASK](#ASK)
 - [PREPARE](#PREPARE)
 - [PROCESS](#PROCESS)
 - [ANALYZE](#ANALYZE)
 - [SHARE](#SHARE)
 - [ACT](#ACT)

---
## Introduction

In today’s fast-paced customer service environment, call centers play a crucial role in handling customer queries efficiently. However, managing call volumes, tracking agent performance, and identifying areas for improvement can be challenging.

This project focuses on analyzing call center activities to provide insights into agent performance, call volume trends, and customer interactions. By leveraging data, we aim to determine the best and worst-performing agents, track the number of calls received, and assess overall efficiency.

With a data-driven approach, this dashboard helps stakeholders optimize call center operations, improve customer satisfaction, and enhance agent productivity.

---

## ASK

### Objectives
* How well are agents performing? → Identify top-performing and underperforming agents based on call volume and resolution rates.
* How many calls are being handled? → Analyze the total number of calls received across different companies and query types.
* Are customer queries being resolved efficiently? → Assess how effectively agents handle queries and escalate issues.
* What challenges exist in the call process? → Identify bottlenecks and suggest strategies for better call management.
* How can call center operations be optimized? → Use data insights to enhance workflow, agent training, and overall customer service quality.

---

## Prepare

### Data Collection & Methodology
This dataset was specifically created for the Lagos Tableau User Group Bootcamp, aiming to project focuses on analyzing call center activities to provide insights into agent performance, call volume trends, and customer interactions.

### Dataset Overview
The dataset consists of 2000 Rows and 15 key columns, including:

* Call ID: A unique identifier for each call, ensuring no duplication and enabling easy tracking of call records.
* Customer Company Name: Indicates the name of the company or organization the customer represents, helping to categorize and segment calls by client.
* Sentiment: Reflects the overall tone of the conversation (e.g., positive, negative, or neutral), often derived from agent feedback or sentiment analysis tools.
* CSAT Score: A numerical measure of Customer Satisfaction, typically collected through post-call surveys or direct feedback.
* Call Timestamp: The date and time when the call took place, useful for time-based analyses such as peak calling hours or seasonal trends.
* Reason: Describes the purpose of the call or the query raised by the customer (e.g., technical support, billing inquiry, product complaint).
* City: Indicates the city from which the customer is calling or where the service is being requested, aiding geographic segmentation.
* State: Shows the state or region associated with the call, allowing for broader location-based analysis.
* Channel: Specifies the communication channel used (e.g., call centre, chatbot), highlighting how customers reach out for support.
* Response Time: The time taken by an agent to respond to the call, reflecting the efficiency of the call center in addressing incoming inquiries.
* Call Duration (in Minutes): The total length of the call, measured in minutes, which can be used to assess agent performance and call complexity.
* Call Center: Identifies the call center location or name responsible for handling the call, useful for comparing performance across different centers.
* First Contact Resolution (FCR) Flag: Indicates whether the customer’s issue was resolved on the first contact (Yes/No), a key metric for measuring call effectiveness.
* Abandon Flag: Marks whether the call was abandoned by the caller before connecting or being resolved (Yes/No), highlighting potential service gaps.
* Agent: The name or ID of the agent who handled the call, crucial for performance evaluation and accountability.

---

## Process

### Data Transformation Process
To prepare the dataset for analysis, I used Microsoft Excel for an initial review, ensuring data cleanliness, and Tableau for visualization. The dataset contains both categorical (qualitative) and numerical (quantitative) data, including string, numerical, and boolean values.

In **Tableau**, I created parameters and the following calculated fields also organized them into respective folders:

* Incoming Call
* Average Talk Time
* Customer Satisfaction (C Sat)
* First Contact Resolution Call (FCRC)

#### Incoming Call Folder
* Incoming call: COUNT([Call ID]).
* calculated Current Month (CM) Incoming Call:
COUNT(IF [Current Month] = MONTH([Call Timestamp])
THEN [Call ID]
END).
* Previous Month (PM) Incoming call: COUNT(IF [Current Month] -1 = MONTH([Call Timestamp])
THEN [Call ID]
END).
* Month over Month (MOM) Incoming call: [CM Incoming Call]/[PM Incoming Call]-1.
MOM color: SIGN([MOM Incoming Calls]).

#### Average Talk Time Folder
* Average Talk Time: AVG(IF [Abandon Flag] != ‘Y’
THEN [Call Duration (in Minutes)]
END).
* CM Avg Talk Time: AVG(
IF[Current Month]= MONTH([Call Timestamp])
AND [Abandon Flag] != ‘y’
THEN [Call Duration (in Minutes)]
END).
* PM Avg Talk Time: AVG(
IF[Current Month]-1 = MONTH([Call Timestamp])
AND [Abandon Flag] != ‘y’
THEN [Call Duration (in Minutes)]
END).
* MOM Avg Talk Time: [CM Avg Call]/[PM Avg Call]-1
* MOM Avg talk Color: SIGN([MOM Avg Talk Time]).

#### Csat Score Folder
* CM Csat Score: AVG(IF[Current Month]= MONTH([Call Timestamp])
AND [Abandon Flag] != ‘y’
THEN [CSAT Score]
END).
* PM Csat Score: AVG(IF[Current Month]-1 = MONTH([Call Timestamp])
AND [Abandon Flag] != ‘y’
THEN [CSAT Score]
END).
* Avg Csat Score: AVG(IF [Abandon Flag] != ‘Y’
THEN [CSAT Score]
END).
* MOM Csat Score: [CM Cast Call]/[PM Csat Call]-1
* MOM Csat Score Color: SIGN([MOM Cast Call])

#### FCRC Folder
* FCRC: COUNT( IF[First Contact Resolution (FCR) Flag] = ‘Y’
AND [Abandon Flag] != ‘Y’
THEN [Call ID]
END)
* CM FCRC: COUNT(IF[Current Month]= MONTH([Call Timestamp])
AND([First Contact Resolution (FCR) Flag]) = ‘Y’
AND [Abandon Flag] != ‘Y’
THEN [Call ID]
END)
* PM FCRC: COUNT(IF[Current Month]-1 = MONTH([Call Timestamp])
AND([First Contact Resolution (FCR) Flag]) = ‘Y’
AND [Abandon Flag] != ‘Y’
THEN [Call ID]
END)
* MOM FCRC: [CM FCRC Call]/[PM First Contact Resolution Call ]-1
* MOM FCRC Color: SIGN([MOM FCRC])

These transformations allowed for better structuring and analysis of key performance indicators.

---

## Analyze

### Data Exploration And Key Insight

This dashboard provides a comprehensive performance analysis of the call center in March, focusing on key performance indicators (KPIs), reasons for calls, agent performance, and call distribution patterns.

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/Call%20Kpi.png)

#### KPI Overview (Top Metrics)
* Incoming Calls: 195 (🔼 54.8% increase vs previous month). The number of incoming calls has significantly increased compared to last month, indicating a rise in customer engagement or issues.
* Average CSAT Score: 3.3 (🔼 9.2% increase vs previous month). Customer satisfaction has improved, possibly due to better service handling or quicker resolutions.
* First Contact Resolution Calls (FCRC): 46 (🔼 58.6% increase vs previous month). More calls are being resolved on the first contact, reducing the need for follow-ups and enhancing efficiency.
* Average Talk Time: 31.08 minutes (🔼 16.7% increase vs previous month). Agents are spending more time on calls, which could indicate either better problem resolution or longer issue-handling time.

#### Call Reasons & Customer Issues

##### Top 3 reasons for incoming calls:

* New Service Inquiry: 54 calls
* Technical Support: 52 calls
* Payment Issues: 45 calls

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/Top%205%20Reason.png)

➝ Insight: The majority of calls are from customers inquiring about new services and seeking technical support, highlighting the need for proactive customer communication and possibly an improved self-service option.

#### Percentage breakdown of call issues:

* 73% of calls are for new service inquiries.
* 43% are technical support-related.
* 37% are payment-related.
* Only 4% are about billing questions.

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/%25%20Of%20Issue%20By%20Income%20Calls.png)

➝ Insight: A focus on enhancing self-service FAQs for new service inquiries and payments could help reduce call volume.

#### Agent Performance Analysis
Top Agent Handling Calls:

* Sophia Garcia (34 calls)
* John Smith (32 calls)
* Linda Chen (25 calls)

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/Top%205%20Agent%20By%20Metrics.png) 

#### First Contact Resolution (FCRC) Rate by Agent:

* Sophia Garcia: 19 successful FCR calls
* John Smith: 11 successful FCR calls
* Linda Chen: 4 successful FCR calls

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/FCRC.png)

➝ Insight: Sophia Garcia is the best-performing agent in both handling calls and resolving issues on the first attempt, while Daniel Lee had 0 FCR calls, suggesting a potential performance gap.

#### Call Volume & Activity Patterns
##### Time Distribution of Incoming Calls (Heatmap Analysis)

* High call activity is concentrated between 7 AM and 5 PM.
* Peak call times appear to be around 7 AM, 5 PM, and 7 PM.

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/Heatmap%20Activities%20By%20incoming%20calls.png)

➝ Insight: Staffing resources should be optimized during peak hours to minimize wait times and improve efficiency.

#### Day of the Week Analysis

* Calls are evenly spread across the week, with noticeable spikes on Wednesdays and Fridays.

➝ Insight: Additional staff Agent or extended service options may be necessary on these peak days.

---

## Share

#### Communicating Insights from the Dashboard

**Dashboard Creation**
I developed a Tableau dashboard to visually present key performance metrics of the Customer Call Center using:

* Parameter selection to dynamically choose a month for analysis.
* Pie charts to illustrate the percentage distribution of customer issues.
* Bar charts to highlight the top reasons for incoming calls.
* Heatmaps to track call volumes and activity patterns across different hours and days.
* Area charts to display trends in KPIs such as incoming calls, CSAT score, and first-contact resolution calls.

![](https://github.com/judoski366/Call-Center-Performance-Dashboard/blob/main/Call%20Center%20Dashboard.png)

**Data Storytelling**
To ensure clarity and engagement for stakeholders, I incorporated:

* Concise insights to summarize key findings and trends.
* Interactive KPIs that allow stakeholders to filter data dynamically.
* Actionable recommendations based on agent performance, customer issue trends, and operational efficiency improvements.

This dashboard empowers decision-makers to optimize call center agent workflows, enhance customer support strategies, and allocate resources effectively based on real-time data.

---

## Act

#### Key Recommendations

#### 1. Enhance Self-Service Options
* Since new service inquiries (73%) and payment issues (37%) dominate, consider adding more FAQs, chatbots, or automated call responses to handle common queries.

#### 2. Optimize Staffing & Training

* Sophia Garcia and John Smith are leading performers in resolving issues quickly.
* Daniel Lee needs coaching or training on improving first-contact resolution rates.
* Additional support should be allocated during peak call hours (8 AM — 3 PM, especially Wednesdays and Fridays).

#### 3. Monitor Talk Time Trends

* The 16.7% increase in average talk time should be analyzed further — whether it results from complex inquiries or inefficient processes.

#### 4. Improve Customer Experience & Satisfaction

* CSAT score is improving (3.3, up by 9.2%), but there is room for growth by reducing resolution time and enhancing agent response quality.

#### Final Conclusion
* The call center is seeing a significant rise in customer engagement (54.8% more calls).
* Customer satisfaction is improving, and first-contact resolution rates are up (58.6%), suggesting better issue resolution.
* Peak call hours and days require strategic staffing adjustments to maintain efficiency.
* Agent training and self-service enhancements can further optimize performance.

This dashboard provides a strong foundation for decision-making, helping improve service efficiency and customer experience.

---
## Additional Resources
**_To interact with the report, click[here](https://public.tableau.com/app/profile/jude.nwagu/viz/CallCentreDashboard_17390240892740/CUstomerCallCenterDashboard)_**


