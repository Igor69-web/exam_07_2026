# Запуск окружения

> Запуск хранилища
```bash
start-dfs.sh
````
> Запуск менеджера ресурсов
```bash
start-yarn.sh
````
> Проверка запущенных Java-процессов
```bash
jps
```
<img width="256" height="188" alt="image" src="https://github.com/user-attachments/assets/bf17484e-3d33-4000-9ace-12a59cb6e12f" />

```bash
# 1. Создаем папку в HDFS
hdfs dfs -mkdir -p /user/hadoop/ex_data

# 2. Копируем CSV-файл в HDFS
hdfs dfs -put /home/Download/файл.csv /user/hadoop/ex_data/data.csv

# 3. Проверяем, что файл появился
hdfs dfs -ls /user/hadoop/ex_data
```

> Запуск pyspark
```bash
pyspark
```
### Файл analyze.py
```py
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, count

spark = SparkSession.builder.appName("CSV_Analysis").getOrCreate()

df = spark.read.csv("hdfs://localhost:9000/user/hadoop/ex_data/data.csv", header=True, inferSchema=True)

filtered_df = df.filter(col("building_class_category").isNotNull())

result_df = filtered_df.groupBy("tax_class").agg(count("*").alias("count"))


print("Количество строк:", df.count())
result_df.show() 

result_df.coalesce(1).write.mode("overwrite").csv("hdfs://localhost:9000/user/hadoop/ex_data/results", header=True)

spark.stop()
```

> Запуск файл analyze.py
```bash
spark-submit analyze.py
```
> Проверка, что файл появился
```bash
hdfs dfs -ls /user/hadoop/ex_data/results
```

> Сохранить файл в папку home
```bash
hdfs dfs -get /user/hadoop/ex_data/results/part-*.csv ./final_analysis.csv
```
