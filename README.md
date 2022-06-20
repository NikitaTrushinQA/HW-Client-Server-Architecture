# HW-Client-Server-Architecture
HW
Client_Server
1) Прочитать про клиент-серверную архитектуру
2) Что такое HTTP и HTTPS.

HTTP — это протокол передачи данных между браузером и сервером: страниц, файлов, видеозаписей. HTTPS — это тот же HTTP, но с добавленными методами шифрования данных и проверки безопасности.

«HTTP, или Hyper Text Transfer Protocol, — это протокол передачи гипертекстовой разметки, которая используется для передачи данных в интернете».

HTTPS — это не совсем протокол. Это расширение HTTP-протокола — объединение двух протоколов: HTTP и SSL или HTTP и TLS. 

Протоколы TLS (Transport Layer Security) и SSL (Secure Socket Layer) — криптографические. Это значит, что они позволяют шифровать данные, в нашем случае те, что передаются между браузером и сервером. Расшифровать эти данные могут только сервер и браузер, для всех остальных это будет набор нечитаемых символов.

Примечание: TLS основан на SSL, но второй уже устарел, и вместо него используют TLS. 

3) HTTP методы.

GET
Метод GET запрашивает представление ресурса. Запросы с использованием этого метода могут только извлекать данные.

HEAD
HEAD запрашивает ресурс так же, как и метод GET, но без тела ответа.

POST
POST используется для отправки сущностей к определённому ресурсу. Часто вызывает изменение состояния или какие-то побочные эффекты на сервере.

PUT
PUT заменяет все текущие представления ресурса данными запроса.

DELETE
DELETE удаляет указанный ресурс.

CONNECT
CONNECT устанавливает "туннель" к серверу, определённому по ресурсу.


OPTIONS
OPTIONS используется для описания параметров соединения с ресурсом.

TRACE
TRACE выполняет вызов возвращаемого тестового сообщения с ресурса.

PATCH
PATCH используется для частичного изменения ресурса.

4) HTTP статус коды сервера.

Код ответа (состояния) HTTP показывает, был ли успешно выполнен определённый HTTP запрос. Коды сгруппированы в 5 классов:

Информационные(Informational) 1** -В этот класс выделены коды, информирующие о процессе передачи

Успешные(Success) 2**   -Сообщения данного класса информируют о случаях успешного принятия и обработки запроса клиента. В зависимости от статуса сервер может ещё передать заголовки и тело сообщения.

Перенаправления(Redirection) 3** -Коды этого класса сообщают клиенту, что для успешного выполнения операции необходимо сделать другой запрос, как правило, по другому URI.

Клиентские ошибки(Client error) 4** -Класс кодов  предназначен для указания ошибок со стороны клиента. При использовании всех методов, кроме HEAD, сервер должен вернуть в теле сообщения гипертекстовое пояснение для пользователя.

Серверные ошибки(Server error) 5** -Коды  выделены под случаи необработанных исключений при выполнении операций на стороне сервера. Для всех ситуаций, кроме использования метода HEAD, сервер должен включать в тело сообщения объяснение, которое клиент отобразит пользователю.

Часто встречающиеся типы ответов сервера это:

200 ОК - Страница с кодом 200 ОК говорит об успешной обработке запроса. Это значит, что сервер работает нормально, а поисковый робот получил возможность ее проиндексировать.

201 Created — в результате успешного выполнения запроса был создан новый ресурс. Сервер может указать адреса (их может быть несколько) созданного ресурса в теле ответа, при этом предпочтительный адрес указывается в заголовке Location

202 Accepted — запрос был принят на обработку, но она не завершена. Клиенту не обязательно дожидаться окончательной передачи сообщения, так как может быть начат очень долгий процесс.

300 Multiple Choices — по указанному URI существует несколько вариантов предоставления ресурса

301 Moved Permanently - Код переадресации означает, что URL страницы изменен. Страница по запросу недоступна по прошлому адресу и у нее теперь  есть новый URL.

302 Found - Код означает, что страница временно недоступна по данному адресу, но у нее есть новый временный URL.

304 Not Modified - Этот ответ сервера говорит, что на запрашиваемой странице не было обновлений с момента последнего ее посещения. Получая такой ответ браузер или поисковый робот не будут полностью ее запрашивать с сервера, а возьму сохраненную копию из собственного кеша.

