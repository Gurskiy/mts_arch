# Модель предметной области
<!-- Логическая модель, содержащая бизнес-сущности предметной области, атрибуты и связи между ними. 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375782602

Используется диаграмма классов UML. Документация: https://plantuml.com/class-diagram 
-->

```plantuml
@startuml

namespace Users{
    class User
    {
        id : string
        login : string
        fullName : string
        role : Role
        createdAt : datetime
        updatedAt : datetime
    }

    enum RoleType
    {
        speaker
        viewer
        reviewer
        manager
        support
    }
    User -- RoleType
}

namespace Conference {


    class Conference
    {
        id : string
        name : string
        dateStart : datetime
        dateFinish : datetime
    }

    class ConferenceMember
    {
        confId : string
        userId : string
    }


    class ConferenceSchedule
    {
        confId : string
        time : time
        reportId : string
    }


    class ConferenceFeedback
    {
        id : string
        confId : string
        userId : string
        questionId : string
        score : integer
    }


    Conference *-- "1" ConferenceSchedule
    ConferenceMember "*"--"*" Conference
    Conference *-- "*" ConferenceFeedback

}

namespace Reports {
    class Report
    {
        id : string
        userId : string
        name : string
        content : string
        conferenceId : string
    }

    class ReportReview
    {
        reportId : string
        reviewerId : string
        status : ReportStatus
    }

    enum ReportStatus
    {
        pending
        reviewing
        reopened
        accepted
        rejected
    }

    ReportReview -- ReportStatus
    Report *--"1" ReportReview
}

Conference.ConferenceMember "*"--"*" Users.User
Conference.ConferenceFeedback "*"--"*" Users.User
Reports.Report "*"--"*" Users.User
Reports.ReportReview "*"--"*" Users.User
Reports.Report "*"--* Conference.ConferenceSchedule

@enduml
```
