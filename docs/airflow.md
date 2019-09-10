# Airflow

## Install
```
pip install apache-airflow
```

## Admin

### Start
```
airflow webserver
airflow scheduler
```

### Add new dag
1. Create a DAG definition script under "{AIRFLOW_HOME}/dags/"
    1. Import Airflow: `import airflow`
    * Set default_args
    * Init DAG
    * Create Task include or inherit the arguments task_id and owner
    * (Optionally) use Jinja template create a flexible command in task
    * Setting up Dependencies between tasks, reuslt in a DAG
* (Optionally) Testing
    2. Test static syntax: `python {dag script filepath}`
    * Metadata Validation：`airflow list_dags` and `airflow list_tasks {task name}`
    * Test special task: `airflow test {dag name} {task name} {date, like 2015-06-01}`
* (Optionally) Backfill：`airflow backfill {dag name} -s {startDate, like 2015-06-01} -e {endDate, like 2015-06-07}`
* (Optionally)Init Database: `airflow initdb`
## Debug
### No module named 'werkzeug.wrappers.json'
```
pip install -U Flask==1.0.4
```

## Referral
[Airflow Official Site](https://airflow.apache.org/)