400 Bad Request	- Этот ответ означает, что сервер не понимает запрос из-за неверного синтаксиса. 

401 Unauthorized "Неавторизованно" - Для получения запрашиваемого ответа нужна аутентификация. Статус похож на статус 403, но,в этом случае, аутентификация возможна.

403 Forbidden	"Запрещено" - У клиента нет прав доступа к содержимому, поэтому сервер отказывается дать надлежащий ответ.  

404 Not Found - Ответ сервера (код ошибки) показывающий, что заданная страница (ресурс) больше не существует.

500 Internal Server Error "Внутренняя ошибка сервера" - Сервер столкнулся с ситуацией, которую он не знает как обработать. 

502 Bad Gateway — Номер ошибки сервера, говорящий что прокси сервер не может получить ответ от сайта.

503 Service Unavailable - Ответ сервера (код ошибки) означает, что запроса сервис оказался перегружен и в данный момент не доступен.

504 Gateway Timeout - Этот номер ошибки появляется в результате слишком долгого ответа, когда прокси-сервер не получил результат запроса от вышестоящего сервиса.

5) Что такое ядро браузера. 

Компонент браузера, обрабатывающий HTML, называется HTML-парсером, а модуль, подготавливающий графическое представление HTML-документа, — рендером. 
Ядром браузера мы будем называть совокупность HTML-парсера, рендера и еще нескольких базовых модулей, включая обработчик сценариев Java и JavaScript

6) Какие браузеры какиие ядра используют.

Браузеры на движке WebKit
Движок с открытым кодом, который разрабатывается Apple Computer.
Safari
Konqueror

Браузеры на движке Blink

Создан на основе WebKit, Blink используется для браузера Chromium и как следствие для его производных.
Chromium
Google Chrome
Яндекс.Браузер
Opera
Vivaldi
Microsoft Edge

Браузеры на движке Gecko
Движок с открытым кодом Gecko разработан Mozilla Foundation.
Mozilla Firefox
SeaMonkey
Avant Browser
K-Meleon
Netscape Browser (использует как Gecko, так и Trident)

Браузеры на движках KHTML
Движок с открытым кодом, разработанный в рамках KDE, послужил основой для WebKit.
Konqueror
ABrowse

Браузеры на движке Trident
Microsoft переходит на Blink.
Trident разработан Microsoft для Internet Explorer.
Internet Explorer
Maxthon (прежде известный как MyIE2)
Slim Browser
GreenBrowser

Браузер на движке Presto - более не используется
Opera перешла на движок Blink.
Движок Opera (Presto) лицензирован Adobe и интегрирован в пакет Adobe Creative Suite.
Opera

7) Что такое API.

API (Application Programming Interface — программный интерфейс приложения) — это набор способов и правил, по которым различные программы общаются между собой и обмениваются данными.

8). Что такое ендпоинты.

Эндпоинт представляет собой некий шлюз, который соединяет серверные процессы приложения с внешним интерфейсом. Простыми словами, это адрес, на который отправляются сообщения.
Чтобы понять, что такое эндпоинты, важно упомянуть работу API. API — аббревиатура от application programming interface, что переводится как программный интерфейс приложения. 
Приложения используют API для взаимодействия со сторонними приложениями и своими пользователями.
Чтобы связаться с API, нужно отправить ему запрос. Для корректной обработки запроса клиент должен предоставить универсальный указатель ресурса (URL), метод (HTTP method), и в зависимости от метода добавить заголовки (headers), тело (body), параметры запроса. Заголовки предоставляют метаданные о запросе, а тело содержит данные, например, поля для новой строки в базе данных.

9) URL (URI, URL, URN).

URI (Uniform Resource Identifier) – это строка символов, которая используется для идентификации какого-либо ресурса по его адресу или по его имени, либо по тому и тому вместе.

URL (Uniform Resource Locator) – это строка символов, которая используется для идентификации какого-либо ресурса, но только по его адресу, по его местоположению.

URN (Uniform Resource Name) – это строка символов, которая используется для идентификации какого-либо ресурса, но только по его имени.

URI – имя и адрес ресурса в сети, включает в себя URL и URN

URL – адрес ресурса в сети, определяет местонахождение и способ обращения к нему

URN – имя ресурса в сети, определяет только название ресурса, но не говорит как к нему подключиться

