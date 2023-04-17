@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

LAYOUT_WITH_LEGEND()

Person(listner, "Слушатель", "Пользователь, заинтересованный прослушать доклады")
Person(speaker, "Докладчик", "Пользователь, заинтересованный выступить на конференции")
Person(manager, "Организатор", "Пользователь, заинтересованный в качестве контента на конференции")

System(spa, "SPA", "WEB интерфейс системы")
System(api, "API", "Сервис, предоставляющий REST API для платформы")

System_Ext(youtube, "Youtube", "Стриминг выступлений")

Rel(listner, spa, "Регистрация, просмотр расписания, просмотр выступлений, обратная связь")
Rel(speaker, spa, "Регистрация, подача заявки на доклад, получение обратной связи")
Rel(manager, spa, "Регистрация, модерация докладов, формирование расписания")

Rel(spa, api, "Api запросы", "REST API")
Rel(api, youtube, "Стриминг выступлений", "https")


@enduml
