# The Analysis 
## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most popular demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing whcih skills I shoudl pay attention to depending on the role I'm targeting. 

View my notebook with detialed steps here : [Skills_Count.ipynb](Skills_Count.ipynb)
### Visualize Data
```python 
fig, ax = plt.subplots(len(job_titles),1)

sns.set_theme(style='ticks')

for i , job_title in enumerate(job_titles):
  df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
  #df_plot.plot(kind='barh',x='job_skills',y='skill_percent',ax =ax[i],title=job_title)

  sns.barplot(data=df_plot, x='skill_percent',y='job_skills',ax=ax[i], hue='skill_count',palette='dark:b_r')
  ax[i].set_title(job_title)
  ax[i].set_ylabel('')
  ax[i].set_xlabel('')
  ax[i].get_legend().remove()
  ax[i].set_xlim(0,80)
  for n,v in enumerate(df_plot['skill_percent']):
    ax[i].text(v+1,n,f'{v:.0f}%',va='center')
  if i != len(job_titles) -1:
    ax[i].set_xticks([])
fig.suptitle('Likelihood of Skills Requested in the US job Postings',fontsize = 20)
fig.tight_layout(h_pad=.5)
plt.show()
```
### Results 

![Visulization of Likelihood of skills Requested in data jobs in the US]
![alt text](images/Likelihood_of_skills.png)


### Insights 
Data Analyst:

SQL is the most requested skill, appearing in 51% of job postings. This indicates that SQL is essential for Data Analysts, highlighting its importance in querying and managing databases.
Excel follows with a significant 41% demand, showing its relevance for data manipulation and reporting.
Tableau and Python appear almost equally (28% and 27%, respectively), suggesting that both visualization and programming skills are becoming more essential for data analysis.
SAS appears in 19% of job postings, showing that while it is less commonly required, it still holds value in certain industries.

Data Engineer:

SQL and Python are dominant in this role, with 68% and 65% of job postings requesting these skills, respectively. This suggests strong proficiency in data management (SQL) and programming (Python) are crucial for Data Engineers.
AWS appears in 43% of job postings, emphasizing the importance of cloud infrastructure knowledge.
Azure and Spark both appear in 32% of postings, indicating that experience with cloud platforms and big data processing frameworks is also highly sought after.

Data Scientist:

Python is overwhelmingly the most requested skill, with 72% of job postings, indicating its central role in data science for tasks such as data manipulation, analysis, and machine learning.
SQL follows at 51%, showing its importance in database querying and managing data for analysis.
R is requested in 44% of job postings, demonstrating its continued relevance for statistical computing and data science.
Both SAS and Tableau appear equally at 24%, highlighting that while less common, these tools still have a notable presence in data science job requirements.
Overall Insights:
SQL and Python are universally in high demand across all three roles, with Python being especially critical for Data Scientists.
Cloud technologies (AWS, Azure) are becoming essential for Data Engineers, pointing to the increasing reliance on cloud infrastructure for data-related roles.
Data visualization skills (Tableau) are more prominent in Data Analyst roles, whereas programming and data processing skills (Python, Spark) are crucial for Data Scientists and Engineers.




## How are in-demand skills trending for Data Analysts?

```Python
df_plot = df_DA_US_Percent.iloc[:,:5]

sns.lineplot(data=df_plot,dashes=False,palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top SKills for Data Analysts in the US')
plt.ylabel('Likelihood in Job Posting')
plt.xlabel('2023')
plt.legend().remove()


from matplotlib.ticker import PercentFormatter
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(xmax=100,decimals=0))

for i in range(5):
  plt.text(11.2,df_plot.iloc[-1,i],df_plot.columns[i])
  ```

### Results
  ![alt text](images/Trending_Skills.png)

### Insights 
SQL:

SQL consistently remains the top requested skill, with its likelihood in job postings hovering around 60% throughout the year. While there's a slight decline from the start of the year to December, it is still the most in-demand skill for Data Analysts.

Excel:

Excel remains in steady demand, fluctuating between 40% and 45% over the year, with a notable dip in the latter part of the year before rising again in December. This suggests that spreadsheet proficiency continues to be a valuable skill, particularly for data manipulation and reporting.

Python:

Python's demand fluctuates around the 30% mark, indicating its continued importance for Data Analysts. However, its demand is notably lower than SQL, suggesting that while it's an important skill, it is less universally required compared to database skills.

Tableau:

Tableau remains consistently in demand around the 30% mark but slightly declines in the second half of the year. This suggests that visualization skills are essential but perhaps not as critical as SQL or Excel in Data Analyst roles.

Power BI:

Power BI is the least requested skill among the five, ranging between 20% and 25% throughout the year. While it is less demanded than Tableau, it still shows up in a notable portion of job postings, indicating that some employers prefer this alternative visualization tool.

Overall Insights:

SQL and Excel dominate the skills landscape for Data Analysts, with SQL being particularly essential.
Python and Tableau are both highly valued but seem to be secondary compared to SQL and Excel.
Power BI has a smaller presence but still demonstrates a significant demand, indicating that proficiency in multiple visualization tools (Power BI and Tableau) may be advantageous for Data Analysts.





