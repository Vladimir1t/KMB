## Клиент-серверное приложение

Программа, реализующующая простое клиент-серверное приложение: клиент 
устанавливает связь с сервером, расположенным по заранее определённому адресу, на что 
сервер посылает ему сообщение, в котором сообщает адрес клиента.

---
В режиме сервера (флаг *-s*) программа:
- слушает введённый адрес в бесконечном цикле;
-  при получении запроса отправляет ответ, содержащий IP-адрес и порт клиента.
В режиме клиента программа:
- посылает запрос серверу по указанному адресу;
- ждёт ответ сервера;
- выводит полученный ответ в формате <адрес>:<порт>;
- завершает свою работу.
  
В зависимости от флагов запуска связь устанавливается через сокеты по протоколу TCP 
или UDP. Протоколу TCP соответствует флаг *-t*, UDP - *-u*.
Программа не может использовать одновременно два протокола, поэтому одновременное использование флагов
*-t* и *-u* недопустимо, программа должна проверять корректность переданных 
параметров при разборе введенной команды. По умолчанию используется TCP (в случае 
если не указан ни один параметр)

# Пример: 
```
  python3 kmb.py 127.0.0.1 13000 -s -t -f log_output

```
- запуск программы в режиме сервера по протоколу TCP с записью логов в файл 
log_output;
- программа открывает сокет по адресу 127.0.0.1:13000