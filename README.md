# drgunpack5
Dragon UnPACKer v5.7.0 Beta 
Dragon UnPACKer v5.7.0 Бета-версия MPL 1.1 с открытым исходным
кодом от Alexande "Elbereth" Devilliers 04.08.2014
===============================================================================

  ** ПРИМЕЧАНИЕ: Это незавершенная сборка (Альфа, бета-версия или релиз-кандидат),
используйте ее на свой страх и риск. Может быть нестабильным. Вас предупреждали! **

  Файлы документации не обновлялись с момента последнего стабильного выпуска (v5.6.2).
  
-------------------------------------------------------------------------------
Основная версия программы и история версий:

Версия 5.7.0.284
Бета-версия (SVN Release 695) [04.08.2014]

 я обновил лицензию до MPL 2.0 (с MPL 1.1).
 ! Добавлена дополнительная проверка в процедуре извлечения, чтобы избежать прохождения мимо конца
файла.
 ! Исправлено множество утечек памяти (спасибо FastMM!).
 ! Исправлена функция создания списка (макросы могут быть прописными или строчными).
 * Изменены макросы в HTML-шаблоне DUP4 (версия 1.2) для списков на прописные буквы
   во всяком случае, чтобы быть последовательным.
 * Переработан класс TDrivers, чтобы прекратить использование указателей, замененных динамическими
   массивы. Будет проще в обслуживании и менее подвержен ошибкам.
   Также представлен DUDI v6, который использует функцию обратного вызова каждый раз, когда вводится запись
   нуждается в дополнении. Это совершенно не похоже на то, что DUDI v5 был ядром
   программа вызывает функцию подключаемого модуля для всех найденных записей.
   Оба старых метода DUDI v1-v5 и v6 поддерживаются Dragon UnPACKer
   5.7.0+.
   Новый кэш каталогов должен быть таким же быстрым (если не быстрее), чем старый.
   Примечание: Только драйвер main и ZIP были адаптированы к DUDI v6.
 + Добавлены FastCode и FastMove.
   http://fastcode.sourceforge.net/
 ! Исправлена поддержка нескольких плагинов преобразования во время предварительного просмотра.
 * Пересмотрел то, как TDrivers и TPlugins были глобальными переменными, теперь они стали свойствами
   из основной формы. Оба больше не имеют прямого доступа к основным компонентам формы
   и пройдите через командный класс-оболочку.
 * Полностью обновлены функции ведения журнала.
   Там все еще могли бы быть какие-то места, где он плохо себя ведет.
 + Обновлена старая функциональность "Внешний вид", чтобы ее было гораздо проще поддерживать и
изменять "Тему" (на данный момент файлы находятся в папке).
   Не очень хорошо с Delphi 7, но должно проложить путь к Lazarus.
 + Добавлено цепное преобразование из плагинов во внутреннюю библиотеку изображений Vampyre.
   Это позволяет плагинам просто конвертировать, например, в .DDS, и
цепочка также будет предлагать BMP, PNG и TGA без дополнительной работы с
   подключаемый модуль.
 + Добавлено прямое преобразование внутренней библиотеки изображений Vampyre в совместимые
   файлы. Например: .DDS в .BMP/.PNG/.TGA.
 ! Исправлена функция обратного вызова SetPercent, которая обновляла компонент
при каждом вызове, теперь она будет обновляться только в том случае, если значение изменилось...
   Это привело к значительному ускорению загрузки некоторых форматов, например
   пример: загрузка POD5 в предыдущей версии: ~17 секунд, сейчас: ~7 секунд.
 i HyperRipper v5.6b:
   ! Исправлена проверка работоспособности алгоритма поиска BIK.
     Следует избегать некоторых ложноположительных срабатываний.
   ! Исправлена утечка памяти из-за того, что компонент TBufferedFS не был освобожден:
     Переключился обратно на использование THandleStream вместо TBufferedFS.
	 Освободите THandleStream, но оставьте дескриптор открытым и передайте его TDrivers.
 * Подключаемый модуль ZIP-драйвера Elbereth версии 2.0.0 Бета-версия 1:
   * Обновлено до новой версии DUDI v6. Это означает, что начиная с данной версии подключаемый модуль
     требуется Dragon UnPACKer версии 5.7.0 или более поздней. Это не сработает со старым драконом
	 Версии для распаковки.
   * Изменено использование аббревиатуры вместо Info-Zip UnZip32.dll .
 * Подключаемый модуль основного драйвера Elbereth версии 3.0.1 Beta 4:
   * Обновлено до новой версии DUDI v6. Это означает, что начиная с данной версии подключаемый модуль
     требуется Dragon UnPACKer версии 5.7.0 или более поздней. Это не сработает со старым драконом
	 Версии для распаковки.
   + Добавлена поддержка игры Aliens vs. Predator (2010) .Формат файла ASR.
     Фактически поддерживается как несжатый, так и сжатый Asura-файл.
	 Почти все файлы в игре используют эти форматы (.EN/.GUI/и т.д.).
	 Если у вас активирован smart format (что вам и следует делать), он загрузит их
	 автоматически.
	 Пожалуйста, обратите внимание, что сжатые файлы Asura медленно загружаются и извлекаются из
них, но я ничего не могу сделать (формат не предусмотрен для произвольного
доступа для чтения).
   + Добавлена поддержка Starfighter из "Звездных войн" .Формат файла PAK.
     Запрос на публикацию #89 от Джеймса Крайенхагена.
   + Добавлена поддержка формата файла 7th Guest .GJD.
     (Это никогда не работало в drv_11th...)
   + Добавлена поддержка на 11 - й час.Формат файла GJD.
     (Активация не требуется)
   * Добавлены проверки работоспособности в Terminal Velocity .Формат POD.
 - Удален плагин Elbereth для драйвера 11-го часа.
   Больше не нужен, функции объединены в drv_default версии 3.0.1 бета-версии 3.
 * Duppi v3.4.0:
   я обновился, чтобы работать с Indy 9 вместо Curl.
     Это означает полную реализацию на Delphi без необходимости в библиотеках DLL.
	 Он также совместим с Lazarus (Indy 9 и 10 были портированы на Lazarus).
   Теперь я скомпилировал с помощью FastMM4, FastCode и FastMove.
 + Плагин преобразования по умолчанию версии 2.2.1:
   + Добавлены "Охотники за привидениями: видеоигра" .TEX в .DDS
     Основан на коде Ghostbusters texture converter C++ Джонатана Уилсона
	 Опубликовано в 2010 году.
   я благодарю Пола (от spookcentral.tk /) за идею и за тестирование.

Страница разработки бета-версии:
-----------------------

Эта страница позволяет вам следить за журналом разработки Dragon UnPACKer 5 между
Бета-версии. Вы также можете найти другую информацию и, возможно, некоторые загрузки.
     
http://www.elberethzone.net/en/dup-devlog.html

===============================================================================
