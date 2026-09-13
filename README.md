# Practice_DBT

This repository contains a [dbt](https://www.getdbt.com/) (Data Build Tool) project for data transformations and modeling.

## Project Structure

```
.
├── analyses/              # Ad-hoc SQL queries and analyses
├── macros/                # Reusable Jinja/SQL macros
├── models/                # Data models and transformations
│   └── example/           # Starter example models & schema tests
├── seeds/                 # Static CSV files loaded into database
├── snapshots/             # Slowly Changing Dimensions (Type 2) definitions
├── tests/                 # Custom singular data tests
├── dbt_project.yml        # Main dbt project configuration
├── profiles.yml.example   # Example database connection configuration
├── requirements.txt       # Python dependencies (dbt-core, dbt-databricks)
└── README.md
```

## Setup & Getting Started

### 1. Set Up Python Virtual Environment

```bash
# Create virtual environment
python3 -m venv .venv

# Activate virtual environment
source .venv/bin/activate

# Upgrade pip and install dependencies
pip install --upgrade pip
pip install -r requirements.txt
```

### 2. Configure Credentials (`profiles.yml`)

Copy the example profile to your local `~/.dbt/profiles.yml`:

```bash
mkdir -p ~/.dbt
cp profiles.yml.example ~/.dbt/profiles.yml
```

Then edit `~/.dbt/profiles.yml` with your Databricks workspace credentials:
- **Host**: `dbc-a3e4d3c2-a6be.cloud.databricks.com`
- **HTTP Path**: From your Databricks SQL Warehouse or Cluster (`Connection Details` tab -> `HTTP Path`)
- **Token**: Personal Access Token (from `User Settings` -> `Developer` -> `Access tokens`) or set `auth_type: oauth`
- **Catalog**: Your Unity Catalog name (e.g. `main`)
- **Schema**: Your target schema (e.g. `default` or personal dev schema)

### 3. Verify Connection

```bash
dbt debug
```

### 4. Common dbt Commands

```bash
# Parse and validate project syntax
dbt parse

# Compile SQL models without executing
dbt compile

# Run all models
dbt run

# Run a specific model
dbt run --select my_first_dbt_model

# Run tests
dbt test

# Generate and view documentation
dbt docs generate
dbt docs serve
```


Hi samra