---
title: " "
date: 2018-01-28
tags: [ETL Pipline, Stream Processing, Data Mining, Web Scraping]
header:
  image: "/images/perceptron/project2.jpg"
excerpt: "Data Manipulation, Web Scraping, Stream Processing, Data Mining"
mathjax: "true"
---

## Stream Processing

The aim of this project is to enrich a Kinesis data stream with external dataset.

In this project seeks to:

- Create a shard kinesis stream

- Create a producer and consumer to push results from web scraping into created kinesis and to collect the data from kinesis respectively

- Enrich data consumed and append to CSV

### Configuration

- AWS
- Boto3
- Pandas
- Requests
- Beautifulsoup
- lxml

```python
    import boto3
    import csv
    import json
    import time
    from datetime import datetime
    from looper_scraper import scrape_looper
    import datetime as dt
    import pandas as pd

    region = 'regionname'

    streamName = 'blossom-data-eng-username'

    kinesis = boto3.client('kinesis', region_name=region)

    kinesis.list_streams()

    response = kinesis.create_stream(StreamName=streamName, ShardCount=1)
    kinesis.list_streams()
```

[View source](https://github.com/EnaSmoak/stream-processing)

## Web Scraping

In this project, a website was scraped for information and outputted to csv.

### Configuration

- Pandas
- Numpy
- Requests
- Beautifulsoup
- lxml

```python
    import re
    import datetime
    import requests
    import numpy as np
    import pandas as pd
    from bs4 import BeautifulSoup
```

[View source](https://github.com/EnaSmoak/web-scraping)

## End-To-End ETL Pipline

The purpose of this project is to implement an Extract, Transform and Load (ETL) pipline. This was achieved by using spark to:

- extract data from data source
- transform data
- load data
- manipulate data with sql

### Configuration

- Pandas
- Pyspark
- Postgresql

```python
    from string import punctuation, digits
    from pyspark.sql.types import BooleanType
    from pyspark.sql.functions import udf
    from pyspark.sql import functions as F
    from pyspark.sql import SparkSession, DataFrame
    from pyspark.ml import Pipeline
    import pandas as pd

    spark = (
      SparkSession.builder
          .appName("Name of Application")
          .config("spark.jars",
      "/driverpath/jars/postgresql-42.2.8.jar")
          .getOrCreate()
    )
```

[View source](https://github.com/EnaSmoak/end-to-end-ETL-pipeline)

## Batch Processing

the aim of this project is to process batch for data mining by:

- connect to amazon s3 bucket using boto3
- download and extract compressed datasets
- join dataframes
- implement ngram on text in columns
- determine frequency of columns in dataframe
- visualize data

### Configuration

- Pandas
- Pyspark
- Boto3
- zipfile (for extracting compressed file)
- mathplotlib (for visualization)

```python
    import pyspark
    import boto3
    from zipfile import ZipFile
    from string import punctuation, digits
    from pyspark.sql.types import BooleanType
    from pyspark.sql.functions import udf
    from pyspark.sql import functions as F
    from pyspark.sql import SparkSession, DataFrame
    from pyspark.ml import Pipeline
    from pyspark.ml.feature import  NGram, Tokenizer,CountVectorizer, StopWordsRemover
    import pandas as pd
    import matplotlib.pyplot as plt

    #download dataset from s3 bucket
    s3_client.download_file(bucket, "fileName", 'pathToSaveFile')

    spark = SparkSession.builder.getOrCreate()
```

[View source](https://github.com/EnaSmoak/batch_processing)

## Read and convert data file format

A python script that uses **pandas** to read data from csv files, filter columns and convert to other file formats.

### Configuration

- Pandas
- Fastparquet
- Pandavro
- Boto3

```python
    import boto3
    import numpy as np
    import pandas as pd
    import fastparquet
    import pandavro as pdx
```

[View source](https://github.com/EnaSmoak/read-and-convert-with-pandas)
