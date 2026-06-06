# Exploring data flow with path queries

Detect potential vulnerabilities by running path queries and analyzing your data flow.

## Prerequisites

Before you can effectively use path queries, you should understand the basics of data flow analysis. See [About data flow analysis](https://codeql.github.com/docs/writing-codeql-queries/about-data-flow-analysis/) in the CodeQL documentation.

## Running path queries in VS Code locally

1. Open a path query in VS Code. A path query is a CodeQL query with the property `@kind path-problem`.
2. Right-click in the window with the query open, then select **CodeQL: Run Query on Selected Database**. Alternatively, you can also run this from the VS Code Command Palette.
3. Once the query has finished running, you can see the results in the "Results" view (under `alerts` in the dropdown menu). Each query result describes the flow of information between a source and a sink.
4. Expand the result to see the individual steps that the data follows.
5. Click each step to jump to it in the source code and investigate the problem further.

## Next steps

You can use the "Variant Analysis Repositories" view to run a query against up to 1,000 repositories on GitHub.com. See [Running CodeQL queries at scale with multi-repository variant analysis](/en/code-security/codeql-for-vs-code/getting-started-with-codeql-for-vs-code/running-codeql-queries-at-scale-with-multi-repository-variant-analysis).

To start writing your own path queries, see [Creating path queries](https://codeql.github.com/docs/writing-codeql-queries/creating-path-queries/#creating-path-queries) in the CodeQL documentation.