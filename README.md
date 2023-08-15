## <a name="versions"></a>**System Architecture**
## <a name="versions"></a>*Table of content*
1. Introduction
2. Types of users
3. Users limits
4. User state
5. User transitions
6. User Transitions Diagram
7. Conclusion
### <a name="versions"></a>*1. Introduction*
This documents discribes the architrcture of a system designed of provide a set of services for partner users. Each partner has a distinct set of functional oportunites and right, and users belonging to differents partners have non-overlapping memberships. The system handles various user type each with different capabilities and session limits.
### <a name="versions"></a>*2. Types of users*
The system are four types of  users\
-guest\
-basic\
-company\
-advanced\
Each partner organization can define its own set of functionalities and rights for each user type.
### <a name="versions"></a>*3. Users limits*
The system employs session management to track user activity and set certain limits based on user types:\
**-guest**
> Guest users have sessions limited to 20 minutes.
Guest users can perform up to 5 operations per day and 20 operations per week. After reaching this limit, they transition to an "idle" state.

**-basic**
> Basic users have increased limits of 20 operations per day and 50 operations per week.

**-company**
>Company users have no such restrictions.

**-advanced**
>Advanced users have no such restrictions.

### <a name="versions"></a>*4. User state*
User state determines the possible statuses a user account can be in. States,  include:\
-idle\
-active\
-inactive
### <a name="versions"></a>*5. User transitions*
User transitions are based on user actions, verification processes (e.g., KYC), and partner-defined rules. Users can transition between user types based on specific criteria:
```plantuml
Guest --> Basic --> Advanced

Advanced --> Basic --> Guest

Company --> Advanced

Advanced ---> Company
```
### <a name="versions"></a>*6. User Transitions Diagram*
```plantuml
Guest --> Basic : KYC Completed
Basic --> Advanced : User Progression
Advanced --> Basic : User Demotion
Advanced --> Company : Company Status
Company --> Advanced : Company Promotion
Basic --> Guest : Limits Exceeded
Advanced --> Guest : User Demotion
```

### <a name="versions"></a>*7. Conclusion*
The system architecture described above provides a flexible and scalable solution for managing partner-specific services and user types. This document serves as a guide to understand the system's internal workings and can be used for further development and maintenance.
