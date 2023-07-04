# Sql DataBase (С#)
Небольшая справка по созданию и привязке базы данных к программе(в моём случае к Windows Forms)

## Предисловие
Для создания БД, нужно установить SQL Management Studio(у меня 2019 года)<br>
 
## Создание Базы данных
Всё чётко и подробно расписано тут - https://metanit.com/sharp/adonet/2.1.php


## Привязка Базы данных и использование её возможностей
В коде программы, для работоспособности команд, прописать:<br>
<br>
using System.Configuration;<br>
using System.Data.SqlClient;<br>

В коде, прописываем перед public Form1():<br>
public static string connectionString = ConfigurationManager.ConnectionStrings["DefaultConnection"].ConnectionString;<br>
public SqlConnection connection = new SqlConnection(connectionString);<br>

Эту часть прописываем после InitializeComponent(); (я так делал, у меня работает :D )<br>
string connectionString = @"Data Source=.\SQLEXPRESS;Initial Catalog=First-DataBase;Integrated Security=True"; где First-DataBase - название Базы данных<br>

### Подключение к Базе данных
connection.Open(); //Для первой проверки советую оборачивать в try<br>
![image](https://github.com/Ksasha05/Sql-DataBase-C-/assets/113344025/2cc952ac-50c8-4034-ac92-818b30d9f8c2)




