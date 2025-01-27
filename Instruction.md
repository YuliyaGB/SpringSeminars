# Основы работы с GitHub.

## Основы работы с удаленным репозиторием.

Для начала работы с центральным репозиторием, следует создать копию оригинального проекта со всей его историей локально.

Клонирует репозиторий, используя протокол http:

* git clone http://user@somehost:port/~user/repository/project.git

Для синхронизации текущей ветки с репозиторием используются команды git fetch и git pull.

git fetch — забирает изменения удаленной ветки из репозитория по умолчания, основной ветки; той, которая была использована при клонировании репозитория. Изменения обновят удаленную ветку (remote tracking branch), после чего надо будет провести слияние с локальной ветку командой git merge.

Команда git pull сразу забирает изменения и проводит слияние с активной веткой. 

Забирает из репозитория, для которого были созданы удаленные ветки по умолчанию:

* git pull

Забирает изменения и метки из определенного репозитория:

* git pull username-project --tags

После проведения работы в экспериментальной ветке, слияния с основной, необходимо обновить удаленный репозиторий (удаленную ветку). Для этого используется команда git push.

Отправляет свои изменения в удаленную ветку, созданную при клонировании по умолчанию:

* git push

Отправляет изменения из ветки master в ветку experimental удаленного репозитория:

* git push ssh://yourserver.com/~you/proj.git master:experimental

## Работа с локальным репозиторием.

*Базовые команды*

* git init — создание репозитория

Команда git init создает в директории пустой репозиторий в виде директории .git, где и будет в дальнейшем храниться вся информация об истории коммитов, тегах — о ходе разработки проекта:

* git add и git rm — индексация изменений

Следующее, что нужно знать — команда git add. Она позволяет внести в индекс — временное хранилище — изменения, которые затем войдут в коммит.

Индексирует измененный файл, либо оповещение о создании нового:

* git add EDITEDFILE

Вносит в индекс все изменения, включая новые файлы:

* git add .

Из индекса и дерева проекта одновременно файл можно удалить командой:

* git rm.

Удаляет из индекса и дерева проекта отдельные файлы:

* git rm FILE1 FILE2

Хороший пример удаления из документации к git, удаляются сразу все файлы txt из папки:

* git rm Documentation/\*.txt

Вносит в индекс все удаленные файлы:

* git rm -r --cached .

Сбросить весь индекс или удалить из него изменения определенного файла можно командой git reset:

* git reset

Удаляет из индекса конкретный файл:

* git reset — EDITEDFILE

Команда git reset используется не только для сбрасывания индекса, поэтому дальше ей будет уделено гораздо больше внимания.

* git status — состояние проекта, измененные и не добавленные файлы, индексированные файлы.

Команду git status, пожалуй, можно считать самой часто используемой наряду с командами коммита и индексации. Она выводит информацию обо всех изменениях, внесенных в дерево директорий проекта по сравнению с последним коммитом рабочей ветки; отдельно выводятся внесенные в индекс и неиндексированные файлы. Использовать ее крайне просто:

* git status

Кроме того, git status указывает на файлы с неразрешенными конфликтами слияния и файлы, игнорируемые git.

* git commit — совершение коммита

Коммит — базовое понятие во всех системах контроля версий, поэтому совершаться он должен легко и по возможности быстро. В простейшем случае достаточно после индексации набрать:

* git commit

Если индекс не пустой, то на его основе будет совершен коммит, после чего пользователя попросят прокомментировать вносимые изменения вызовом команды edit. Сохраняемся, и вуаля! Коммит готов. Есть несколько ключей, упрощающих работу с git commit.

Совершает коммит, автоматически индексируя изменения в файлах проекта. Новые файлы при этом индексироваться не будут! Удаление же файлов будет учтено:

* git commit -a

Комментирует коммит прямо из командной строки вместо текстового редактора:

* git commit -m «commit comment»
