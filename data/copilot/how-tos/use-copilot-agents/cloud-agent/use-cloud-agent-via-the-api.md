# Using Copilot cloud agent via the API

You can start and manage Copilot cloud agent tasks programmatically using the REST API.

> \[!NOTE]
> The agent tasks API is in public preview and subject to change.

You can use the agent tasks API to integrate cloud agent into your own tools and workflows. For example, you can start a new task, list existing tasks, or check the status of a task.

For the full API reference, see [REST API endpoints for agent tasks](/en/rest/agent-tasks/agent-tasks).

## Authentication

The agent tasks API only supports user-to-server tokens. You can authenticate using a personal access token, a OAuth app token or a GitHub App user-to-server token.

Server-to-server tokens, such as GitHub App installation access tokens, are not supported.

## Starting a task via the API

To start a new cloud agent task, send a `POST` request to `/agents/repos/{owner}/{repo}/tasks`. The only required parameter is `prompt`, which is the prompt for the agent.

```shell copy
curl -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -H "Authorization: Bearer YOUR-TOKEN" \
  https://api.github.com/agents/repos/OWNER/REPO/tasks \
  -d '{
    "prompt": "Fix the login button on the homepage",
    "base_ref": "main"
  }'
```

Replace the following placeholder values:

* `YOUR-TOKEN`: A personal access token or GitHub App user-to-server token.
* `OWNER`: The account owner of the repository.
* `REPO`: The name of the repository.

You can also include the following optional parameters in the request body:

* `base_ref`: The base branch for the new branch and pull request.
* `model`: The AI model to use for the task. If omitted, auto model selection is used. For more information about supported models, see [REST API endpoints for agent tasks](/en/rest/agent-tasks/agent-tasks).
* `create_pull_request`: A boolean that determines whether to create a pull request for the task.

## Listing tasks

You can list tasks for a specific repository or across all repositories you have access to.

To list tasks for a specific repository:

```shell copy
curl -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -H "Authorization: Bearer YOUR-TOKEN" \
  https://api.github.com/agents/repos/OWNER/REPO/tasks
```

To list your tasks across all repositories:

```shell copy
curl -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -H "Authorization: Bearer YOUR-TOKEN" \
  https://api.github.com/agents/tasks
```

## Checking the status of a task

To check the status of a specific task, send a `GET` request with the task ID:

```shell copy
curl -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -H "Authorization: Bearer YOUR-TOKEN" \
  https://api.github.com/agents/repos/OWNER/REPO/tasks/TASK-ID
```

Replace `TASK-ID` with the ID of the task you want to check. You can get this ID from the response when you create a task or list tasks. The response includes the task's current `state`, which can be one of: `queued`, `in_progress`, `completed`, `failed`, `idle`, `waiting_for_user`, `timed_out`, or `cancelled`.

## Further reading

* [REST API endpoints for agent tasks](/en/rest/agent-tasks/agent-tasks)
* [About GitHub Copilot cloud agent](/en/copilot/concepts/agents/cloud-agent/about-cloud-agent)
* [Starting GitHub Copilot sessions](/en/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions)