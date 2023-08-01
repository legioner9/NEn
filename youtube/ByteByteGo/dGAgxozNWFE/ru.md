Кэширование — распространенный в современных компьютерах метод повышения производительности.
производительность системы и сократить время отклика.
От переднего конца до заднего конца,
кэширование играет решающую роль в повышении эффективности различных приложений и систем.
Типичная системная архитектура включает несколько уровней кэширования.
На каждом уровне есть несколько стратегий и механизмов кэширования.
данных в зависимости от требований и ограничений конкретного приложения.
Прежде чем углубиться в типичную системную архитектуру,
давайте увеличим масштаб и посмотрим, насколько распространено кэширование на каждом компьютере.
Давайте сначала посмотрим на компьютерное оборудование.
Наиболее распространенными аппаратными кэшами являются кэши L1, L2 и L3.
Кэш L1 — это самый маленький и быстрый кэш, обычно встроенный в сам ЦП.
Он хранит часто используемые данные и инструкции, позволяя ЦП
быстро получить к ним доступ, не извлекая их из более медленной памяти.
Кэш L2 больше, но медленнее, чем кеш L1,
и обычно находится на кристалле ЦП или на отдельном чипе.
Кэш L3 даже больше и медленнее, чем кеш L2, и часто распределяется между несколькими ядрами ЦП.
Еще одним распространенным аппаратным кэшем является резервный буфер трансляции (TLB).
В нем хранятся недавно использованные преобразования виртуальных адресов в физические.
Он используется процессором для быстрой трансляции адресов виртуальной памяти.
к адресам физической памяти, сокращая время, необходимое для доступа к данным из памяти.
На уровне операционной системы есть кэш страниц и другие кэши файловой системы.
Кэш страниц управляется операционной системой и находится в основной памяти.
Он используется для хранения недавно использованных дисковых блоков в памяти.
Когда программа запрашивает данные с диска,
операционная система может быстро извлекать данные из памяти, а не читать их с диска.
Существуют и другие кэши, которыми управляет операционная система, например кэш инодов.
Эти кэши используются для ускорения операций файловой системы за счет уменьшения
количество обращений к диску, необходимое для доступа к файлам и каталогам.
Теперь давайте уменьшим масштаб и посмотрим, как кэширование используется в типичной архитектуре системы приложений.
В интерфейсе приложения
веб-браузеры могут кэшировать ответы HTTP, чтобы обеспечить более быстрое извлечение данных.
Когда мы запрашиваем данные через HTTP в первый раз,
и он возвращается с политикой истечения срока действия в заголовке HTTP;
мы снова запрашиваем те же данные, и браузер возвращает данные из своего кеша, если они доступны.
Сети доставки контента (CDN) широко используются для улучшения доставки статического контента,
таких как изображения, видео и другие веб-ресурсы.
Одним из способов, которым CDN ускоряют доставку контента, является кэширование.
Когда пользователь запрашивает контент из CDN,
сеть CDN ищет запрошенный контент в своем кеше.
Если содержимое еще не находится в кеше,
CDN получает его с исходного сервера и кэширует на своих пограничных серверах.
Когда другой пользователь запрашивает тот же контент, CDN может доставить контент напрямую.
из его кеша, избавляя от необходимости снова получать его с исходного сервера.
Некоторые балансировщики нагрузки могут кэшировать ресурсы, чтобы снизить нагрузку на внутренние серверы.
Когда пользователь запрашивает контент с сервера за балансировщиком нагрузки,
балансировщик нагрузки может кэшировать ответ и предоставлять его непосредственно будущим пользователям, которые запрашивают
тот же контент. Это может улучшить время отклика и снизить нагрузку на внутренние серверы.
Кэширование не всегда должно быть в памяти. В инфраструктуре обмена сообщениями
брокеры сообщений, такие как Kafka, могут кэшировать огромное количество сообщений на диске.
Это позволяет потребителям получать сообщения в своем собственном темпе. 
сообщения могут кэшироваться в течение длительного периода времени в зависимости от политики хранения.
Распределенные кэши, такие как Redis, могут хранить пары ключ-значение в памяти,
обеспечение высокой производительности чтения/записи по сравнению с традиционными базами данных
Полнотекстовые поисковые системы, такие как Elastic Search, могут индексировать данные для документов.
поиск и поиск по журналам, обеспечивающий быстрый и эффективный доступ к конкретным данным.
Даже внутри базы данных доступно несколько уровней кэширования.
Данные обычно записываются в журнал с упреждающей записью (WAL) перед индексацией в B-дереве.
Пул буферов — это область памяти, используемая для кэширования результатов запроса.
в то время как материализованные представления могут предварительно вычислять результаты запроса для повышения производительности.
Журнал транзакций записывает все транзакции и обновления базы данных,
в то время как журнал репликации отслеживает состояние репликации в кластере базы данных.
В целом, кэширование данных является важным методом оптимизации производительности системы.
и сокращение времени отклика. От переднего конца до заднего конца,
существует множество уровней кэширования для повышения эффективности различных приложений и систем.
Если вам нравятся наши видео, вам также может понравиться наш информационный бюллетень по проектированию систем. Он охватывает темы и
тенденции в проектировании крупномасштабных систем. Нам доверяют 300 000 читателей. Подпишитесь на blog.bytebytego.com