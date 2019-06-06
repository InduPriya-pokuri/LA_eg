# Project - 1: ======>LogsAnalysis 
## Developed by =====>Pokuri InduPriya

LogsAnalysis,part of the udacity [fullstack web developer nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004)

## Login Analysis Project Overview

This is single file project this generates the reports from the news article database.This reporting tool is a python program using the ``psycopg2`` module to connect to the ``PostgreSQL`` database.

## Requirements to run the Login Analysis Project

======>Python         (Programming Language)
======>vagrant        (A virtual Environment)
======>virtual Box    (An Open Source Virtualization Product)
======>Git Bash / power shell (for windows)
======>psycopg2       (library)
======>postgreSQL     (database)


## In this Project the following files / Contents

=====> app_log.py --> is the main file to run this logAnalysis Project executes the SQLQuaries.

=====> README.md --> Step By Step Procedure to run this LogAnalysis project.

=====> newsdata.zip --> The Newsdata ZipFile contains populate news.

=====> Result.txt --> Executed expected output my Project


## Project Setup step by step procedure

1) Install Vagrant ===> [https://www.vagrantup.com/]

2) Install 

****************************************************************
VirtualBox[https://www.virtualbox.org/wiki/Download_Old_Builds_5_1] to install and run your projects on virtual machine.
***************************************************************

3) Vagrant Setup file to this Download or Clone fullstack-nanodegree -vm
****************************************************************
*   [https://github.com/udacity/fullstack-nanodegree-vm]       *
****************************************************************
repository.

4) Launch the vagrant VM inside vagrant sub-directory in the downloaded fullstack-nanodegree-vm repository using commands:

Step I ----> "$vagrant up"

Step II ---->  "$vagrant ssh"

Step III ----> Change Directory to vagrant =>  "$cd /vagrant/"

Step IV ----> Change Directory to project folder => $cd mylogsanlysis

Step V ----> Download the [newsdata]
****************************************************************

(https://d17h27t6h515a5.cloudfront.net/topher/2016/August/57b5f748_newsdata/newsdata.zip). Unzip the file in order to extract newsdata.sql. This file should be inside the `vagrant/mylogsanlysis/`.
****************************************************************

Step VI ----> Load news data in database ----> ``$psql -d news -f newsdata.sql ``

Step VII ----> Connect news data to database ---->  ``$psql -d news``

Step VIII----> Create helping view for third problem create view using 

'''select * from (select x.days_count ,
round(cast((100*y.hits) as numeric) / cast(x.hits as numeric) , 2)
as error_per from (select date(time) as days_count , count(*) as hits
from log group by days_count) as x inner
join (select date(time) as days_count, count(*) as hits from log
where status like '%404%' group by days_count) as y
on x.days_count = y.days_count) as t where error_per > 1.0;'''

Step IX ----> Type `\q` command for exit from PostgreSQL.

Step X ----> Run Python file ----> ``$python3 app_log.py``

## We have to follow different types of another  Helpful Resources

1. [PEP 8 -- Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/)
2.[PostgreSQL 9.5 Documentation](https://www.postgresql.org/docs/9.5/static/index.html)
3. [Vagrant](https://www.vagrantup.com/downloads)
4. [VirtualBox](https://www.virtualbox.org/wiki/Downloads)