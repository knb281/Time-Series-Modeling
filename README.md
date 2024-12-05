# Business Problem and Project Objective
Introduction:
Swire Coca-Cola
Predictive Maintenance Problem Statement Kathryn O’Connor - Kimberly Buesser
Griffin Brown - Kyle Anderson
 Swire Coca-Cola is a major bottling partner of The Coca-Cola Company in the Western United States. Swire operates 6 production plants across 13 states which support distribution, marketing, and production of Coca-Cola products.
 
Problem Statement:
As the primary bottler of Coca-Cola products in the Western United States, Swire Coca-Cola's operational efficiency affects the entire distribution network. Despite achieving 94% mechanical efficiency, unforeseen machine breakdowns and inadequate predictive maintenance lead to significant downtime. This shortfall in meeting demand results in an annual loss of approximately $60 million in uncaptured revenue. The current process—issuing work orders, waiting for parts, and making repairs—often lacks the foresight to prevent these downtimes, leading to extended production stoppages and impacting overall performance.

Benefit of a Solution:
By implementing a predictive maintenance solution, Swire Coca-Cola can reduce unplanned downtimes, improve production efficiency, and avoid costly interruptions. A solution would enable the company to:
• Anticipate machine failures before they occur
• Stock necessary parts in advance, reducing repair time
• Optimize machine usage schedules to balance output and machine wear
• Increase production output to meet demand

Success Metrics:
Stakeholders will judge the success of the project based on:
 Reduction in Downtime: A decrease in both the frequency and duration of unplanned maintenance
 Cost Savings: Reduction in maintenance-related costs, aiming to recover a portion of the $60 million annual loss
 Predictive Accuracy: Accurate prediction of breakdowns and reduced time-to-repair.
 Operational Efficiency: Enhanced machine uptime and overall production efficiency

Analytics Approach:
Utilizing the data from Swire, the focus will be to develop a deep understanding of the data and develop actionable insights. Major focuses include:
• Patterns: Follow the methodology of Survivorship Bias - What failed and what didn’t fail?
• Statistics: Exploratory data analysis to understand and visualize patterns between variables
• Predictive Modeling: Develop a model that predicts line failures to increase plant productivity

Scope of Project:

• In Scope:
• Analysis of line downtime data and its impact on production
• Recommendations for maintenance scheduling and parts inventory
• Creative production strategies to manage downtime
• Development of a predictive model for machine failures

• Out of Scope:
• Analysis of machine sensor data
• Issues unrelated to mechanical failures
• Future Considerations:
• Potential integration with sensor data
• Additional production line data

# Solution
Using a Prophet Model to Identify Maintenance Time Anomalies in a Coca-Cola Bottling Plant

Prophet, an open-source time series forecasting tool developed by Facebook, is well-suited for detecting anomalies in maintenance time data in a production line due to its robustness to missing data, ease of parameter tuning, and ability to capture seasonality and trends. Here’s how it can be applied to a Coca-Cola bottling plant:

Objective
The goal is to identify maintenance time anomalies that deviate significantly from the expected patterns. Anomalies could indicate issues such as equipment malfunctions, inefficiencies, or scheduling problems that need further investigation.

Steps for Implementation

1. Data Collection and Preprocessing

Data Collection: Gather historical data on maintenance times, including:
Timestamps of maintenance events.
Duration of each maintenance event.
Type of maintenance (preventive or corrective).
Preprocessing:
Aggregate maintenance durations to a suitable frequency (e.g., daily or weekly totals).
Handle missing data by interpolation or imputation.

2. Model Training with Prophet

Decompose Time Series:
Prophet automatically decomposes the time series into trend, seasonality, and residual components.
Bottling plants often have cyclical patterns, e.g., higher activity during peak seasons or at specific times of the day/week.
Train the Model:
Train Prophet on historical maintenance data to capture regular patterns of maintenance time.
Specify additional regressors if external factors influence maintenance times (e.g., machine usage, production volume, or staff availability).

3. Forecast Expected Maintenance Times

Use Prophet to forecast maintenance times over the desired period.
Include confidence intervals to represent the expected range of normal behavior.

4. Anomaly Detection

Compare Actual vs. Forecasted Values:
Identify anomalies by calculating residuals (difference between actual and forecasted maintenance times).
Mark data points outside the forecasted confidence intervals as anomalies.
Thresholds:
Set thresholds based on the plant's tolerance for deviations.

Advantages

Adaptability:
Automatically adjusts to changes in seasonality or trend patterns.

Transparency:
Decomposition makes it easy to explain detected anomalies.

Scalability:
Can be extended to monitor multiple production lines or machines.
Applications in the Coca-Cola Bottling Plant

Predictive Maintenance:
Use anomaly detection to proactively schedule maintenance before severe issues occur.

