# Introduction_to_Airflow
This is a memo to document what I have learnt in Apache Airflow, capturing the learning objectives as well as my personal notes. The course is taught by Mike Metzger from DataCamp and includes 4 chapters:
1. Intro to Airflow
2. Implementing Airflow DAGs
3. Maintaining and monitoring Airflow workflows
4. Building production pipelines in Airflow


## Chapter 1. Intro to Airflow

### Running a task in Airflow
You've just started looking at using Airflow within your company and would like to try to run a task within the Airflow platform. You remember that you can use the airflow run command to execute a specific task within a workflow. Note that an error while using airflow run will return airflow.exceptions.AirflowException: on the last line of output.

An Airflow DAG is set up for you with a dag_id of etl_pipeline. The task_id is download_file and the start_date is 2020-01-08. All other components needed are defined for you.

Which command would you enter in the console to run the desired task? Possible Answers

airflow run dag task 2020-01-08

airflow run etl_pipeline task 2020-01-08

airflow run etl_pipeline download_file 2020-01-08 (Answer)


### Examining Airflow commands
While researching how to use Airflow, you start to wonder about the airflow command in general. You realize that by simply running airflow you can get further information about various sub-commands that are available.

Which of the following is NOT an Airflow sub-command? Possible Answers

list_dags

edit_dag (Answer)

test

scheduler


### Defining a simple DAG
You've spent some time reviewing the Airflow components and are interested in testing out your own workflows. To start you decide to define the default arguments and create a DAG object for your workflow.

#### Import the DAG object
from airflow.models import DAG

#### Define the default_args dictionary
default_args = {
  'owner': 'jamessmith',
  'start_date': datetime(2020, 1, 14),
  'retries': 2
}

#### Instantiate the DAG object
dag_variable = DAG('dag_name', default_args=default_args)


### Working with DAGs and the Airflow shell
While working with Airflow, sometimes it can be tricky to remember what DAGs are defined and what they do. You want to gain some further knowledge of the Airflow shell command so you'd like to see what options are available.

Multiple DAGs are already defined for you. How many DAGs are present in the Airflow system from the command-line?

> airflow list_dags

>> INFO - Using executor SequentialExecutor

>> INFO - Filling up the DagBag from /home/repl/workspace/dags

>> DAGS

>> example_dag

>> update_state

Answer: 2


### Troubleshooting DAG creation
Now that you've successfully worked with a couple workflows, you notice that sometimes there are issues making a workflow appear within Airflow. You'd like to be able to better troubleshoot the behavior of Airflow when there may be something wrong with the code.

Two DAGs are defined for you and Airflow is setup. Note that any changes you make within the editor are automatically saved.

from airflow.models import DAG

default_args = {
  'owner': 'jdoe',
  'start_date': '2019-01-01'
}

dag = DAG( dag_id="etl_update", default_args=default_args )

from airflow.models import DAG

default_args = {
  'owner': 'jdoe',
  'email': 'jdoe@datacamp.com',
  'start_date': '2019-01-01'
}

dag = DAG( dag_id='refresh_data', default_args=default_args )


### Airflow web interface

### Starting the Airflow webserver
You've successfully created some DAGs within Airflow using the command-line tools, but notice that it can be a bit tricky to handle scheduling / troubleshooting / etc. After reading the documentation further, you realize that you'd like to access the Airflow web interface. For security reasons, you'd like to start the webserver on port 9090.

Which airflow command would you use to start the webserver on port 9090?

Remember to use the airflow -h command if needed. airflow subcommand -h will provide further detail.

> airflow webserver -p 9090


### Navigating the Airflow UI
To gain some familiarity with the Airflow UI, you decide to explore the various pages. You'd like to know what has happened on your Airflow instance thus far.

Which of the following events have not run on your Airflow instance? Possible Answers

cli_scheduler

cli_webserver

cli_worker (Answer)


### Examining DAGs with the Airflow UI
You've become familiar with the basics of an Airflow DAG and the basics of interacting with Airflow on the command-line. Your boss would like you to show others on your team how to examine any available DAGs. In this instance, she would like to know which operator is NOT in use with the DAG called update_state, as your team is trying to verify the components used in production workflows.

Remember that the Airflow UI allows various methods to view the state of DAGs. The Tree View lists the tasks and any ordering between them in a tree structure, with the ability to compress / expand the nodes. The Graph View shows any tasks and their dependencies in a graph structure, along with the ability to access further details about task runs. The Code view provides full access to the Python code that makes up the DAG.

Remember to select the operator NOT used in this DAG. Possible Answers

BashOperator

PythonOperator

JdbcOperator (Answer)

SimpleHttpOperator


## Chapter 2. Implementing Airflow DAGs







--
