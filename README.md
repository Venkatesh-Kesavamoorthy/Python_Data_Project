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