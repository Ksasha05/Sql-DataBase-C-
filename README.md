# Sql DataBase (С#)
Небольшая справка по созданию и привязке базы данных к программе(в моём случае к Windows Forms)

## Предисловие
Для создания БД, нужно установить SQL Management Studio(у меня 2019 года)<br>
В коде программы, для работоспособности команд, прописать:<br>
<br>
using System.Configuration;<br>
using System.Data.SqlClient;<br>
 
## Создание Базы данных
Всё чётко и подробно расписано тут - https://metanit.com/sharp/adonet/2.1.php


## Привязка Базы данных и использование её возможностей
Прописываем:<br>
public static string connectionString = ConfigurationManager.ConnectionStrings["DefaultConnection"].ConnectionString;<br>
public SqlConnection connection = new SqlConnection(connectionString);<br>


