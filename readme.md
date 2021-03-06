# M2 - App Log (master)
---
## Оглавление

  - [Ссылки](#link1)
  - [Введение](#link2)
	- [Как сделать запись в лог](#link3)
	- [Ограничения на кол-во хранимых данных](#link4)
	- [Теги](#link5)
	- [Как читать лог](#link6)
	- [Как очистить лог](#link7)
  - [Заметки к релизам](#link100)

---

## Ссылки <a id="link1"></a>
```

  > Адрес репозитория пакета M2 на github
      https://github.com/4gekkman/m2

	
			
```

## Введение <a id="link2"></a>
```

  ● Это М-пакет для ведения лога приложения.


```
## Как сделать запись в лог <a id="link3"></a>
```

  # Способ №1
    - С помощью функции-хелпера write2log из R1.
    - Пример:

        write2log('hello world', ['tag1', 'tag2']);

    - Хелпер write2log возбуждает событие с ключём 'm2:write2log'.
    - Обработчик H1_catch2log пакета ловит его, и делает запись в лог.

  # Способ №2
    - С помощью консольной команды m2:writ2log
    - Пример (надо вводить в терминале, в корневом каталоге приложения):

        php artisan m2:write2log 'hello world'


```
## Ограничения на кол-во хранимых данных <a id="link4"></a>
```
  # Есть 3 типа ограничений
    ● По кол-ву дней, в течение которых хранить запись.
    ● По общему кол-ву записей в логе.
    ● Комбинация первых двух.

  # Где настроить
    - В конфиге пакета.
    - MAX кол-во дней для хранения: 1825 (5 лет).
    - MAX кол-во записей: 1000000 штук.

  # Как реализуются
    - После каждой записи в лог, запускается команда C2_limitator.
    - Она смотрит настройки, и реализует заданную политику ограничений.

## Теги <a id="link5"></a>
```

  ● Каждую запись в лог можно связывать с любым набором тегов.
  ● Для этого надо при осуществлении записи передать массив тегов.
  ● Потом по этим тегам удобно будет искать записи в логе.


```
## Как читать лог <a id="link6"></a>
```

  # Способ №1: с помощью демона в терминале
    - Надо запустить отдельный экземпляр терминала.
    - В нём перейти в каталог приложения, и запустить демона командой:

        m2:listener N

    - Где N необязательный параметр, период обновления в секундах (5 сек. по умолчанию).
    - По умолчанию, в терминал будут загружены 100 последних сообщений лога.
    - И каждые N секунд, он будет проверять, не появились ли новые, и если да, показывать.


```
## Как очистить лог <a id="link7"></a>
```

  ● Для этого есть к.команда m2:clear.
  ● Она удаляет все-все записи из лога.


```
## Заметки к релизам <a id="link100"></a>
```

  1.0.0
    - Первый релиз.

```










