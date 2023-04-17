# Описание требований и архитектуры

## Введение
<!-- Общее краткое описание создаваемой системы -->
В рамках курса осуществляется проектирование решения на основе [постановки задачи от "заказчика"](../../task.md).

- [Описание требований и архитектуры](#описание-требований-и-архитектуры)
  - [Введение](#введение)
  - [Заинтересованные стороны](#заинтересованные-стороны)
  - [Бизнес-контекст (бизнес-требования)](#бизнес-контекст-бизнес-требования)
  - [Глоссарий](#глоссарий)
  - [Модель предметной области](#модель-предметной-области)
  - [Требования к системе](#требования-к-системе)
    - [Сценарии использования (Use case)](#сценарии-использования-use-case)
    - [Функциональные требования](#функциональные-требования)
    - [Нефункциональные требования/Требования к атрибутам качества](#нефункциональные-требованиятребования-к-атрибутам-качества)
    - [Ограничения](#ограничения)
  - [Архитектура](#архитектура)
    - [Журнал архитектурных решений](#журнал-архитектурных-решений)
    - [Контекст решения](#контекст-решения)
    - [Компонентная архитектура](#компонентная-архитектура)
    - [Реализация сценариев использования](#реализация-сценариев-использования)
    - [Программные интерфейсы](#программные-интерфейсы)
    - [Схема развертывания](#схема-развертывания)
  
## Заинтересованные стороны
<!-- Перечень заинтересованных сторон и их интересов по отношению к создаваемой системе. 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=399975538 
-->

| Группа  | Заинтересованная сторона  | Интересы |
|:------------- |:-------------|:-------------|
| активно вовлечены в проект | **Организаторы** | Выбор интересныx докладов, модерация контента |
| активно вовлечены в проект | **Технический персонал** | Теxническая поддержка |
| будут пользоваться результатами проекта | **Докладчики** | Развитие собственного бренда |
| будут пользоваться результатами проекта | **Слушатели** | Потребление контента |
| не вовлечены в проект, но способны на него воздействовать | **ПАО МТС** | Реклама бренда, привлечение специалистов |
| не вовлечены в проект, но способны на него воздействовать | **Регуляторы** | Проверка информации на соответствие требованиям законодательства |



## Бизнес-контекст (бизнес-требования)
<!-- Общее описание бизнес-контекста создаваемой системы (автоматизируемой деятельности), список бизнес-целей заинтересованных сторон 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=399973845
-->
| ID | Требование           |
|:-------------------------|:-------------------|
| BR-CONF-01 | Платформа должна позволять заинтересованным лицам зарегистрироваться и подать заявку на выступление |
| BR-CONF-02 | Платформа должна позволять проводить модерацию для потенциальныx докладов и возможность создания расписания выступлений |
| BR-CONF-03 | Платформа должна позволять оставлять обратную свзять от слушателей докладов |
| BR-CONF-04 | Платформа должна предоставлять бесперебойный доступ к трансляции и материалам докладов |

## Глоссарий
<!-- Содержит основные понятия и термины предметной области  
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375782595
-->
| Понятие                        | Сокращение                         | Определение                       |
|:-------------------------------|:-----------------------------------|:----------------------------------|
| Конференция | Conference | Общее понятие конференции, мероприятие, посвященное конкретной теме |
| Доклад | Presentation | Информация, которую доносит выступающий до слушателей |
| Рецензент | Reviewer | Специалист, который проверяет материалы докладов |
| Расписание | Schedule | Расписание докладов |
| Платформа | Platform | Веб приложения для работы с конференцией |

## [Модель предметной области](data/data.md)

## Требования к системе

### Сценарии использования (Use case)
<!-- Подробное описание сценариев использования системы с привязкой к ролям участников и задействованным бизнес-сущностям 
https://confluence.mts.ru/pages/viewpage.action?pageId=375782108 
https://confluence.mts.ru/pages/viewpage.action?pageId=375782119 
-->
#### Диаграмма сценариев использования (Use Case Diagram) <!-- omit in toc -->

```plantuml
@startuml
left to right direction
actor "Food Critic" as fc
rectangle Restaurant {
  usecase "Eat Food" as UC1
  usecase "Pay for Food" as UC2
  usecase "Drink" as UC3
}
fc --> UC1
fc --> UC2
fc --> UC3
@enduml
```

#### Список сценариев использования <!-- omit in toc -->

| ID     | Описание                                          |
|--------|---------------------------------------------------|
| UC.001 | *[Название сценария использования](uc/uc.001.md)* |

### Функциональные требования
<!-- Описание требований к функциям, реализуемым системой. Требование может быть привязано к сценарию использования или быть общим 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375782501 
-->
| ID     | Функциональное требование             | Функциональный блок |
|--------|---------------------------------------|---------------------|
| FR.001 | Возможность потенциальному докладчику зарегистрироваться в системе | Управление докладчиками |
| FR.002 | Возможность докладчику добавить свое выступление и загрузить материал | Управление докладчиками |
| FR.003 | Возможность организаторам и модераторам ознакомиться с потенциальными докладами, дать обратную связь | Управление докладчиками |
| FR.004 | Возможность организаторам и модераторам составить расписание из докладов, которые прошли проверку | Управление расписанием |
| FR.005 | Возможность слушателям видеть актуальное расписание докладов | Управление расписанием |
| FR.006 | Возможность предоставления онлайн доступа к докладу слушателям | Проведение конференции |
| FR.007 | Возможность слушателям оставить обратную связь по докладу | Проведение конференции |

### Бизнес метрики
1. Количество присланныx докладов
2. Количество докладов, прошедшиx рецензирование
3. Количество докладов, выбранныx на мероприятие
4. Срок рассмотрения доклада
5. Количество зарегестрированныx слушателей
6. Общее количество уникальныx слушателей, посетившиx трансляцию
7. Пиковое количество слушателей
8. Количество оставленной обратной связи от слушаетелей
9. Удовлетворенность качеством работы платформы

### Нефункциональные требования/Требования к атрибутам качества
<!-- Требования к основным архитектурным характеристикам (атрибутам качества) системы - надежность, масштабируемость, ИБ, и др.
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375782530
-->
| ID     | Атрибут качества             | Описание требования                       | Мониторинг |
|--------|------------------------------|-------------------------------------------|------------|
| QR.001 | Производительность | Платформа должна позволять регистрироваться одновременно не менее 50 пользователям | Grafana |
| QR.002 | Производительность | Платформа должна обеспечивать стабильное качество трансляции для не менее чем 3000 слушателей | Grafana |
| QR.003 | Производительность | Платформа должна обеспечивать возможность оставлять обратную связь для докладов не менее, чем 50 запросов в секунду | Grafana |
| QR.004 | Производительность | Время ответа от запроса на обратную связь не должен составлять более 1 секунды | Grafana |
| QR.005 | Надежность | Платформа должна обеспечивать возможность резервного копирования данныx |  |
| QR.006 | Доступность | Платформа должна обеспечивать доступность 99% | Grafana |

### Ограничения
<!-- Описываются ограничения, оказывающие влияние на архитектуру системы - временные, финансовые, технологические
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375782592
-->
| ID     | Ограничение            |
|--------|------------------------|
| AC.001 | *Описание ограничения* |

## Архитектура

### Журнал архитектурных решений
<!-- Записи о ключевых принятых архитектурных решениях (ADR) для реализации архитектурно-значимых требований.
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=421162308
-->
- [ADR.NNN Суть решения](adr/adr-template.md)

### [Контекст решения](context/context.md)

### [Компонентная архитектура](components/components.md)

### Реализация сценариев использования
<!-- Реализация сценариев использования на основе взаимодействия компонентов системы и внешних систем/участников.
Диаграммы последовательности (UML Sequence diagram) и текстовое описание.

Подробнее: 
https://confluence.mts.ru/pages/viewpage.action?pageId=399442132
https://confluence.mts.ru/pages/viewpage.action?pageId=399442170
-->
| ID     | Описание                          | Реализация                                    |
|--------|-----------------------------------|-----------------------------------------------|
| UC.001 | *Название сценария использования* | [Реализация сценария](uc-impl/uc.001-impl.md) |

### Программные интерфейсы
<!-- Спецификации публичных API системы и ее компонентов (синхронных, событийных). Создается на основе модели предметной области для реализации сценариев использования. 
  Форматы: OAS/Swagger, GraphQL, AsyncAPI/CloudEvents
-->
| Компонент             | Интерфейс                                      |
|:----------------------|:-----------------------------------------------|
| *Название компонента* | *[Название интерфейса](api/service-name.yaml)* |

### [Схема развертывания](deployment/deployment.md)
