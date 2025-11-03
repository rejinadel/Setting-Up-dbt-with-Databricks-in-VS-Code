# Setting-Up-dbt-with-Databricks-in-VS-Code
Data Build Tool for Data Engineers


Setting Up dbt with Databricks in VS Code

This guide explains how to set up dbt (data build tool) with Databricks on Windows using Python virtual environments and VS Code. This is ideal for learners who want to practice dbt models and SQL transformations in a cloud environment.

1. Prerequisites

Before starting, ensure you have:

Python 3.8 or 3.12 installed.

VS Code installed.

Databricks workspace with a SQL endpoint.

Optional: Git for version control.

2. Create and Activate a Virtual Environment

Open PowerShell or VS Code terminal.

Navigate to your workspace folder:

cd C:\Users\prashant\Desktop\dbt_learn1


Create a virtual environment:

python -m venv .venv


Activate the environment:

& .\.venv\Scripts\Activate.ps1


Upgrade pip inside the environment:

python -m pip install --upgrade pip

3. Install dbt-core and Databricks Adapter

Install dbt core and the Databricks adapter:

pip install dbt-core dbt-databricks


Verify installation:

dbt --version


Expected output:

Core: dbt-core 1.10.x
Plugins: databricks 1.10.x

4. Initialize a dbt Project

Navigate to your workspace folder:

cd C:\Users\prashant\Desktop\dbt_learn1


Initialize the project:

dbt init dbt_learnings


Project name: dbt_learnings

Database adapter: Databricks

Answer prompts for catalog, schema, threads, and Unity Catalog.

Folder structure will look like:

dbt_learnings/
├─ models/
├─ snapshots/
├─ seeds/
├─ macros/
├─ dbt_project.yml
└─ .gitignore

5. Configure Profiles

Open profiles.yml (usually in C:\Users\prashant\.dbt\profiles.yml):

dbt_learnings:
  target: dev
  outputs:
    dev:
      type: databricks
      catalog: dbt_learnings
      schema: default
      host: <your-databricks-host>
      http_path: <your-databricks-sql-endpoint>
      token: <your-databricks-personal-access-token>
      threads: 1


Test the connection:

dbt debug


Expected outcome:

profiles.yml file [OK found and valid]
dbt_project.yml file [OK found and valid]
Connection: Registered adapter: databricks

6. Open VS Code Correctly

Open the folder containing dbt_project.yml, e.g.:

C:\Users\prashant\Desktop\dbt_learn1\dbt_learnings


Select Python interpreter (.venv):

Ctrl+Shift+P → Python: Select Interpreter → Choose .venv


Install dbt Power User extension for VS Code.

7. Configure dbt Power User

Open Command Palette (Ctrl+Shift+P):

dbt: Select Project


Choose your project: dbt_learnings.

Status bar should show your active dbt project.

You can now use:

Build models: dbt: Build Project

Preview query results: dbt: Preview Results

Compile models: dbt: Compile Project

Seed tables: dbt: Seed Project

8. Working with dbt Models

Place SQL files in the models/ folder.

Run models:

dbt run


Test models:

dbt test


Compile models without executing:

dbt compile


Generate documentation:

dbt docs generate
dbt docs serve

9. Optional: Git Integration

Initialize git:

git init
git add .
git commit -m "initial commit"


Rename branch:

git branch -M main

10. Tips & Common Pitfalls

Always activate the virtual environment before running dbt commands.

profiles.yml must match the project name in dbt_project.yml.

Open VS Code in the folder where dbt_project.yml exists.

If Power User errors occur, check Python interpreter and active dbt project.

This setup is now ready for building dbt models on Databricks, running SQL queries, and managing transformations end-to-end.
