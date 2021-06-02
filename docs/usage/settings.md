<div class="axi-header">
  <h1>Settings</h1>
</div>

## Authentication

The authentication protocol uses the authorization token which allows third party services obtain limited access to your Axiom instances. It lets you configure a OAuth2 authentication when your provide your `Client ID` and `Client Secret` from your provider for multiple use case support. 

**To add OAuth2 Provider** visit **Settings > Authentication**

<img class="axi-window-shadow" src="/assets/shots/authentication.png" alt="Auth overview" /> 


## Token

**Obtain a token in the Axiom UI**

You can generate an ingest and personal token manually in your Axiom user settings. 

The ingest token is to used to send data to one or more datasets. Ingest tokens do not allow control of your organization, they are only used to ingest events, while the Personal token is used to access the Axiom API programmatically for custom integrations or for tools such as the Axiom CLI.

---

**To generate an ingest Token**

1. under **settings**, select **ingest token**. 
2. Select **Add ingest token**.
3. Enter a **name** and **description** and select **ADD**. 
4. Copy the generated token to your clipboard. Once you navigate from the page, token can be seen again by selecting **Ingest Tokens**. 

<img class="axi-window-shadow" src="/assets/shots/ingest-token.png" alt="Ingest Token overview" /> 




---


**To generate a Personal Token**

1. Under **settings**, select **profile**
2. Select **Add personal token**
3. Enter a **name** and **description** and select **ADD**.
4. Copy the generated token to your clipboard. Once you navigate from the page, token can be seen again by selecting **Personal token**


<img class="axi-window-shadow" src="/assets/shots/personal-token.png" alt="Personal Token overview" /> 

## API

The best way to get started with our API is to use [Go-Axiom](https://github.com/axiomhq/cli) to send events directly to Axiom. 

## Dataset 

Manage datasets for your organization, including creating new datasets or deleting existing datasets.

**Datasets are a collection of similar events** When data is sent to Axiom it is stored in a dataset. 

Dataset names must be between 1-128 characters, and may only contain ASCII alphanumeric characters and the '-' character.

To create a dataset, enter the **name** and **description** of your dataset. 

<img class="axi-window-shadow" src="/assets/shots/dataset.png" alt="Auth overview" /> 

## Status

You can see the license and instance configuration for your organization by selecting **Status** this lets you know:

- How much data you can ingest. 
- How long can you use your Instance.
- Maximum Datasets you can have.
- Maximum number of Users.
- Maximum number of Teams. 
- Maximum Query Window.

<img class="axi-window-shadow" src="/assets/shots/status.png" alt="Auth overview" /> 


## Manage Teams

You can view, create, and manage teams.  Team members added can also manage access to datasets. 

If you’re a team Owner, you can add new team members to the team by selecting the **Add button** at the upper right corner omn the Axiom UI.   

- Enter the name of the user you want to add as a member. 

- Search for the team member you want to add to your Team.

**Only users with the roles User or Read Only can be added as team members. Once a user is added to one or more teams, they can only see the datasets that are visible to those teams.**

<img class="axi-window-shadow" src="/assets/shots/teams.png" alt="Auth overview" /> 


## User Settings

After signing up, you can control the access to your Axiom deployments by managing the user's list.  **Settings > Users.** 

Team owners can add a user's name, email, and also assign a specific role. 

**Settings > Users > Add user > Assign roles**. 

<img class="axi-window-shadow" src="/assets/shots/user.png" alt="Auth overview" /> 