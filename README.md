# Introduction_to_Airflow
This is a memo to share what I have learnt in Apache Airflow, capturing the learning objectives as well as my personal notes. The course is taught by Mike Metzger from DataCamp and includes 4 chapters:
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

airflow run etl_pipeline download_file 2020-01-08 <answer>


### Examining Airflow commands
While researching how to use Airflow, you start to wonder about the airflow command in general. You realize that by simply running airflow you can get further information about various sub-commands that are available.

Which of the following is NOT an Airflow sub-command? Possible Answers

list_dags

edit_dag <answer>

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











--
