Meltano Demo
====

## Overview

[Meltano](https://meltano.com/) is an open source self-managed data integration platform. This repo uses Meltano to load data from a local CSV file into a PostgreSQL database. This repo was created by following [this tutorial](https://docs.meltano.com/getting-started/) and using a different extractor.

## Repo Plugins
- Extractor: [CSV](https://hub.meltano.com/extractors/tap-csv)
- Loader: [PostgreSQL](https://hub.meltano.com/loaders/target-postgres)

## Prerequisites
- Python3
- PostgreSQL
- [Install Meltano](https://docs.meltano.com/getting-started/installation)

## Setup

Create a python [virtual environment](https://docs.python.org/3/library/venv.html) for installing packages and activate it
```bash
python -m venv </path/to/new/virtual/environment>

source env/bin/activate
```

Run the pipeline
```bash
meltano run tap-csv target-postgres
```

Check the database for your data
```bash
psql -d demo -U meltano
```

Meltano will create schema with the name of the data source and a table with the entity name
```sql
select count(*) from tap_csv.buildings;
```
