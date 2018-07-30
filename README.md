# Подготовка
* Если нет JDK, то установите его для своей платформы http://www.oracle.com/technetwork/java/javase/downloads/index.html
* Скачайте проект https://github.com/zloyksardas/obligation-cordapp ( ` https://github.com/zloyksardas/obligation-cordapp ` )

# Запуск приложения

## Генерация нод
* Откройте терминал и перейдите в директорию `obligation-cordapp` 
* Постройте ноды, иcпользуя команду:
    * Unix/Mac OSX: `./gradlew deployNodes`
    * Windows: `gradlew.bat deployNodes`
## Конфигурация нод
* Откройте директорию `obligation-cordapp/kotlin-source/build/nodes/`. Там вы увидите папки `Notary`, `PartyA`, `PartyB`, `PartyC` \- это папки с нодами.
* Перейдите, например, в папку `Notary` и откройте файл  `node.conf`. Здесь нужно изменить значение поля `p2pAdress` на адрес компьютера в локальной сети, с которого будет запускаться нода.
* Предыдущий пункт нужно проделать с каждой нодой, заменяя адрес на тот, с которого будет запускаться нода.
* Загрузите network-bootstrapper http://downloads.corda.net/network-bootstrapper-corda-3.0.jar и поместите его в директорию `obligation-cordapp/kotlin-source/build/nodes/`.
* Запустите network-bootstrapper с помощью терминала командой `java -jar network-bootstrapper-corda-3.0.jar ./`

## Перенос нод на другие компьютеры
* Перенесите папку каждой ноды на машины с соответствующими адресами, которые вы указали ранее.
* Так же на каждый компьютер нужно перенести файлы `runnodes`, `runnodes.bat`, `runnodes.jar`. Они должны лежать в одной директории с папкой ноды.
* Удалите перенесенные папки нод с первого компьютера.

## Запуск нод
* Откройте терминал и перейдите в папку `obligation-cordapp/kotlin-source/build/nodes/` на начальном компьютере (на котором лежит Notary нода) и запустите скрипт командой `./runnodes`. Подождите некоторое время пока скрипт отработает. Для каждой ноды появится свое окно терминала.
* На остальных компьютерах откройте терминал и  перейдите в директорию, где лежат файлы `runnodes`, `runnodes.bat`, `runnodes.jar` и папка ноды. Запустите скрипт командой `./runnodes`. Подождите некоторое время пока скрипт отработает. Для каждой ноды появится свое окно терминала.

# Взаимодействие с нодами
* Откройте браузер и передите по адресу **своей ноды**, который вы указали ранее (например `localhost:10013`).

## Элементы управления
* С помощью кнопки **Issue cash** вы можете добавить себе денег для последующего взаимодействия (в поле **Currency** указываем **USD**)
* С помощью кнопки **Create Obligation** создается факт закдолженности, который сразу отобразиться в поле **Recorded Obligations** как у заемщика, так и у должника.
* Напротив каждой облигации есть кнопка **Settle**, которая позволяет должнику погасить долг частично или полностью.
* Кнопка **Transfer** работает некорректно и нажимать ее не стоит.

