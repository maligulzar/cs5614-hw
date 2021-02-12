# Apache Spark Standalone Cluster on Docker

This standalone Spark cluster is adapted from **cluster-apps-on-docker/spark-standalone-cluster-on-docker**. Please follow the following steps for a smooth deployment of the cluster in your local machine.


## Introduction

This project gives you an **Apache Spark** cluster in standalone mode with a **JupyterLab** interface built on top of **Docker**.
Learn Apache Spark through its **Scala**, **Python** (PySpark) and **R** (SparkR) API by running the Jupyter [notebooks](build/workspace/) with examples on how to read, process and write data.

<p align="center"><img src="docs/image/cluster-architecture.png"></p>

![build-master](https://github.com/cluster-apps-on-docker/spark-standalone-cluster-on-docker/workflows/build-master/badge.svg)
![sponsor](https://img.shields.io/badge/patreon-sponsor-ff69b4)
![jupyterlab-latest-version](https://img.shields.io/docker/v/andreper/jupyterlab/3.0.0-spark-3.0.0?color=yellow&label=jupyterlab-latest)
![spark-latest-version](https://img.shields.io/docker/v/andreper/spark-master/3.0.0?color=yellow&label=spark-latest)
![spark-scala-api](https://img.shields.io/badge/spark%20api-scala-red)
![spark-pyspark-api](https://img.shields.io/badge/spark%20api-pyspark-red)
![spark-sparkr-api](https://img.shields.io/badge/spark%20api-sparkr-red)

## TL;DR

```bash
curl -LO https://raw.githubusercontent.com/cluster-apps-on-docker/spark-standalone-cluster-on-docker/master/docker-compose.yml
docker-compose up
```

## Contents

- [Quick Start](#quick-start)
- [Tech Stack](#tech-stack)
- [Metrics](#metrics)
- [Contributing](#contributing)
- [Contributors](#contributors)
- [Support](#support)

## <a name="quick-start"></a>Quick Start


### Prerequisites

 - Install [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/), check **infra** [supported versions](#tech-stack)
 - Make sure that you provide ample resources to Docker. Otherwise, the JupyterLab Notebook won't be able to connect to the Spark Master. 
 
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

5. Stop the cluster by typing `ctrl+c` on the terminal;
6. Run step 2 to restart the cluster.