пример:

URI – https://www.kinopoisk.ru/film/435/

URL - https://www.kinopoisk.ru

URN - film/435

10) Идемпотентные HTTP методы.

Метод HTTP является идемпотентным, если повторный идентичный запрос, сделанный один или несколько раз подряд, имеет один и тот же эффект, не изменяющий состояние сервера.
Другими словами, идемпотентный метод не должен иметь никаких побочных эффектов (side-effects), кроме сбора статистики или подобных операций.
Корректно реализованные методы GET, HEAD, PUT и DELETE идемпотентны, но не метод POST(будет добавлять несколько раз информацию). Также все безопасные методы являются идемпотентными.
Для идемпотентности нужно рассматривать только изменение фактического внутреннего состояния сервера, а возвращаемые запросами коды статуса могут отличаться: первый вызов DELETE вернёт код 200, в то время как последующие вызовы вернут код 404. Из идемпотентности DELETE неявно следует, что разработчики не должны использовать метод DELETE при реализации RESTful API с функциональностью удалить последнюю запись.

11) Безопасные HTTP методы.

Безопасными называются те запросы, которые не имеют никакого влияния на ресурс, они просто запрашивают и помогают считывать информацию. 
Примером такого запроса является отображение картинки – через ее адрес идет запрос на сервер в указанную директиву, где должен находится файл с картинкой. Такой тип запроса распространяется на методы HEAD и GET.

12) Иденфикация, Аутентификация, Авторизация.

Идентификация — процесс распознавания пользователя по его идентификатору

Аутентификация — процедура проверки подлинности, доказательство что пользователь именно тот, за кого себя выдает

Авторизация — предоставление определённых прав

Например пользователь хочет войти в свой аккаунт Google:

Для начала система запрашивает логин, пользователь его указывает, система распознает его как существующий — это идентификация.
После этого Google просит ввести пароль, пользователь его вводит, и система соглашается, что пользователь, похоже, действительно настоящий, раз пароль совпал, — это аутентификация.
Скорее всего, Google дополнительно спросит еще и одноразовый код из SMS или приложения. Если пользователь и его правильно введет, то система окончательно согласится с тем, что он настоящий владелец аккаунта, — это двухфакторная аутентификация.
После этого система предоставит пользователю право читать письма в его почтовом ящике и все в таком духе — это авторизация.

13) Что такое IP.

IP-адрес (Internet Protocol) — уникальный числовой идентификатор устройства в компьютерной сети, работающей по протоколу IP.

В сети Интернет требуется глобальная уникальность адреса; в случае работы в локальной сети требуется уникальность адреса в пределах сети.
В версии протокола IPv4 IP-адрес имеет длину 4 байта, а в версии протокола IPv6 — 16 байт.

В 4-й версии IP-адрес представляет собой 32-битное число. 
Как правило, адрес записывается в виде четырёх десятичных чисел значением от 0 до 255 (эквиваленты четырём восьмибитным числам), разделённых точками, например, 192.168.0.3.(ip от 0.0.0.0 до 255.255.255.255).

В 6-й версии IP-адрес является 128-битным. Как правило, адрес записывается в виде восьми четырёхзначных шестнадцатеричных чисел (эквивалентны восьми 16-битным числам), разделённых двоеточиями, например, 2001:0db8:85a3:0000:0000:8a2e:0370:7334. 
Ведущие нули допускается в записи опускать. Нулевые группы, идущие подряд, могут быть опущены, вместо них ставится двойное двоеточие (fe80:0:0:0:0:0:0:1 можно записать как fe80::1). Более одного такого пропуска в адресе не допускается.

14) Что такое октаты в DNS.

Служба доменных имен (DNS, domain name system) — это стандартный протокол, который позволяет пользователям получать доступ к веб-сайтам, используя удобочитаемые адреса. Как телефонная книга позволяет найти имя контакта и узнать его телефонный номер, так и DNS позволяет ввести адрес веб-сайта и автоматически определить его IP-адрес, то есть уникальный идентификатор конкретного устройства (сервера) в компьютерной сети.
Октет, квадрант

Каждое из 8-битных чисел иногда носит название октета ( octet )
или квадранта ( quad ).
255.170.33.8.

255. -первый октет  

170. -второй октет 

33.  -третий октет 

