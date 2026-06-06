# Exporting a software bill of materials for your repository

You can export a software bill of materials or SBOM for your repository from the dependency graph. SBOMs allow transparency into your open source usage and help expose supply chain vulnerabilities, reducing supply chain risks.

You can export the current state of the dependency graph for your repository as a software bill of materials (SBOM) using the industry standard [SPDX](https://spdx.github.io/spdx-spec/v2.3/) format.

SBOMs include an inventory of a project's dependencies and associated information such as versions, package identifiers, licenses, transitive paths, and copyright information. SBOMs do not include dependents (other projects that rely on your project).

## Exporting a software bill of materials for your repository from the UI

1. On GitHub, navigate to the main page of the repository.
2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-graph" aria-label="graph" role="img"><path d="M1.5 1.75V13.5h13.75a.75.75 0 0 1 0 1.5H.75a.75.75 0 0 1-.75-.75V1.75a.75.75 0 0 1 1.5 0Zm14.28 2.53-5.25 5.25a.75.75 0 0 1-1.06 0L7 7.06 4.28 9.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.25-3.25a.75.75 0 0 1 1.06 0L10 7.94l4.72-4.72a.751.751 0 0 1 1.042.018.751.751 0 0 1 .018 1.042Z"></path></svg> Insights**.

   ![Screenshot of the main page of a repository. In the horizontal navigation bar, a tab, labeled with a graph icon and "Insights," is outlined in orange.](/assets/images/help/repository/repo-nav-insights-tab.png)
3. In the left sidebar, click **Dependency graph**.
4. On the top right side of the **Dependencies** tab, click **Export SBOM** to generate an SBOM file for download from your browser.

## Exporting a software bill of materials for your repository using the REST API

If you want to use the REST API to export an SBOM for your repository, see [REST API endpoints for software bill of materials (SBOM)](/en/rest/dependency-graph/sboms#export-a-software-bill-of-materials-sbom-for-a-repository).

## Generating a software bill of materials from GitHub Actions

The following actions will generate an SBOM for your repository and attach it as a workflow artifact which you can download and use in other applications. For more information about downloading workflow artifacts, see [Downloading workflow artifacts](/en/actions/managing-workflow-runs/downloading-workflow-artifacts).

| Action                                                                                                        | Details                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [SPDX Dependency Submission Action](https://github.com/marketplace/actions/spdx-dependency-submission-action) | Uses [Microsoft's SBOM Tool](https://github.com/microsoft/sbom-tool) to create SPDX 2.2 compatible SBOMs with the [supported ecosystems](https://github.com/microsoft/component-detection/blob/main/docs/feature-overview.md) |
| [Anchore SBOM Action](https://github.com/marketplace/actions/anchore-sbom-action)                             | Uses [Syft](https://github.com/anchore/syft) to create SPDX 2.2 compatible SBOMs with the [supported ecosystems](https://github.com/anchore/syft#supported-ecosystems)                                                        |
| [SBOM Dependency Submission Action](https://github.com/marketplace/actions/sbom-submission-action)            | Uploads a CycloneDX SBOM to the dependency submission API                                                                                                                                                                     |