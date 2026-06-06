# Security overview permissions

The actions you can take in security overview depend on your permissions for the repositories in your organization or enterprise.

The actions you can take in the security overview depend on your permissions for the repositories in your organization or enterprise.

## Organization-level overview

If you are an **owner or security manager** for an organization, you can see data for all the repositories in the organization in all views.

If you are an **organization or team member**, you can view security overview for the organization and see data for repositories where you have an appropriate level of access.

> \[!TIP] The Assessments view, which is not shown in the table below, is only available to organization owners and security managers.

<div class="ghd-tool rowheaders">

| Organization or team member with                                                     | Overview dashboard view                                       | Risk and alerts views                                         | Coverage view                    |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------- | ------------------------------------------------------------- | -------------------------------- |
| `admin` access for one or more repositories                                          | View data for those repositories                              | View data for those repositories                              | View data for those repositories |
| `write` access for one or more repositories                                          | View code scanning and Dependabot data for those repositories | View code scanning and Dependabot data for those repositories | No access                        |
| `read` or `triage` access for one or more repositories                               | No access                                                     | No access                                                     | No access                        |
| Security alert access for one or more repositories                                   | View all security alert data for those repositories           | View all security alert data for those repositories           | No access                        |
| Custom organization role with permission to view one or more types of security alert | View allowed alert data for all repositories                  | View allowed alert data for all repositories in all views     | No access                        |

</div>

> \[!NOTE]
> To ensure a consistent and responsive experience, for organization members, the organization-level security overview pages will only display results from the most recently updated 3,000 repositories. If your results have been restricted, a notification will appear at the top of the page. Organization owners and security managers will see results from all repositories.

For more information about access to security alerts and related views, see [Managing security and analysis settings for your repository](/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-security-and-analysis-settings-for-your-repository#granting-access-to-security-alerts) and [About custom repository roles](/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/about-custom-repository-roles#security).

## Enterprise-level overview

> \[!NOTE]
> If you are an **enterprise owner**, you will need to join an organization as an organization owner to view data for the organization's repositories in both the organization-level and enterprise-level overview. For more information, see [Managing your role in an organization owned by your enterprise](/en/enterprise-cloud@latest/admin/user-management/managing-organizations-in-your-enterprise/managing-your-role-in-an-organization-owned-by-your-enterprise).

In the enterprise-level security overview, you can see data for all organizations where you are an **organization owner or security manager**.