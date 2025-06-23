# `git-create-jira-branch`

This script automates the creation of a new Git branch based on a Jira ticket. It fetches the Jira ticket summary and generates a branch name in the format:  
`your_username/BOARD-123/ticket-summary-in-kebab-case` 
this template can be edited also to include only the jira ticket title.

## Features

- Fetches Jira ticket details using the Jira API.
- Automatically creates a new branch with a descriptive name based on the ticket summary.
- Handles errors for authentication, missing tickets, and configuration issues.

## Dependencies

- Ensures required dependencies (`jq`) are installed.

## Setup

- It is preferrable to add it to usr/bin or usr/local/bin.
- Name the file with `git-` prefix e.g `git-create-jira-branch`, git identifies the custom commands if they have `git-` prefix.
- Make it excutable `chmod +x git-create-jira-branch`
- Then add it to the pathes if it is not already added. `export PATH="${PATH}:/your-directory"`

## Usage

```sh
git-create-jira-branch <TICKET_NUMBER>
```
**Example:**
```sh
git-create-jira-branch 123
```
This will create a branch like:  
`your_username/PRO-123/implement-login-feature`

## Configuration

Before using the script, you **must configure** these placeholders at the top of the file:

| Variable         | Description                                                                                                 | Example Value                                      |
|------------------|------------------------------------------------------------------------------------------------------------|----------------------------------------------------|
| `JIRA_EMAIL`     | Your Atlassian (Jira) email address.                                                                      | `"your.email@domain.com"`                          |
| `JIRA_API_TOKEN` | Your Jira API token. Create one at https://id.atlassian.com/manage-profile/security/api-tokens             | `"your_jira_api_token"`                            |
| `USERNAME`       | Your Git username or handle. This will be prefixed to the branch name.                                     | `"myname"`                                           |
| `BOARD_KEY`      | The key                            | `PRO`                                                                 |
| `BOARD_CLOUD_ID` | The cloud id of your Jira Board | You can get it from `https://<your-site-name>.atlassian.net/_edge/tenant_info"` |  
