```bash 
# 1. Создание изолированной директории в файловой системе HDFS для вашего проекта
hdfs dfs -mkdir -p /user/hadoop/analytics_project

# 2. Загрузка скачанного датасета с локальной машины в HDFS
hdfs dfs -put /path/to/{file_name}.csv /user/hadoop/analytics_project/data.csv

# 3. Проверка успешности загрузки (выводит размер файла и права доступа)
hdfs dfs -ls /user/hadoop/analytics_project/

#4 Команда для выгрузки результирующего CSV из HDFS на локальный диск
hdfs dfs -get /user/hadoop/analytics_project/output_filtered_data/part-*.csv ./spark_result.csv
```
```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col

# Инициализация сессии
spark = SparkSession.builder.appName("TaskAnalysis").getOrCreate()

# 1. ЗАГРУЗКА (Чтение данных из HDFS)
df = spark.read.csv("hdfs:///user/hadoop/analytics/dataset.csv", header=True, inferSchema=True)

# 2. ТРАНСФОРМАЦИЯ (Фильтрация данных по критерию, например, статус 'Active')
# На этом этапе Spark только строит план вычислений, но не считывает весь файл
filtered_df = df.filter(col("status") == "Active")

# 3. ДЕЙСТВИЕ (Подсчет количества строк для вывода результата)
# Здесь запускается реальный расчет на кластере
row_count = filtered_df.count()
print(f"Количество активных записей: {row_count}")

# 4. СОХРАНЕНИЕ РЕЗУЛЬТАТА (Действие записи обратно в HDFS)
filtered_df.write.mode("overwrite").csv("hdfs:///user/hadoop/analytics/output_result", header=True)
```
