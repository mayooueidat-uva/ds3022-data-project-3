# DS3022 Data Project 3

This data project is more open-ended than projects before it. You are asked to do something interesting with the data sources, tools, or approaches we have touched in the third block of this course. This could include fetching data from APIs and streaming sources, it could include Kafka or tools to fetch bulk data for processing.

## Project Ideas

Some ideas to use as inspiration but feel free to be creative:

- Use the **GitHub Events Archive** [https://www.gharchive.org/](https://www.gharchive.org/) and process a month's worth of activities. What types of events do you see? Make a visualization representing shifts or trends in this data, and explore unique dynamics across event types. Learn more about [GitHub Event Types](https://docs.github.com/en/rest/using-the-rest-api/github-event-types?apiVersion=2022-11-28).
- Use the near real-time [**GitHub Events API**](https://docs.github.com/en/rest/activity/events?apiVersion=2022-11-28) to look at recent events for a repository, user, organization. This is a **powerful** API that offers historical data up to 30 days in the past for any specific GitHub resource. It returns a maximum of 300 records. Be aware that this API is "near real-time" meaning events in this feed are delayed by at least 5 minutes and up to 6 hours, depending upon congestion and user traffic. Learn more about [GitHub Event Types](https://docs.github.com/en/rest/using-the-rest-api/github-event-types?apiVersion=2022-11-28). A full public API of all events in GitHub [is also available](https://docs.github.com/en/rest/activity/events?apiVersion=2022-11-28#list-public-events), be sure to return 100 pages per request. (Authenticated API requests are rate-limited at 5000 requests per hour, which means a maximum of 500,000 records per hour can be retrieved. This should be more than enough.) Note from the same API documentation that stargazers (users who have starred a specific repository) can be fetched as well. See [this page](https://docs.github.com/en/rest/activity/starring?apiVersion=2022-11-28) to read more.
- Use the **Authenticated GitHub API** and analyze the event or commit history for five of the following packages to compare/contrast. How many commits happened in the last month? In the last year? Can you plot commit/PR activity for the lifetime of one project? Does the commit history for the last 3 or 6 months represent significant changes in code? How many users are represented in the last 1000 commits? (Original committers, not those who approved pull requests or bot accounts.)

    - `pandas`
    - `matplotlib`
    - `numpy`
    - `boto3`
    - `polars`
    - `seaborn`
    - `pytorch`
    - `scikit-learn`
    - `tensorflow`
    - `scipy`
    - `plotly`
    - `requests`
    - `beautiful-soup`
    - `nltk`

- Alternatively, you could refer to the [`hugovk` JSON list of the top 1000 packages](https://raw.githubusercontent.com/hugovk/top-pypi-packages/main/top-pypi-packages.json) from PyPi.
- Write a **GUI application** that takes the name of a GitHub repository as an input which generates a series of commit/contributor analyses and plots. You could represent the density of commits (adding code, removing code, etc.) Think of it as an activity dashboard generated for any repo name it is given.
- Continue to work with the **Bluesky Firehose**. Gather 100k posts or comments into Kafka and perform a simple sentiment analysis on that text. Identify the top 20 topics or tags for that time period. (Note: you could learn how to code/run this yourself using NLTK, or articles like this from Hugging Face. Or, this might be something LLMs are quite good at. Can you submit your request to the ChatGPT or Claude API via code?)
- Continue to work with the **Wikipedia Event Stream**. What interesting trends do you find when you gather 50k messages?
- Work with data from **other open APIs and data streams**. There are many to choose from [here](https://github.com/bytewax/awesome-public-real-time-datasets) as well as more listed in Module 0.

## Good Sources / Worthy Projects

What does "something interesting" look like? Here are some criteria to use when deciding on a good data source and deliverables:

- **Scale & Complexity**
    - Processing of substantial data volumes (50K+ records minimum, ideally 100K-1M+)
    - Multiple data transformation steps beyond simple filtering
    - Handling of real-world messiness: missing values, inconsistent formats, rate limits, API pagination
    - Evidence that the data presented genuine engineering challenges, not just a single API call
- **Technical Depth & Tool Integration**
    - Use of at least 2-3 modern data engineering tools from the course (streaming platforms, workflow orchestrators, databases, containerization)
    - Thoughtful tool selection with clear rationale for why each was chosen
    - Evidence of proper data pipeline architecture (ingestion → processing → storage → analysis)
    - Code that demonstrates understanding beyond copy-pasting tutorials
- **Insight Generation Beyond Description**
    - Analysis that reveals non-obvious patterns or trends
    - Goes beyond "here's what the data looks like" to "here's what the data means"
    - Comparative analysis, temporal trends, anomaly detection, or predictive elements
    - Clear articulation of at least one surprising or counterintuitive finding
    - Visualizations that illuminate patterns humans couldn't spot in raw data
- **Real-World Relevance & Domain Context**
    - Connection to actual problems or questions people care about
    - Domain knowledge application (understanding what the data represents, not just treating it as abstract numbers)
    - Consideration of data quality, bias, or limitations in interpretation
    - Potential implications or applications of the findings
    - Context that shows why this analysis matters to developers, businesses, or society
- **Reproducibility & Documentation**
    - Clear setup instructions that enable others to run the pipeline
    - Well-organized repository structure with logical separation of concerns
    - Environment specifications (requirements.txt, docker-compose.yml, etc.)
    - Meaningful code comments explaining why decisions were made, not just what the code does
    - Discussion of challenges encountered and how they were overcome
    - Honest acknowledgment of limitations or trade-offs
- Draws upon skills and underastanding from other courses.
- Each team member should plan on contributing an estimated 6-10 hours total for this project.

**Weak project**: "We collected 10,000 GitHub stars and made a bar chart of their programming languages"

**Strong project**: "We ingested the full history of commits for 5 data science packages, used DuckDB to identify repos with emerging velocity changes in commits, discovered that repos emphasizing 'performance' gained both commits and stars 3x faster in machine learning while 'simplicity' messaging dominated in plotting and viz tools, then built a Prefect workflow that could monitor this in real-time for trend detection for any specific repo."

You may work with up to ONE (1) partner on this project. Any student in either DS3022 section can be your partner. You may also choose to work alone.

## Other notes and comments:

- Teams should work independently (no cross-team collaboration).
- Both team members should contribute code to the same repository. You may add a teammate to a repository by going to Settings -> Collaborators & Teams.
- Your work should be in python, should be contained in a separate repository (not your fork of the DP3 repository, only use that for your findings) and demonstrate all the usual normal expectations - comments, error handling, and logging.
- You may use your own laptop or Amazon EC2 instance for computational resources. Be mindful of costs!
- ADULT CONTENT - Be aware that analysis on social media data comes with the risk of exposure to content for mature audiences. This can be ignored or filtered out if desired.
- Your solution does not need to automate the entire process end-to-end (data collection, analysis, plots, etc.) in a single script, but should require no manual edits, cleaning, copy+paste, or other manual steps (beyond running a series of scripts in a specific order) in order to reproduce your work.


## Submission

Your group/team will write up a one page summary of your work, written in markdown, which should include:

1. The names of your team members.
2. What data source did you work with?
3. What challenges did this data choice present in data gathering, processing and analysis, and how did you work through them? What methods and tools did you use to work with this data?
4. Offer a brief analysis of the data with your findings. Keep it brief, clear, and meaningful. 
5. Include at least one compelling plot or visualization of your work.
6. Link to your project GitHub repository.

To submit your team's summary, fork this repository, then copy the "sample" directory in your fork give it a unique name. Next, edit the README.md file within that directory and include/embed your plots in that directory and in the README file as needed. Finally, submit a pull request for your changes to be incorporated back into the upstream source. Only one pull request per team is necessary.

**Submissions are due by 11:59pm on Monday, November 24, 2025.**

## Grading Rubric

A rough breakdown of the 50 points available in this project:

- Choice of data source (10 points)
- Effort and technical agility in data consumption, transformation, and loading (15 points)
- Quality of analysis and unique approaches (10 points)
- Results, plots, meaningful insights (10 points)
- Overall cohesiveness, originality, and focus of the project (5 points)

## Judging & Prizes 🏆
After completion students and TAs will vote for their top 3 projects and there will be a prize for the top voted project in each section. (And I mean a _real_ prize.)

