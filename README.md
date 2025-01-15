# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles in Singapore?

To find the most demanded skills for top 3 data roles in Singapore through filtering out those positions by which ones were the most popular and got the 5 top skills for the top 3 roles. This query highlights the most popular job titles and their top skills showing
which skills I should pay attention to depending on the tole I'm targeting.

View my notebook with detailed steps here: [2_skills_count.ipynb](3_project/2_skills_count.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(job_titles), 1)

for index, job_title in enumerate(job_titles):
    df_plot = df_skills_count[df_skills_count['job_title_short'] == job_title].head(5)
    df_plot.plot(kind='barh', x='job_skills', y='skill_count', ax=ax[index], title= job_title)
    ax[index].invert_yaxis()
    ax[index].set_ylabel('')
    ax[index].legend().set_visible(False)

fig.suptitle('Counts of Top Skills in Job Posting', fontsize = 15)
fig.tight_layout(h_pad=1)
plt.show()
```
### Results

![Visualization of top skills for Data Nerds](3_project/images/skill_demand_top_3_jobs.png)


### Insights

SQL:

- Essential across all roles (55%-56% demand for Analysts and Engineers; 50% for Scientists).
- Core skill for querying and managing databases, crucial for data analysis, ETL processes, and dataset extraction.

Python:

- Highly demanded (47%-68%) with the most use in Data Science.
- A versatile tool for data analysis, automation, machine learning, and big data processing.

Excel:

- Key skill for Data Analysts (35% demand).
- Used for organizing, analyzing, and visualizing data, but less relevant for Engineers and Scientists.


# The Analysis

## 2. How are in_demand skills trending for Data Analysts?

To analyse the top 5 trending skills of Data Analyst in Singapore which were filtered through the month in dataframe.
Using the explode method which converted the job_skills into list that helped to seperate the data, and assigned the data to the index values. Finally we got the top 5 trending skills of Data Analyst role.

view my notebook to see my detailed steps here:[3_trending_skills](3_project/3_trending_skills.ipynb)

### Visualize Data

```python 
df_plot = df_da_sg_perc.iloc[:, :5]

sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills for Data Analysts in the Sg')
plt.ylabel('Likelihood in Job Postings')
plt.xlabel('2023')
plt.legend().remove()

from matplotlib.ticker import PercentFormatter
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))
```
### Results
![Visualization of top trending skills for Data Analyst role](3_project/images/trending_skills.png)

### Insights

SQL (51%)

- The most consistently demanded skill across the year.
- Peaks in the middle of the year but shows a gradual decline toward December.
- Essential for querying and managing databases, making it a core skill for Data Analysts.

Python (46%)

- Maintains strong demand throughout the year with minor fluctuations.
- Slight decline in the latter half of the year.
- A versatile tool for data analysis, automation, and visualization.

- Excel (30%) and Tableau (30%)

- Both exhibit similar demand trends, with fluctuations throughout the year.
- Demand decreases slightly in the second half of the year.
- Excel is crucial for organizing and analyzing data, while Tableau is vital for creating interactive visualizations.

R (21%)

- Least demanded skill among the listed ones.
- Demand remains stable with minimal variation.
- Primarily used for statistical analysis and niche modeling tasks.