8.   -четвертый октет

15) Что такое порт, сколько портов у Linux сервера.

Порт есть виртуальная точка, в которой сетевые соединения начинаются и заканчиваются.
Порты основаны на программном обеспечении и управляются операционной системой компьютера. Каждый порт связан с определенным процессом или службой.
Номера портов делятся на три диапазоны: 
Известные порты: от 0 до 1023. 
Зарегистрированные порты: от 1024 до 49151. 
Динамические и / или частные порты: от 49152 до 65535.

16) Уровни OSI.

Сетевая модель OSI имеет семь уровней, иерархически расположенных от большего к меньшему. То есть, самым верхним является седьмой (прикладной), а самым нижним — первый (физический). 
![image](https://github.com/NikitaTrushinQA/HW-Client-Server-Architecture/blob/main/OSI.jpg)
Прикладной уровень
Прикладной уровень (уровень приложений; англ. application layer) — верхний уровень модели, обеспечивающий взаимодействие пользовательских приложений с сетью:

позволяет приложениям использовать сетевые службы:
удалённый доступ к файлам и базам данных,
пересылка электронной почты;
отвечает за передачу служебной информации;
предоставляет приложениям информацию об ошибках;
формирует запросы к уровню представления.
Протоколы прикладного уровня: RDP, HTTP, SMTP, SNMP, POP3, FTP, XMPP, OSCAR, Modbus, SIP, TELNET и другие.

Определения протокола прикладного уровня и уровня представления очень размыты, и принадлежность протокола к тому или иному уровню, например протокола HTTPS зависит от конечного сервиса который предоставляет приложение.

В том случае если протокол, например HTTPS, используется для просмотра некоей простой интернет страницы через браузер — его можно рассматривать как протокол прикладного уровня. В том же случае если протокол HTTPS используется как низкоуровневый протокол для передачи финансовой информации например по протоколу ISO 8583, то протокол HTTPS будет являться протоколом уровня представления, а протокол ISO 8583 — будет протоколом уровня приложения. 

Уровень представления

Уровень представления (англ. presentation layer) обеспечивает преобразование протоколов и кодирование/декодирование данных. Запросы приложений, полученные с прикладного уровня, на уровне представления преобразуются в формат для передачи по сети, а полученные из сети данные преобразуются в формат приложений. На этом уровне может осуществляться сжатие/распаковка или шифрование/дешифрование, а также перенаправление запросов другому сетевому ресурсу, если они не могут быть обработаны локально.

Уровень представлений обычно представляет собой промежуточный протокол для преобразования информации из соседних уровней. Это позволяет осуществлять обмен между приложениями на разнородных компьютерных системах прозрачным для приложений образом. Уровень представлений обеспечивает форматирование и преобразование кода. Форматирование кода используется для того, чтобы гарантировать приложению поступление информации для обработки, которая имела бы для него смысл. При необходимости этот уровень может выполнять перевод из одного формата данных в другой.

Уровень представлений имеет дело не только с форматами и представлением данных, он также занимается структурами данных, которые используются программами. Таким образом, уровень 6 обеспечивает организацию данных при их пересылке.

Чтобы понять, как это работает, представим, что имеются две системы. Одна использует для представления данных расширенный двоичный код обмена информацией EBCDIC, например, это может быть мейнфрейм компании IBM, а другая — американский стандартный код обмена информацией ASCII (его использует большинство других производителей компьютеров). Если этим двум системам необходимо обменяться информацией, то нужен уровень представлений, который выполнит преобразование и осуществит перевод между двумя различными форматами.

Другой функцией, выполняемой на уровне представлений, является шифрование данных, которое применяется в тех случаях, когда необходимо защитить передаваемую информацию от доступа несанкционированными получателями. Чтобы решить эту задачу, процессы и коды, находящиеся на уровне представлений, должны выполнить преобразование данных. На этом уровне существуют и другие подпрограммы, которые сжимают тексты и преобразовывают графические изображения в битовые потоки, так, что они могут передаваться по сети.

Стандарты уровня представлений также определяют способы представления графических изображений. Для этих целей может использоваться формат PICT — формат изображений, применяемый для передачи графики QuickDraw между программами.

Другим форматом представлений является тэгированный формат файлов изображений TIFF, который обычно используется для растровых изображений с высоким разрешением. Следующим стандартом уровня представлений, который может использоваться для графических изображений, является стандарт, разработанный Объединённой экспертной группой по фотографии (Joint Photographic Expert Group); в повседневном пользовании этот стандарт называют просто JPEG.

Существует другая группа стандартов уровня представлений, которая определяет представление звука и кинофрагментов. Сюда входят интерфейс электронных музыкальных инструментов (англ. Musical Instrument Digital Interface, MIDI) для цифрового представления музыки, разработанный Экспертной группой по кинематографии стандарт MPEG, используемый для сжатия и кодирования видеороликов на компакт-дисках, хранения в оцифрованном виде и передачи со скоростями до 1,5 Мбит/с, и QuickTime — стандарт, описывающий звуковые и видео элементы для программ, выполняемых на компьютерах Macintosh и PowerPC.

Протоколы уровня представления: AFP — Apple Filing Protocol, ICA — Independent Computing Architecture, LPP — Lightweight Presentation Protocol, NCP — NetWare Core Protocol, NDR — Network Data Representation, XDR — eXternal Data Representation, X.25 PAD — Packet Assembler/Disassembler Protocol.

Сеансовый уровень

Сеансовый уровень (англ. session layer) модели обеспечивает поддержание сеанса связи, позволяя приложениям взаимодействовать между собой длительное время. Уровень управляет созданием/завершением сеанса, обменом информацией, синхронизацией задач, определением права на передачу данных и поддержанием сеанса в периоды неактивности приложений.

Протоколы сеансового уровня: H.245 (Call Control Protocol for Multimedia Communication), ISO-SP (OSI Session Layer Protocol (X.225, ISO 8327)), iSNS (Internet Storage Name Service), L2F (Layer 2 Forwarding Protocol), L2TP (Layer 2 Tunneling Protocol), NetBIOS (Network Basic Input Output System), PAP (Password Authentication Protocol), PPTP (Point-to-Point Tunneling Protocol), RPC (Remote Procedure Call Protocol), RTCP (Real-time Transport Control Protocol), SMPP (Short Message Peer-to-Peer), SCP (Session Control Protocol), ZIP (Zone Information Protocol), SDP (Sockets Direct Protocol)…

Транспортный уровень

Транспортный уровень (англ. transport layer) модели предназначен для обеспечения надёжной передачи данных от отправителя к получателю. При этом уровень надёжности может варьироваться в широких пределах. Существует множество классов протоколов транспортного уровня, начиная от протоколов, предоставляющих только основные транспортные функции (например, функции передачи данных без подтверждения приёма), и заканчивая протоколами, которые гарантируют доставку в пункт назначения нескольких пакетов данных в надлежащей последовательности, мультиплексируют несколько потоков данных, обеспечивают механизм управления потоками данных и гарантируют достоверность принятых данных. Например, UDP ограничивается контролем целостности данных в рамках одной датаграммы и не исключает возможности потери пакета целиком или дублирования пакетов, нарушение порядка получения пакетов данных; TCP обеспечивает надёжную непрерывную передачу данных, исключающую потерю данных или нарушение порядка их поступления или дублирования, может перераспределять данные, разбивая большие порции данных на фрагменты и наоборот, склеивая фрагменты в один пакет.

Протоколы транспортного уровня: ATP (AppleTalk Transaction Protocol), CUDP (Cyclic UDP), DCCP (Datagram Congestion Control Protocol), FCP (Fibre Channel Protocol), IL (IL Protocol), NBF (NetBIOS Frames protocol), NCP (NetWare Core Protocol), SCTP (Stream Control Transmission Protocol), SPX (Sequenced Packet Exchange), SST (Structured Stream Transport), TCP (Transmission Control Protocol), UDP (User Datagram Protocol).

Сетевой уровень

Сетевой уровень (англ. network layer) модели предназначен для определения пути передачи данных. Отвечает за трансляцию логических адресов и имён в физические, определение кратчайших маршрутов, коммутацию и маршрутизацию, отслеживание неполадок и «заторов» в сети.

Протоколы сетевого уровня маршрутизируют данные от источника к получателю. Работающие на этом уровне устройства (маршрутизаторы) условно называют устройствами третьего уровня (по номеру уровня в модели OSI).

Протоколы сетевого уровня: IP/IPv4/IPv6 (Internet Protocol), IPX (Internetwork Packet Exchange, протокол межсетевого обмена), X.25 (частично этот протокол реализован на уровне 2), CLNP (сетевой протокол без организации соединений), IPsec (Internet Protocol Security).

Протоколы маршрутизации — RIP (Routing Information Protocol), OSPF (Open Shortest Path First).

Канальный уровень

Канальный уровень (англ. data link layer) предназначен для обеспечения взаимодействия сетей на физическом уровне и контроля ошибок, которые могут возникнуть. Полученные с физического уровня данные, представленные в битах, он упаковывает в кадры, проверяет их на целостность и, если нужно, исправляет ошибки (либо формирует повторный запрос повреждённого кадра) и отправляет на сетевой уровень. Канальный уровень может взаимодействовать с одним или несколькими физическими уровнями, контролируя и управляя этим взаимодействием.

Спецификация IEEE 802 разделяет этот уровень на два подуровня: MAC (англ. media access control) регулирует доступ к разделяемой физической среде, LLC (англ. logical link control) обеспечивает обслуживание сетевого уровня.

На этом уровне работают коммутаторы, мосты и другие устройства. Эти устройства используют адресацию второго уровня (по номеру уровня в модели OSI).

Протоколы канального уровня: ARCnet, ATM, Controller Area Network (CAN), Econet, IEEE 802.3 (Ethernet), Ethernet Automatic Protection Switching (EAPS), Fiber Distributed Data Interface (FDDI), Frame Relay, High-Level Data Link Control (HDLC), IEEE 802.2 (предоставляет функции LLC для подуровня IEEE 802 MAC), Link Access Procedures, D channel (LAPD), IEEE 802.11 wireless LAN, LocalTalk, Multiprotocol Label Switching (MPLS), Point-to-Point Protocol (PPP), Point-to-Point Protocol over Ethernet (PPPoE), Serial Line Internet Protocol (SLIP, устарел), StarLan, Token ring, Unidirectional Link Detection[en] (UDLD), x.25, ARP.

При разработке стеков протоколов на этом уровне решаются задачи помехоустойчивого кодирования. К таким способам кодирования относится код Хемминга, блочное кодирование, код Рида — Соломона.

В программировании этот уровень представляет драйвер сетевой платы, в операционных системах имеется программный интерфейс взаимодействия канального и сетевого уровней между собой. Это не новый уровень, а просто реализация модели для конкретной ОС. Примеры таких интерфейсов: ODI (англ.), NDIS, UDI.

Физический уровень

Физический уровень (англ. physical layer) — нижний уровень модели, который определяет метод передачи данных, представленных в двоичном виде, от одного устройства (компьютера) к другому. Составлением таких методов занимаются разные организации, в том числе: Институт инженеров по электротехнике и электронике, Альянс электронной промышленности, Европейский институт телекоммуникационных стандартов и другие. Осуществляют передачу электрических или оптических сигналов в кабель или в радиоэфир и, соответственно, их приём и преобразование в биты данных в соответствии с методами кодирования цифровых сигналов.

На этом уровне также работают концентраторы, повторители сигнала и медиаконвертеры.

Функции физического уровня реализуются на всех устройствах, подключенных к сети. Со стороны компьютера функции физического уровня выполняются сетевым адаптером или последовательным портом. К физическому уровню относятся физические, электрические и механические интерфейсы между двумя системами. Физический уровень определяет такие виды сред передачи данных как оптоволокно, витая пара, коаксиальный кабель, спутниковый канал передач данных и т. п. Стандартными типами сетевых интерфейсов, относящимися к физическому уровню, являются: V.35, RS-232, RS-485, RJ-11, RJ-45, разъёмы AUI и BNC.

При разработке стеков протоколов на этом уровне решаются задачи синхронизации и линейного кодирования. К таким способам кодирования относится код NRZ, код RZ, MLT-3, PAM5, Манчестер II.

Протоколы физического уровня: IEEE 802.15 (Bluetooth), IRDA, EIA RS-232, EIA-422, EIA-423, RS-449, RS-485, DSL, ISDN, SONET/SDH, 802.11 Wi-Fi, Etherloop, GSM Um radio interface, ITU и ITU-T, TransferJet[en], ARINC 818, G.hn/G.9960, Modbus Plus.

17) Хедеры http запросов.
