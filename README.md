# Setting-Up-dbt-with-Databricks-in-VS-Code
Data Build Tool(dbt) for Data Engineers

Getting Started with dbt and Databricks in VS Code

This article provides a step-by-step guide to setting up dbt (data build tool) with Databricks on Windows using Python virtual environments and VS Code. By the end of this guide, you will have a working environment ready to run dbt models, SQL transformations, and explore data in Databricks.


** Prerequisites**

Before starting, ensure you have:

Python 3.8 or 3.12 installed

VS Code installed

A Databricks workspace with a SQL endpoint

Git (optional, for version control)

** Create and Activate a Virtual Environment**

Open PowerShell or the VS Code terminal.

**Navigate to your workspace folder:**

cd C:\Workspace\dbt_project

**Create a virtual environment:**

python -m venv .venv

**Activate the environment:**
& .\.venv\Scripts\Activate.ps1

**Upgrade pip:**
python -m pip install --upgrade pip

**Install dbt-core and Databricks Adapter**


pip install dbt-core dbt-databricks


**Verify installation:**

dbt --version


You should see output similar to:

Core: dbt-core 1.x.x
Plugins: databricks 1.x.x

** Initialize a dbt Project**

**Navigate to your workspace folder:**

cd C:\Workspace\dbt_project


**Initialize a new dbt project:**

dbt init my_dbt_project


**Enter project name: my_dbt_project**

Database adapter: Databricks

Provide required details like catalog, schema, threads, and Unity Catalog option.

**Folder structure created:**

my_dbt_project/
├─ models/
├─ snapshots/
├─ seeds/
├─ macros/
├─ dbt_project.yml
└─ .gitignore

 **Configure dbt Profiles**

Edit profiles.yml (usually located at C:\Users\<User>\.dbt\profiles.yml) and add:

my_dbt_project:
  target: dev
  outputs:
    dev:
      type: databricks
      catalog: my_catalog
      schema: default
      host: <databricks-host>
      http_path: <databricks-sql-endpoint>
      token: <databricks-access-token>
      threads: 1


**Test the connection:**

dbt debug


**Expected outcome:**

profiles.yml file [OK found and valid]
dbt_project.yml file [OK found and valid]
Connection: Registered adapter: databricks

** Open the Project in VS Code**

Open the folder containing dbt_project.yml.

**Select Python interpreter:**

Ctrl+Shift+P → Python: Select Interpreter → Choose .venv


**Install the dbt Power User extension from the VS Code Marketplace.**

** Configure dbt Power User**

Open Command Palette (Ctrl+Shift+P):

dbt: Select Project


**Choose your project: my_dbt_project.**

Status bar should show your active dbt project.

You can now use:

Build models: dbt: Build Project

Preview query results: dbt: Preview Results

Compile models: dbt: Compile Project

Seed tables: dbt: Seed Project

** Working with dbt Models**

Place SQL files in the models/ folder.

**Run models:**

dbt run


**Test models:**

dbt test


**Compile models without executing:**

dbt compile


**Generate documentation:**

dbt docs generate
dbt docs serve

 **Optional: Git Integration**

Initialize git in the project folder:

git init
git add .
git commit -m "initial commit"


**Rename the default branch:**

git branch -M main

** Tips & Common Pitfalls**

Always activate your virtual environment before running dbt commands.

Ensure profiles.yml matches the project name in dbt_project.yml.

Open VS Code in the folder where dbt_project.yml exists.

If Power User errors occur, check Python interpreter and active dbt project.

With this setup, you can now start building dbt models on Databricks, execute SQL queries, and manage transformations efficiently.

