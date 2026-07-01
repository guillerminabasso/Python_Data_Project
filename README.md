# The Analysis
## 1. What are the most demanded skills for the 3 most popular data roles?

To find the most demanded skills for the top 3 most popular jobs I filtered out those positions by which one were the most popular (more appearances on the dataset), and got the top 5 skills for those roles.
This query highlights the most popular roles and the 5 top skills associated to them, showing what skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: 
[2_Skills_Demand.ipynb](2_My_Project\2_Skills_Demand.ipynb)

### Visualizing Data 

```python
fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
   df_plot = df_percent_skills[df_percent_skills['job_title_short'] == job_title].head(5)
   sns.barplot(data=df_plot, x='skills_percent', y='job_skills', ax=ax[i], hue='skills_count')
   ax[i].set_title(job_title)
   ax[i].set_xlabel('')
   ax[i].set_ylabel('')
   ax[i].legend().set_visible(False)
   ax[i].set_xlim(0,78)
   
   for n, v in enumerate(df_plot['skills_percent']):
      ax[i].text(v + 1, n, f'{v:.0f}%', va='center')
   
   if i != len(job_titles) - 1:
      ax[i].set_xticks([])

plt.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=16)
plt.tight_layout(h_pad=0.5)
plt.show()

```
### Results

![Visualization of Top Skills for Data Roles](2_My_Project\images\skill_demand.png)

### Insights

* Python is one of the most important skills for **Data Engineers** and **Data Scientists**, while it is less common in **Data Analyst** roles, appearing in about **27%** of Data Analyst job postings.
* SQL is a key skill across all three roles, showing how essential it is for working in data.
* Cloud technologies are especially important for **Data Engineer** positions, where working with cloud platforms is a common requirement.
* For **Data Analyst** roles, **Excel** and **data visualization tools** are the second and third most requested skills, highlighting their importance for data analysis and reporting.


