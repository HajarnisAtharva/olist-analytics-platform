# olist-analytics-platform
olist-analytics-platform/
├── README.md
├── LICENSE
├── .gitignore
├── .env.example
├── .pre-commit-config.yaml
├── pyproject.toml
├── Makefile
│
├── docs/
│   ├── 00-requirements.md          <- Chapter 0 output
│   ├── 01-setup.md
│   ├── ...
│   ├── 16-results.md               <- the measured scorecard
│   ├── adr/
│   │   ├── 0001-postgres-as-source.md
│   │   └── ...
│   └── images/
│
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── versions.tf
│   ├── databases.tf
│   ├── warehouses.tf
│   ├── roles.tf
│   ├── grants.tf
│   ├── governance.tf              <- masking, row policies (Ch 13)
│   ├── terraform.tfvars.example
│   └── environments/
│       ├── dev.tfvars
│       └── prod.tfvars
│
├── docker/
│   ├── docker-compose.yml
│   ├── .env.example
│   └── postgres/
│       ├── Dockerfile
│       ├── postgresql.conf         <- wal_level=logical for CDC
│       └── init/
│           ├── 01_schema.sql
│           ├── 02_load_csv.sql
│           ├── 03_constraints.sql
│           ├── 04_triggers.sql
│           └── 05_cdc_setup.sql
│
├── ingestion/
│   ├── framework/
│   │   ├── __init__.py
│   │   ├── config.py               <- pydantic settings
│   │   ├── logging_setup.py        <- structured JSON logging
│   │   ├── state.py                <- watermark store
│   │   ├── pipeline.py             <- the runner
│   │   ├── extractors/
│   │   │   ├── base.py
│   │   │   ├── postgres.py
│   │   │   ├── rest_api.py
│   │   │   └── file.py
│   │   └── loaders/
│   │       ├── base.py
│   │       └── snowflake.py
│   ├── pipelines/
│   │   ├── postgres_orders.yml
│   │   ├── postgres_customers.yml
│   │   └── fx_rates.yml
│   ├── generators/
│   │   ├── simulate_day.py
│   │   ├── defect_injector.py
│   │   └── clickstream.py
│   ├── tests/
│   └── run.py                      <- CLI entry point
│
├── dbt/olist_analytics/
│   ├── dbt_project.yml
│   ├── packages.yml
│   ├── profiles.yml.example
│   ├── models/
│   │   ├── bronze/
│   │   ├── silver/
│   │   │   ├── staging/
│   │   │   └── intermediate/
│   │   └── gold/
│   │       ├── dimensions/
│   │       ├── facts/
│   │       └── marts/
│   ├── snapshots/
│   ├── seeds/
│   ├── macros/
│   ├── tests/
│   └── analyses/
│
├── airflow/
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── packages.txt
│   ├── dags/
│   │   ├── dag_ingest_daily.py
│   │   ├── dag_transform_daily.py
│   │   └── dag_observability.py
│   └── include/
│
├── streamlit/
│   ├── executive_dashboard.py
│   └── environment.yml
│
├── .github/
│   └── workflows/
│       ├── pr.yml
│       ├── deploy.yml
│       └── nightly.yml
│
└── scripts/
    ├── download_data.py
    ├── bootstrap_snowflake.sql
    └── generate_keypair.ps1
