# Learning in Public

This repository serves as a record of my learning journey, where I track and outline the resources I've used. My focus is on Machine Learning (including MLOps and ML Engineering), Data Science, Data Engineering, and Programming. 
I try to learn by implementing in code.  

| | Resources | Status of Completion |
| - | - | - |
| 1 | [**DataTalksClub Data Engineering Zoomcamp**](https://github.com/DataTalksClub/data-engineering-zoomcamp) |  |
| 2 | [**DataTalksClub Machine Learning Zoomcamp**](https://github.com/DataTalksClub/machine-learning-zoomcamp) |  |  

| | Projects and Notebooks |
| - | - |
| 1 | [**My notes for Data Engineering Zoomcamp**](https://github.com/kemaldahha/data-engineering-course/blob/main/week_1_notes.md) |

## Day 0

Over the past month I have been going through the Data Engineering Zoomcamp by DataTalksClub. Here is a summary of what I covered so far.
- **Docker** is a platform that uses containers to create, deploy, and run applications. It's self-contained, so whatever you 'Dockerize' on a particular system (e.g. Windows), will run on any other machine (e.g. Linux) with Docker. Docker images are files which contain everything to run a piece of software (e.g. Postgres). You can download them from Docker Hub or make them yourself. The creation of Docker images can be automated using a Dockerfile. You can provide it arguments and instructions (e.g. to upload a file from your current working directory to a certain location in the image before running the software). When you run a Docker image, a container (instance of an image) is created. You can run multiple containers that communicate with each other. Containers are _ephemeral_, meaning that their state is not saved unless _volumes_ are used for persistence. Networks can be used to allow multiple containers to communicate with each other.
- I used a **Postgres** database. To inspect the data in postgres, I used both pgcli (command-line interface) as well as pgAdmin (browser interface).
- I did a refresher on **SQL**. It's been a while since I did SQL, because these days I use Pandas. But I will put some SQL practice on my roadmap down the line.
- **Terraform** was completely new to me. It's an Infrastructure-as-Code application which allows for convenient setup of Cloud resources. It's an easy to use abstraction layer on top of Cloud platforms such as GCP, Azure, AWS, and many others. Terraform commands are pretty straightforward: init, plan, apply, destroy. You can use variables in your Terraform .tf files.
- During this month, I used **Linux** extensively and learned about **SSH** and **port forwarding**.  

![Image](./images/day0a.png)
![Image](./images/day0b.png)

Resources:
- [My week 1 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_1_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 1

**Workflow orchestration** tools such as Apache Airflow enable Data Engineers to organize and manage data pipelines/workflows. For example, consider a pipeline that involves downloading CSV data from the internet, reading the data, and storing it in a database. Executing these steps sequentially using a simple bash script, can be error-prone - if one step fails, the entire pipeline fails. Although you could circumvent this by writing code to retry upon failure, this approach becomes unwieldy as workflows grow in complexity. Workflow Orchestration address these challenges by simplifying retries, enabling parametrization of steps in the workflow, handling parallel execution, and providing tools to inspect logs and track execution history.

Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)

## Day 2

Today I set up **Airflow** using Docker. I took a docker-compose.yaml file from the [Apache Airflow documentation](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html) and made adjustments to it to make it work with GCP. Running into an issue which I'll troubleshoot tomorrow. 
![Error with airflow](./images/day2.png)


Resources:
- [My week 2 notes](https://github.com/kemaldahha/data-engineering-course/blob/main/week_2_notes.md) for [DataTalksClub Data Engineering Zoomcamp](https://github.com/DataTalksClub/data-engineering-zoomcamp)
