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
<p>Транзакционная модель. Это конечно преимущество не столько для администратора, сколько для программиста. Программист может объединить операции с базой в транзакцию, с кучей вытекающих из этого профита. Это основная причина по которой архитекторы выбирают InnoDB.</p>
<p>Блокировка на уровне строки. В отличии от MyISAM, где идет блокировка на уровне таблицы, в InnoDB блокировка осуществляется на уровне строки. Проблема конкурентных блокировок стоит не так остро как в MyISAM, однако все таки присутствует. Но об этом ниже.</p>
<p>Защита от сбоев. InnoDB более устойчивая к сбоям, если сказать точнее, InnoDB намного лучше восстанавливается после сбоев и практически не теряет данные. Для восстановления же MyISAM таблиц зачастую требуется потушить MySQL сервер и вручную восстанавливать таблицы утилитой myisamchk. Результатом работы myisamchk зачастую может оказаться частичная или полная потеря данных в таблице. InnoDB восстанавливается автоматически.</p>
<p>Качественная работа с IO. InnoDB имеет свой собственный Buffer Pool в памяти, где держит таблицы. Для InnoDB можно отключить системную буферизацию IO при работе с таблицами InnoDB. Таким образом, можно сказать что в InnoDB нет двойной буферизации (как в MyISAM), следовательно, оперативная память разумно расходуется.</p>
<p>MyISAM конечно же тоже обладает преимуществами, в основном это простота и скорость. На небольших объемах данных и большом количестве операций чтения лучше хранилища не найти, если конечно вам не нужны транзакции. Но сейчас не об этом. На этой ноте про MyISAM больше ни слова.</p>

<p>InnoDB не готова корректно работать из коробки на высоких нагрузках. Надо хорошо понимать о происходящих в недрах InnoDB процессах дабы правильно настроить этот тип хранилища.</p>