Process Optimization:
Identify bottlenecks or inefficiencies in the production process.

Resource Allocation:
Optimize the workforce and spare parts inventory by understanding maintenance trends.

Challenges

Data Quality: Missing or incorrect data can lead to inaccurate forecasts.
External Factors: Unforeseen events (e.g., power outages, staff shortages) might not be accounted for by the model.
Granularity: Ensuring the data aggregation level aligns with the operational needs of the plant.

Conclusion
Implementing Prophet for maintenance anomaly detection in a Coca-Cola bottling plant can enhance operational efficiency by identifying irregularities promptly. This allows the plant to minimize downtime, improve machine reliability, and sustain production targets.

# Contribution
First off, I came up with the idea of using a time series model to identify anomalies in maitenance time in order to preemptively fix equipment before it results in a signficant increase in downtime. I began this analysis by reviewing the time series trends for certain functional area nodes to become familiar with how the plant worked and what the trends in breakdowns were. This allowed me to understand that each plant has a can and a bottle line that equate for the majority of maitenance time.

From there I became curious about how to identify the piece of equipment that caused the maitenance time on the production line. So I thought to compare time series trends, from a breakdown (canline or bottleline) to a piece of equipment (comparing functional area node to equipment description). I did this using a pearson correlation and was easiy able to identify the pieces of equipment that were most highly correlated with the line downtime. I ran Prophet models on each piece of equipment that was highly correlated with the line downtime to idetify the exact piece of equipment that was causing the downtime. This helped us identify the piece of equipment causing the line downtime and therefore prescribe replacement for that specific equipment to reduce future line downtime. 

Lastly I identified the plant, line and pieces of equipment we should drill down into in order to show a full view into how our model can begin at a very general overarching view and from there can automatically identify specific equipment that needs replacing. 

I wrote all the code for these parts (the entire first half of the project) and provided visuals and iterated on the models to create better outputs.

# Business Value
We created a model the accurately identifies when a line has an anomalous amount of maitenance time and then identify the piece of equipment that is causing the downtime. From there we can prescribe maitenance in order to ensure this piece of equipment doesn't cause future downtime. This will reduce production line downtime and therefore increase the profitability of the plant. Running this analysis weekly will allow the plant to understand more clearly what pieces are breaking down and potentially identify areas for improvement in relation to equipment manufacturing (if a certain piece of equipment is the main cause for production line downtime, maybe make this piece of equipment more durable). Griffin created a dashboard that identified the actual improvement in maitenance time for the piece of equipment that we drilled down into in our presentation. Our project has direct correlation to time and money savings. This is how we provide business value through our modeling.

# Difficulties
Our team had few technical difficulties throughout the project. Griffin and I lead the technical parts of the project and our technical abilities combined with our strong communication allowed us to progress quickly through the modeling and other technical aspects of the project. The fact that we were each able to fully analyze and model the data in our own creative ways allowed us to develop individual ideas that improved the end product. Potentially communicating exactly what we had done and how it correlated to eachothers models was one of the biggest struggles that we had, however this was overcome smoothly via meetings. Truly the biggest struggle our team had was working with a member who was unwilling to take the time to understand what we were doing which resulted in the rest of us taking extra time attempting to educate this member of our team which wasted our time and took time from us developing improved or additional outputs.

# Take Aways
The most important thing that I learned/will take away from this project is allowing myself to think creatively about a problem. In this scenario, we were given data different from what was originally presented, had a large amount of missingness and was not overly explained. Therefore we really had to be flexible and create our own understanding of the data and how it correlated to the business problem. Rather than getting bogged down by the factors above, I took it as an opportunity to work with what was available, and in this scenario, I knew that with the amount of missingness, the best way to get significant enough amount of data to come up with a strong model we would have to aggregate at some level. The initial thought I had was to aggregate on a period basis because truly what the plant depends on is their machine working today, and in this case time is very important. 

I also learned how to take a step back from the specifics of my code to be able to explain to a group of people what is the idea behind the code. This was actually much more difficult than expected, as when you are developing you can easily process the steps and how they relate, but when you try to explain that process to someone else who was not there when you were developing, it becomes much more difficult to communincate the process and why you made certain decisions. This will inevitably help me as I continue working in technical roles. 

# EDA
This notebook provides general overview of dataset and further look into important variables. It identifies time series trends to further investigate.
# Modeling
Swire Modeling: This is the initial modeling notebook that begins iterating on the Prophet time series model to create a prediction that aligns with our goal of having an anomalous amount of maitenance time flag in the model

Time Series Modeling: This looks at using different types of time series models to create a more accurate prediction. It also looks into the data as a whole to ensure it is a good fit for time series modeling.

Final Swire Modeling: This uses the best fit model drilling down into the line and correlated equipment.
