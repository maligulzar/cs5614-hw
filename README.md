# Apache Spark Standalone Cluster on Docker

This standalone Spark cluster is adapted from **cluster-apps-on-docker/spark-standalone-cluster-on-docker**. Please follow these steps for a quick deployment of the cluster in your local machine.


## Introduction

This project gives you an **Apache Spark** cluster in a standalone mode with a **JupyterLab** interface built on top of **Docker**.
You can work with Apache Spark through its **Scala** or **Python** (PySpark) API by running the Jupyter [notebooks](build/workspace/) with examples on how to read, process and write data.

## TL;DR

```bash
curl -LO https://raw.githubusercontent.com/cluster-apps-on-docker/spark-standalone-cluster-on-docker/master/docker-compose.yml
docker-compose up
```

### Prerequisites

Install [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/). Make sure that you provide ample resources to Docker. Otherwise, the JupyterLab Notebook won't be able to connect to the Spark Master. 
 
<p align="center"><img src="docs/image/docker-resource.png"></p>

### Download from Docker Hub (easier)

1. Download the [docker compose](docker-compose.yml) file;

```bash
curl -LO https://raw.githubusercontent.com/cluster-apps-on-docker/spark-standalone-cluster-on-docker/master/docker-compose.yml
```

2. Start the cluster;

```bash
docker-compose up
```

4. Visit [localhost:8888](http://localhost:8888/) and Run Apache Spark code using the provided Jupyter [notebooks](build/workspace/) with Scala, PySpark and SparkR examples;
  - You can also monitor the cluster's health at  Spark Master [localhost:8080](http://localhost:8080/)
  - To inspect the status and runtime metric of a Spark job, view the application UI at  [localhost:4040](http://localhost:4040/).

### Cluster overview

| Application     | URL                                      | Description                                                |
| --------------- | ---------------------------------------- | ---------------------------------------------------------- |
| JupyterLab      | [localhost:8888](http://localhost:8888/) | Cluster interface with built-in Jupyter notebooks          |
| Spark Driver    | [localhost:4040](http://localhost:4040/) | Spark Driver web ui                                        |
| Spark Master    | [localhost:8080](http://localhost:8080/) | Spark Master node                                          |
| Spark Worker I  | [localhost:8081](http://localhost:8081/) | Spark Worker node with 1 core and 512m of memory (default) |
| Spark Worker II | [localhost:8082](http://localhost:8082/) | Spark Worker node with 1 core and 512m of memory (default) |

5. Stop the cluster by typing `ctrl+c` on the terminal or in a separate shell, type;
```bash 
docker-compose down
```
6. Run step 2 to restart the cluster.
