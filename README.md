# Python For Data Analysis Beginner Level

## The Analysis

### 1. What are th emost demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtred out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills i should pay attention to depending on the role i am targeting.

View my notebook with detailed steps here: 
[2_skills_count.ipynb](2_skills_count.ipynb)

*code to be visualized*

```python
fig, ax = plt.subplots(len(job_titles), 1, figsize=(12, 8))

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    # df_plot.plot(kind='barh', x='job_skills', y='skill_percent', ax=ax[i], title=job_title)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='viridis')
    ax[i].set_xlabel('Skill Percentage')
    ax[i].set_ylabel('')
    ax[i].invert_yaxis()
    ax[i].legend().set_visible(False)
# print each %
    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.1f}%', va='center')
fig.suptitle('Likelihood of Skills for Each Job Title in US', fontsize=16)

plt.tight_layout()
plt.show()
```

*reslut of this code*

![visualize the likelihood](images\likelyhood.png)

**Insights**

* Python is verstile skill, highly demanded across all three roles, but most prominently for Data scientist (72%) and Data engineers (65%).
* SQL is the most requested skill for Data analysts and Data scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 68% of job postings.
* Data engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected tp be proficient in more general data management and analysis tools (Excel, Tableau)

