PHPUNIT

<strong>Модульное тестирование</strong>, или <strong>юнит-тестирование</strong> (англ. unit testing) — процесс в программировании, позволяющий проверить на корректность отдельные модули исходного кода программы.
<p>Цель модульного тестирования — изолировать отдельные части программы и показать, что по отдельности эти части работоспособны.</p>
<p>Поскольку некоторые классы могут использовать другие классы, тестирование отдельного класса часто распространяется на связанные с ним. Например, класс пользуется базой данных; в ходе написания теста программист обнаруживает, что тесту приходится взаимодействовать с базой. Это ошибка, поскольку тест не должен выходить за границу класса. В результате разработчик абстрагируется от соединения с базой данных и реализует этот интерфейс, используя свой собственный mock-объект. Это приводит к менее связанному коду, минимизируя зависимости в системе.</p>
<p>Как и любая технология тестирования, модульное тестирование не позволяет отловить все ошибки программы. В самом деле, это следует из практической невозможности трассировки всех возможных путей выполнения программы, за исключением простейших случаев. Кроме того, происходит тестирование каждого из модулей по отдельности. Это означает, что ошибки интеграции, системного уровня, функций, исполняемых в нескольких модулях, не будут определены. Кроме того, данная технология бесполезна для проведения тестов на производительность. Таким образом, модульное тестирование более эффективно при использовании в сочетании с другими методиками тестирования.</p>
<p>В <strong>экстремальном программировании</strong> используются модульные тесты для разработки через тестирование. Для этого разработчик до написания кода пишет тесты, отражающие требования к модулю. Очевидно, ни один из этих тестов до написания кода работать не должен. Дальнейший процесс сводится к написанию кратчайшего кода, удовлетворяющего данному набору тестов.</p>
<p>Рефакторинг следует отличать от оптимизации производительности. Как и рефакторинг, оптимизация обычно не изменяет поведение программы, а только ускоряет её работу. Но оптимизация часто затрудняет понимание кода, что противоположно рефакторингу</p>
<p><strong>Mock-объект</strong> (от англ. mock object, буквально: объект-пародия, объект-имитация) представляет собой конкретную фиктивную реализацию интерфейса, предназначенную исключительно для тестирования.</p>
<a href="http://maxshulga-ru.blogspot.ru/2012/03/mock-vs-stub.html">Mocks vs. Stubs</a>
<p>стабы предназначены для получения нужного состояния тестируемого объекта, а моки применяются для проверки ожидаемого поведения тестируемого объекта.</p>
<hr/>
DB

<a href="http://datasql.ru/basesql/16.htm">Транзакции и блокировки</a>
<h3>Почему народ выбирает InnoDB? InnoDB обладает преимуществами перед MyISAM</h3>
<a href="http://www.pentarh.com/wp/2011/03/02/mysql-innodb-highload-optimization/">оригинал</a>
<ul>
  <li>Транзакционная модель. Это конечно преимущество не столько для администратора, сколько для программиста.       Программист может объединить операции с базой в транзакцию, с кучей вытекающих из этого профита. Это основная причина по которой архитекторы выбирают InnoDB.</li>
  <li>Блокировка на уровне строки. В отличии от MyISAM, где идет блокировка на уровне таблицы, в InnoDB блокировка осуществляется на уровне строки. Проблема конкурентных блокировок стоит не так остро как в MyISAM, однако все таки присутствует. Но об этом ниже.</li>
  <li>Защита от сбоев. InnoDB более устойчивая к сбоям, если сказать точнее, InnoDB намного лучше восстанавливается после сбоев и практически не теряет данные. Для восстановления же MyISAM таблиц зачастую требуется потушить MySQL сервер и вручную восстанавливать таблицы утилитой myisamchk. Результатом работы myisamchk зачастую может оказаться частичная или полная потеря данных в таблице. InnoDB восстанавливается автоматически.</li>
  <li>Качественная работа с IO. InnoDB имеет свой собственный Buffer Pool в памяти, где держит таблицы. Для InnoDB можно отключить системную буферизацию IO при работе с таблицами InnoDB. Таким образом, можно сказать что в InnoDB нет двойной буферизации (как в MyISAM), следовательно, оперативная память разумно расходуется.</li>
