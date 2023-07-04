# Sql DataBase (С#)
Небольшая справка по созданию и привязке базы данных к программе(в моём случае к Windows Forms в Visual Studio)

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

В файле App.config необходимо прописать:<br>
  ```<connectionStrings>
   <add name="DefaultConnection" connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=usersdb;Integrated Security=True"
       providerName="System.Data.SqlClient"/>
  </connectionStrings>```


Эту часть прописываем после InitializeComponent(); (я так делал, у меня работает :D )<br>
string connectionString = @"Data Source=.\SQLEXPRESS;Initial Catalog=First-DataBase;Integrated Security=True";<br>
<br>
где SQLEXPRESS - название сервера для подключения<br>
![image](https://github.com/Ksasha05/Sql-DataBase-C-/assets/113344025/65bec770-1abf-47cf-b575-fab44aee5b82)<br>
a First-DataBase - название Базы данных<br>

### Подключение к Базе данных
connection.Open(); //Для первой проверки советую оборачивать в try<br>
![image](https://github.com/Ksasha05/Sql-DataBase-C-/assets/113344025/2cc952ac-50c8-4034-ac92-818b30d9f8c2) <br>

### Создание и использование запроса к Базе данных
//Запрос на языке SQl<br>
string sqlExpression = "SELECT * FROM Table_1 WHERE Name='Alex'";<br>
где Table_1 - Название таблицы<br>

//Создаём объект класса SqlCommand для выполнения команд SQL<br>
SqlCommand command = new SqlCommand(sqlExpression, connection);

//Создаём объект класса SqlDataReader для вычитывания<br>
SqlDataReader reader = command.ExecuteReader();<br>


###Выводим данные из таблицы
(Я выводил в richTextbox)<br>

reader.GetValue(0); - Возвращает значение из столбца, столбцы по порядку 0-1-2-...<br>

На всякий случай, можно сделать проверку на существование данных в таблице<br>
![image](https://github.com/Ksasha05/Sql-DataBase-C-/assets/113344025/0ee6d17a-e2c3-4ecd-982b-9078042812b5)







