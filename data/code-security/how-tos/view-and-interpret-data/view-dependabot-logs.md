# Viewing Dependabot job logs

Access job logs to troubleshoot failed Dependabot updates and understand what is happening.

When Dependabot updates fail or behave unexpectedly, job logs show you exactly what happened. Access job logs from the dependency graph to debug issues quickly. For background on what job logs contain and the types of jobs GitHub records, see [Dependabot job logs](/en/code-security/concepts/supply-chain-security/dependabot-job-logs).

## Viewing Dependabot job logs

The Dependabot job logs list is accessible from the dependency graph tab in your repository.

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled with a graph icon and "Insights," is outlined in orange.](/assets/images/help/repository/repo-nav-insights-tab.png)
3. In the left sidebar, click **Dependency graph**.
   ![Screenshot of the "Dependency graph" tab. The tab is highlighted with an orange outline.](/assets/images/help/graphs/graphs-sidebar-dependency-graph.png)
4. Under "Dependency graph", click **Dependabot**.
5. To the right of the name of manifest file that you're interested in, click **Recent update jobs**.
6. Optionally, to see the full logs files for a particular job, click **view logs**.

   ![Screenshot of a Dependabot job log entry for the Gemfile package manager. A button, called "View logs", is highlighted in a dark orange outline.](/assets/images/help/dependabot/dependabot-job-logs.png)