</ul>
<p>MyISAM конечно же тоже обладает преимуществами, в основном это простота и скорость. На небольших объемах данных и большом количестве операций чтения лучше хранилища не найти, если конечно вам не нужны транзакции. Но сейчас не об этом. На этой ноте про MyISAM больше ни слова.</p>

<p>InnoDB не готова корректно работать из коробки на высоких нагрузках. Надо хорошо понимать о происходящих в недрах InnoDB процессах дабы правильно настроить этот тип хранилища.</p>

<h3><a href="http://www.jeo.ru/mysql-harakteristiki-tablitsyi-myisam.html">MySQL - характеристики таблицы MyISAM</a></h3>
Каждая таблица хранится в трех файлах. Названия файлов совпадают с названия таблицы, а расширения файлов указывают на тип хранимых данных.
<ul>
<li>*.frm - содержит формат таблицы</li>
<li>*.myd (MYData) - содержит данные</li>
<li>*.myi (MYIndex) - содержит индексы</li>
</ul>
Характеристики механизма хранения данных MyISAM
<ul>
<li>Все данные хранятся с младшим байтом в начале. Запись данных в обратном порядке делает их платформо независимым. По заверениям разработчиков запись в обратном порядке не приводит к существенному снижению быстродействия.</li>
<li>Все числовые ключи хранятся со старшим байтом в начале.</li>
<li>Размер базы данных ограничен допустимым размером файла в используемой файловой системе.</li>
<li>Максимальное число строк составляет 2^32 (~4.295E+09), при компиляции MySQL с параметром --with-big-tables максимальное число строк увеличивается до (2^32)^2 (1.844E+19)</li>
<li>Максимальное число индексов для одной таблицы составляет 64. При компиляции MySQL с параметром --with-max-indexes=N (N&lt;=128) число индексов можно увеличить до 128.</li>
<li>Максимальное число полей для одного индекса составляет 16.</li>
<li>Максимальная длина ключа составляет 1000 байт.</li>
<li>Когда строки записываются в отсортированном порядке (для полей с AUTO_INCREMENT), то дерево индекса разбивается так что верхний узел содержит один ключ. Это позволяет оптимизировать место используемое под индекс.</li><li>Для таблицы можно создать только одно поле AUTO_INCREMENT.</li>
<li>Повторное использование значений полученных для поля AUTO_INCREMENT не происходит даже после удаления строки с последним полученным значением. Значения получаемые для поля AUTO_INCREMENT можно изменить использовав SQL запрос. ALTER TABLE `table_name` AUTO_INCREMENT = 123.</li><li>Строки с динамически изменяемым размером менее фрагментируются когда удаление, изменение и запись используются в перемешку. Это достигается благодаря автоматическому объединению смежных удаленных блоков или благодаря расширению изменяемого блока в случае когда последующий блок удален.</li><li>MyISAM поддерживает параллельную запись и чтение строк (конкурентная вставка). Для управления паралельной записью и чтением существует параметр concurrent_insert.</li>
<li>0 - параллельная запись отключенна.</li>
<li>1 - параллельная запись только для не фрагментированных таблиц (таблиц не имеющих свободных блоков в середине файла с данными). Значение по умолчанию.</li>
<li>2 - параллельная запись включенна. В этом режиме все новые строки вставляются в конец файла данных если параллельно происходит чтение данных.</li>
<li>Существует возможность размещения файла данных и файла индексов на разных физических устройствах, задается при создании таблицы параметрами DATA DIRECTORY и INDEX DIRECTORY. Подобное разделение может увеличить скорость выполнения запросов к таблице.</li>
<li>BLOB и TEXT поля могут индексироватся.</li>
<li>Возможно использование значения NULL в индексируемых полях. Может привести к увеличению размеров индекса.</li>
<li>Поля таблицы могут иметь различную кодировку.</li>
<li>В индекс файле содержится флаг отвечающий за нормальное закрытие таблицы. Если MySQL запускается с параметром --myisam-recover. При запуске MySQL таблицы с типом хранения данных MyISAM автоматически проверяются и при необходимости востанавливаются.</li>
<li>Поля типа VARCHAR начинаются с данных (1-2 байта) о размере поля.</li>
<li>Поля VARCHAR могут иметь как фиксированную так и динамически меняющиюся размерность.</li>
<li>Суммарная размерность полей VARCHAR и CHAR в одной таблице не должна превышать 64KB.</li>
<li>Возможна произвольная длина для полей UNIQUE. </li>
</ul>
<h3><a href="http://www.jeo.ru/mysql-harakteristiki-tablitsyi-innodb.html">MySQL - характеристики таблицы InnoDB</a></h3>
InnoDB это транзакционная база данных с возможностью отмены транзакции, а также с блокировкой доступа на уровне строк. Таблицы InnoDB также позволяют использовать внешние ключи (FOREIGN KEY).

