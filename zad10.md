## Подключение и создание dataset 
>при связки dataset-ов - не использовать inner join. Только Left или Righ (взависимости от расположения)
<img width="1611" height="470" alt="image" src="https://github.com/user-attachments/assets/2700ed45-199b-49e4-92c0-05d9218e8a19" />
<img width="671" height="334" alt="image" src="https://github.com/user-attachments/assets/a7263ac0-2edc-4613-8816-1483bab9ff96" />
<img width="668" height="333" alt="image" src="https://github.com/user-attachments/assets/a1698f82-cc88-426c-9193-deccd01b36ac" />


## Создание чартов

<img width="1597" height="944" alt="image" src="https://github.com/user-attachments/assets/4f03abd6-e24f-4599-84c3-5a8f8f82acee" />
<img width="1599" height="941" alt="image" src="https://github.com/user-attachments/assets/cb53ed3a-de66-4487-a7a0-7a2710068f17" />

> datetrunc([order_purchase_timestamp], "month") - Формула для оси X

<img width="1602" height="957" alt="image" src="https://github.com/user-attachments/assets/99fe69f5-ca5a-42fb-aa78-2923679e41d8" />

>Формула для создания "Дней на сборку" `floor([order_delivered_carrier_date] - [order_purchase_timestamp])`
 
<img width="1597" height="955" alt="image" src="https://github.com/user-attachments/assets/fe4c47fe-4a51-4897-98ee-ed29eb6832a1" />
