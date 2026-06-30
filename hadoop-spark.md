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
# 1. Создаем папку в HDFS (если она еще не создана)
hdfs dfs -mkdir -p /user/hadoop/ex_data

# 2. Копируем ваш CSV-файл с рабочего стола ВМ в HDFS
# (Замените путь к файлу на ваш реальный)
hdfs dfs -put /home/ubuntu/Desktop/ваш_файл.csv /user/hadoop/ex_data/data.csv

# 3. Проверяем, что файл появился
hdfs dfs -ls /user/hadoop/ex_data
```

> Запуск pyspark
```bash
pyspark
```

> Запуск файл analyze.py
```bash
spark-submit analyze.py
```
> Проверка, что файл появился
```bash
hdfs dfs -ls /user/hadoop/ex_data/results
```