<p>В InnoDB есть свой собственный буфер для кэширования данных и индексов в памяти. Таблицы InnoDB и их индексы находятся в общем хранилище, хранилище может состоять из нескольких файлов. В отличии от MyISAM таблицы InnoDB могут быть любого размера, не зависимо от ограничений операционной системы.</p>

<p>Назначение транзакционной модели InnoDB заключается в том, чтобы совместить лучшие свойства многовариантной базы данных и традиционной двухфазной блокировки. Для таблиц InnoDB осуществляется блокировка на уровне строки и запросы по умолчанию запускаются как целостное считывание без блокировок, подобно тому, как это реализовано в Oracle. Хранение таблицы блокировок InnoDB организовано таким образом что несколько пользователей могут блокировать любую строку или любой набор строк в базе данных, не занимая всю память, доступную для InnoDB.</p>

<p>В таблицах InnoDB все действия пользователей осуществляются при помощи транзакций. Если в MySQL используется режим автоматической фиксации, то для каждого оператора SQL будет создаваться отдельная транзакция. Если режим автоматической фиксации отключен, то мы предполагаем, что у пользователя постоянно имеется открытая транзакция. Если он выполняет оператор SQL COMMIT или ROLLBACK, которые завершают текущую транзакцию, сразу же запускается новая транзакция. Оба упомянутых оператора снимают все блокировки InnoDB, которые были установлены во время выполнения текущей транзакции. Оператор COMMIT означает, что изменения, внесенные во время выполнения текущей транзакции, зафиксированы и становятся видимыми для других пользователей. Оператор ROLLBACK отменяет все изменения, внесенные текущей транзакцией.</p>
<ul>
  <li><a href="http://habrahabr.ru/post/148446/">Немного о связываемых переменных (prepared statements)</a></li>
  <li><a href="http://habrahabr.ru/post/135217/">MySQL: уровни изоляции транзакций</a></li>
  <li><a href="http://ru.wikipedia.org/wiki/%D0%A3%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C_%D0%B8%D0%B7%D0%BE%D0%BB%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D0%BE%D1%81%D1%82%D0%B8_%D1%82%D1%80%D0%B0%D0%BD%D0%B7%D0%B0%D0%BA%D1%86%D0%B8%D0%B9">Уровень изолированности транзакций (Wiki)</a></li>
  <li><a href="http://www.skillz.ru/dev/php/article-Obyasnenie_SQL_obedinenii_JOIN_INNER_OUTER.html">Объяснение SQL объединений JOIN/INNER/OUTER</a></li>
  <li><a href="http://www.tomjewett.com/dbdesign/dbdesign.php?page=class.php">UML design</a></li>
  <li><a href="http://denis.in.ua/foreign-keys-in-mysql.htm">Использование внешних ключей в MySQL</a></li>
  <li><a href="http://www.interface.ru/home.asp?artId=23781">Первичный ключ - составной или суррогатный?</a></li>
</ul>
