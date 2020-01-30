---
title: SELECT- und JOIN-Anweisungen von Systemsichten für erweiterte Ereignisse
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
ms.assetid: 04521d7f-588c-4259-abc2-1a2857eb05ec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a74026eb70c842d4f66706740e399763260f168
ms.sourcegitcommit: 2d82e4c1b94cec2089b20c084f2ac01240579c57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "6611513"
---
# <a name="selects-and-joins-from-system-views-for-extended-events-in-sql-server"></a><span data-ttu-id="6b29c-102">SELECT- und JOIN-Anweisungen von Systemsichten für erweiterte Ereignisse in SQL Server</span><span class="sxs-lookup"><span data-stu-id="6b29c-102">SELECTs and JOINs From System Views for Extended Events in SQL Server</span></span>


<span data-ttu-id="6b29c-103">Dieser Artikel beschreibt die beiden Arten von Systemsichten, die mit erweiterten Ereignissen in SQL Server und Azure SQL-Datenbank zusammenhängen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-103">This article explains the two sets of system views that relate to extended events in SQL Server and in Azure SQL Database.</span></span> <span data-ttu-id="6b29c-104">Dieser Artikel beschreibt:</span><span class="sxs-lookup"><span data-stu-id="6b29c-104">The article illustrates:</span></span>

- <span data-ttu-id="6b29c-105">wie mithilfe der JOIN-Anweisung verschiedene Systemsichten zusammengefügt werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-105">How to JOIN various system views.</span></span>
- <span data-ttu-id="6b29c-106">wie eine SELECT-Anweisung für bestimmte Informationen der Systemsichten durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="6b29c-106">How to SELECT particular kinds of information from the system views.</span></span>
- <span data-ttu-id="6b29c-107">wie die gleiche Ereignissitzungsinformation von verschiedenen technologischen Standpunkten aus dargestellt wird, was Ihr Verständnis von jeder Perspektive vertieft.</span><span class="sxs-lookup"><span data-stu-id="6b29c-107">How the same event session information is represented from various technological perspectives, which reinforces your understanding of each perspective.</span></span>


<span data-ttu-id="6b29c-108">Die meisten Beispiele werden für SQL Server geschrieben.</span><span class="sxs-lookup"><span data-stu-id="6b29c-108">Most of the examples are written for SQL Server.</span></span> <span data-ttu-id="6b29c-109">Mit kleineren Änderungen könnten sie auf der SQL-Datenbank ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-109">But with minor edits they would run on SQL Database.</span></span>



## <a name="a-foundational-information"></a><span data-ttu-id="6b29c-110">A.</span><span class="sxs-lookup"><span data-stu-id="6b29c-110">A.</span></span> <span data-ttu-id="6b29c-111">Grundlegende Informationen</span><span class="sxs-lookup"><span data-stu-id="6b29c-111">Foundational information</span></span>


<span data-ttu-id="6b29c-112">Es gibt zwei Sammlungen von Systemsichten für erweiterte Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="6b29c-112">There are two sets of system views for extended events:</span></span>


#### <a name="catalog-views"></a><span data-ttu-id="6b29c-113">Katalogsichten:</span><span class="sxs-lookup"><span data-stu-id="6b29c-113">Catalog views:</span></span>

- <span data-ttu-id="6b29c-114">Diese Sichten speichern Informationen über die *Definition* jeder Ereignissitzung, die durch [CREATE EVENT SESSION](../../t-sql/statements/create-event-session-transact-sql.md)oder durch eine Entsprechung der SSMS-Benutzeroberfläche erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="6b29c-114">These views store information about the *definition* of each event session that is created by [CREATE EVENT SESSION](../../t-sql/statements/create-event-session-transact-sql.md), or by an SSMS UI equivalent.</span></span> <span data-ttu-id="6b29c-115">Diese Sichten wissen jedoch nicht, ob eine Sitzung jemals ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-115">But these views know nothing about whether any sessions have ever started running.</span></span>
    - <span data-ttu-id="6b29c-116">Wenn z.B. der **Objekt-Explorer** von SSMS (SQL Server Management Studio) anzeigt, dass keine Ereignissitzungen definiert sind, würde das Ausführen einer SELECT-Anweisung in der Sicht *sys.server_event_session_targets* null (0) Zeilen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="6b29c-116">For example, if the SSMS **Object Explorer** shows no event sessions are defined, SELECTing from the view *sys.server_event_session_targets* would return zero rows.</span></span>


- <span data-ttu-id="6b29c-117">Das Namenspräfix ist:</span><span class="sxs-lookup"><span data-stu-id="6b29c-117">Name prefix is:</span></span>
    - <span data-ttu-id="6b29c-118">Das Namenspräfix auf SQL Server ist *sys.server\_event\_session\** .</span><span class="sxs-lookup"><span data-stu-id="6b29c-118">*sys.server\_event\_session\** is the name prefix on SQL Server.</span></span>
    - <span data-ttu-id="6b29c-119">Das Namenspräfix in der SQL-Datenbank ist *sys.database\_event\_session\** .</span><span class="sxs-lookup"><span data-stu-id="6b29c-119">*sys.database\_event\_session\** is the name prefix on SQL Database.</span></span>


#### <a name="dynamic-management-views-dmvs"></a><span data-ttu-id="6b29c-120">Dynamische Verwaltungssichten (Dynamic management views; DMVs):</span><span class="sxs-lookup"><span data-stu-id="6b29c-120">Dynamic management views (DMVs):</span></span>

- <span data-ttu-id="6b29c-121">Speichern Informationen über die *aktuelle Aktivität* beim Ausführen von Ereignissitzungen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-121">Store information about the *current activity* of running event sessions.</span></span> <span data-ttu-id="6b29c-122">Aber diese DMVs wissen nur wenig über die Definition der Sitzungen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-122">But these DMVs know little about the definition of the sessions.</span></span>
    - <span data-ttu-id="6b29c-123">Auch wenn derzeit alle Eventsitzungen beendet werden, würde aus der Ansicht *sys.dm_xe_packages* SELECT weiterhin Zeilen zurückgegeben, da verschiedene Pakete beim Serverstart in den aktiven Arbeitsspeicher geladen werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-123">Even if all event sessions are currently stopped, a SELECT from the view *sys.dm_xe_packages* would still return rows because various packages are loaded into active memory a server start.</span></span>
    - <span data-ttu-id="6b29c-124">Aus demselben Grund würde *sys.dm_xe_objects* *sys.dm_xe_object_columns* ebenfalls weiterhin Zeilen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="6b29c-124">For the same reason, *sys.dm_xe_objects* *sys.dm_xe_object_columns* would also still return rows.</span></span>


- <span data-ttu-id="6b29c-125">Namenspräfix für erweiterte Ereignisse DMVs ist:</span><span class="sxs-lookup"><span data-stu-id="6b29c-125">Name prefix for extended events DMVs is:</span></span>
    - <span data-ttu-id="6b29c-126">Das Namenspräfix auf SQL Server ist *sys.dm\_xe\_\** .</span><span class="sxs-lookup"><span data-stu-id="6b29c-126">*sys.dm\_xe\_\** is the name prefix on SQL Server.</span></span>
    - <span data-ttu-id="6b29c-127">Das Namenspräfix in der SQL-Datenbank ist in der Regel *sys.dm\_xe\_database\_\** .</span><span class="sxs-lookup"><span data-stu-id="6b29c-127">*sys.dm\_xe\_database\_\** is generally the name prefix on SQL Database.</span></span>


#### <a name="permissions"></a><span data-ttu-id="6b29c-128">Berechtigungen:</span><span class="sxs-lookup"><span data-stu-id="6b29c-128">Permissions:</span></span>


<span data-ttu-id="6b29c-129">Die folgende Berichtigung ist notwendig, um SELECT für Systemsichten ausführen zu können:</span><span class="sxs-lookup"><span data-stu-id="6b29c-129">To SELECT from the system views, the following permission is necessary:</span></span>

- <span data-ttu-id="6b29c-130">VIEW SERVER STATE – wenn es um Microsoft SQL Server handelt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-130">VIEW SERVER STATE - if on Microsoft SQL Server.</span></span>
- <span data-ttu-id="6b29c-131">VIEW DATABASE STATE – wenn es sich um eine Azure SQL-Datenbank handelt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-131">VIEW DATABASE STATE - if on Azure SQL Database.</span></span>


<a name="section_B_catalog_views"></a>

## <a name="b-catalog-views"></a><span data-ttu-id="6b29c-132">B.</span><span class="sxs-lookup"><span data-stu-id="6b29c-132">B.</span></span> <span data-ttu-id="6b29c-133">Katalogansichten</span><span class="sxs-lookup"><span data-stu-id="6b29c-133">Catalog views</span></span>


<span data-ttu-id="6b29c-134">Dieser Abschnitt stimmt mit drei verschiedenen technologischen Perspektiven auf der gleichen definierten Ereignissitzung überein und bezieht sich auf sie.</span><span class="sxs-lookup"><span data-stu-id="6b29c-134">This section matches and correlates three different technological perspectives on the same defined event session.</span></span> <span data-ttu-id="6b29c-135">Die Sitzung wurde definiert und kann im **Objekt-Explorer** von SQL Server Management Studio (SSMS.exe) angezeigt werden. Diese Sitzung wird derzeit jedoch nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-135">The session has been defined and is visible in the **Object Explorer** of SQL Server Management Studio (SSMS.exe), but the session is not currently running.</span></span>

<span data-ttu-id="6b29c-136">Es wird empfohlen, jeden Monat [das neueste Update von SSMS zu installieren](https://msdn.microsoft.com/library/mt238290.aspx), um unerwartete Fehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-136">Every month it is wise to [install the latest update of SSMS](https://msdn.microsoft.com/library/mt238290.aspx), to avoid unexpected failures.</span></span>


<span data-ttu-id="6b29c-137">Die Referenzdokumentation zu den Katalogsichten für erweiterte Ereignisse finden Sie unter [Katalogsichten für erweiterte Ereignisse (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6b29c-137">Reference documentation about the catalog views for extended events is at [Extended Events Catalog Views (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md).</span></span>


&nbsp;



#### <a name="the-sequence-in-this-section-b"></a><span data-ttu-id="6b29c-138">Die Reihenfolge in diesem Abschnitt B:</span><span class="sxs-lookup"><span data-stu-id="6b29c-138">The sequence in this section B:</span></span>


- [<span data-ttu-id="6b29c-139">B.1 Die Perspektive der SSMS-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="6b29c-139">B.1 SSMS UI perspective</span></span>](#section_B_1_SSMS_UI_perspective)
    - <span data-ttu-id="6b29c-140">Erstellen Sie mithilfe der SSMS-Benutzeroberfläche die Definition der Ereignissitzung.</span><span class="sxs-lookup"><span data-stu-id="6b29c-140">Create the definition of the event session, by using the SSMS UI.</span></span> <span data-ttu-id="6b29c-141">Screenshots zeigen eine Schritt-für-Schritt-Anleitung an.</span><span class="sxs-lookup"><span data-stu-id="6b29c-141">Step-by-step screenshots are shown.</span></span>


- [<span data-ttu-id="6b29c-142">B.2 Die Perspektive von Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b29c-142">B.2 Transact-SQL perspective</span></span>](#section_B_2_TSQL_perspective)
    - <span data-ttu-id="6b29c-143">Verwenden Sie das SSMS-Kontextmenü, um die definierte Ereignissitzung in die entsprechende Anweisung **CREATE EVENT SESSION** von Transact-SQL zurückzuentwickeln.</span><span class="sxs-lookup"><span data-stu-id="6b29c-143">Use the SSMS context menu to reverse engineer the defined event session into the equivalent Transact-SQL **CREATE EVENT SESSION** statement.</span></span> <span data-ttu-id="6b29c-144">T-SQL zeigt eine perfekte Übereinstimmung zu der Auswahl der SSMS-Screenshots.</span><span class="sxs-lookup"><span data-stu-id="6b29c-144">The T-SQL shows a perfect match to the SSMS screenshots choices.</span></span>


- [<span data-ttu-id="6b29c-145">B.3 Die Perspektive SELECT JOIN UNION der Katalogsicht</span><span class="sxs-lookup"><span data-stu-id="6b29c-145">B.3 Catalog view SELECT JOIN UNION perspective</span></span>](#section_B_3_Catalog_view_S_J_UNION)
    - <span data-ttu-id="6b29c-146">Geben Sie eine SELECT-Anweisung von T-SQL aus den Systemkatalogsichten für unsere Ereignissitzung aus.</span><span class="sxs-lookup"><span data-stu-id="6b29c-146">Issue a T-SQL SELECT statement from the system catalog views for our event session.</span></span> <span data-ttu-id="6b29c-147">Die Ergebnisse stimmen mit den Spezifikationen der **CREATE EVENT SESSION** -Abfrage überein.</span><span class="sxs-lookup"><span data-stu-id="6b29c-147">The results match the **CREATE EVENT SESSION** statement specifications.</span></span>


&nbsp;



<a name="section_B_1_SSMS_UI_perspective"></a>

### <a name="b1-ssms-ui-perspective"></a><span data-ttu-id="6b29c-148">B.1 Die Perspektive der SSMS-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="6b29c-148">B.1 SSMS UI perspective</span></span>


<span data-ttu-id="6b29c-149">Im **Objekt-Explorer**von SSMS können Sie das Dialogfeld **Neue Sitzung** ausführen, indem Sie **Management** > **Extended Events**erweitern und anschließend mit der rechten Maustaste auf **Sitzungen** > **Neue Sitzung**klicken.</span><span class="sxs-lookup"><span data-stu-id="6b29c-149">In SSMS, in its **Object Explorer**, you can start the **New Session** dialog by expanding **Management** > **Extended Events**, and then right-clicking **Sessions** > **New Session**.</span></span>

<span data-ttu-id="6b29c-150">Im großen Dialogfeld **New Session** (Neue Sitzung) wird im ersten Abschnitt namens **General**(Allgemein) angezeigt, dass die Option **Start the event session at server startup**(Ereignissitzung beim Serverstart starten) ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-150">In the large **New Session** dialog, in its first section labeled **General**, we see the option has been selected to **Start the event session at server startup**.</span></span>

<a name="section_B_2_TSQL_perspective"></a>

### <a name="b2-transact-sql-perspective"></a><span data-ttu-id="6b29c-151">Neue Sitzung > Allgemein, Ereignissitzung beim Serverstart starten.</span><span class="sxs-lookup"><span data-stu-id="6b29c-151">New Session > General, Start the event session at server startup.</span></span>


<span data-ttu-id="6b29c-152">Als nächstes sehen wir, dass im Abschnitt **Events** (Ereignisse), das Ereignis **lock_deadlock** ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-152">Next on the **Events** section, we see the **lock_deadlock** event was chosen.</span></span> <span data-ttu-id="6b29c-153">Drei **Actions** (Aktionen) wurden für dieses Ereignis ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-153">For that event, we see that three **Actions** have been selected.</span></span>

<span data-ttu-id="6b29c-154">Dies bedeutet, dass die Schaltfläche **Configure** (Konfigurieren) geklickt wurde, die nach dem Auswählen ausgegraut wird.</span><span class="sxs-lookup"><span data-stu-id="6b29c-154">This means the **Configure** button was clicked, which becomes gray after being clicked.</span></span>

<span data-ttu-id="6b29c-155">Neue Sitzung > Ereignisse, Globale Felder (Aktionen)</span><span class="sxs-lookup"><span data-stu-id="6b29c-155">New Session > Events, Global Fields (Actions)</span></span> <span data-ttu-id="6b29c-156">Wir sind immer noch im Abschnitt **Events** > **Configure** (Ereignisse > Konfigurieren) und sehen als nächstes, dass [**resource_type** auf **PAGE**](#resource_type_dmv_actual_row) festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-156">Next, still on the **Events** > **Configure** section, we see that [**resource_type** has been set to **PAGE**](#resource_type_dmv_actual_row).</span></span>


```sql
CREATE EVENT SESSION [event_session_test3]
    ON SERVER  -- Or, if on Azure SQL Database, ON DATABASE.

    ADD EVENT sqlserver.lock_deadlock
    (
        SET
            collect_database_name = (1)
        ACTION
        (
            package0  .collect_system_time,
            package0  .event_sequence,
            sqlserver .client_hostname
        )
        WHERE
        (
            [database_name]           = N'InMemTest2'
            AND [package0].[counter] <= (16)
            AND [resource_type]       = (6)
        )
    )

    ADD TARGET package0.event_file
    (
        SET
            filename           = N'C:\Junk\event_session_test3_EF.xel',
            max_file_size      = (20),
            max_rollover_files = (2)
    )

    WITH
    (
        MAX_MEMORY            = 4096 KB,
        EVENT_RETENTION_MODE  = ALLOW_SINGLE_EVENT_LOSS,
        MAX_DISPATCH_LATENCY  = 4 SECONDS,
        MAX_EVENT_SIZE        = 0 KB,
        MEMORY_PARTITION_MODE = NONE,
        TRACK_CAUSALITY       = OFF,
        STARTUP_STATE         = ON
    );
```


<span data-ttu-id="6b29c-157">Dies bedeutet, dass Ereignisdaten nicht von der Ereignis-Engine zum Ziel gesendet wird, wenn der Wert **resource_type** nicht **PAGE** ist.</span><span class="sxs-lookup"><span data-stu-id="6b29c-157">This means that event data will not be sent from the event engine to the target if the **resource_type** value is anything other than **PAGE**.</span></span>


<a name="section_B_3_Catalog_view_S_J_UNION"></a>

### <a name="b3-catalog-view-select-join-union-perspective"></a><span data-ttu-id="6b29c-158">Es werden zusätzliche Prädikatfilter für die Datenbank und für einen Leistungsindikator angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-158">We see additional predicate filters for the database name and for a counter.</span></span>


<span data-ttu-id="6b29c-159">Neue Sitzung > Ereignisse, Prädikatfelder filtern (Aktionen)</span><span class="sxs-lookup"><span data-stu-id="6b29c-159">New Session > Events, Filter Predicate Fields (Actions)</span></span> <span data-ttu-id="6b29c-160">Im Abschnitt **Data Storage** (Datenspeicher) sehen Sie, dass **event_file** als Ziel ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-160">Next on the **Data Storage** section, we see the **event_file** has been chosen as a target.</span></span> <span data-ttu-id="6b29c-161">Darüber hinaus sehen Sie, dass die Option **Enable file rollover** (Dateirollover aktivieren) ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-161">Further, we see that the **Enable file roleover** option has been selected.</span></span> <span data-ttu-id="6b29c-162">Neue Sitzung > Datenspeicher, eventfile_enablefileroleover</span><span class="sxs-lookup"><span data-stu-id="6b29c-162">New Session > Data Storage, eventfile_enablefileroleover</span></span>


```sql
SELECT
        s.name        AS [Session-Name],
        '1_EVENT'     AS [Clause-Type],
        'Event-Name'  AS [Parameter-Name],
        e.name        AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name         AS [Session-Name],
        '2_EVENT_SET'  AS [Clause-Type],
        f.name         AS [Parameter-Name],
        f.value        AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id

        JOIN  sys.server_event_session_fields   As f

            ON  f.event_session_id = s.event_session_id
            AND f.object_id        = e.event_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name              AS [Session-Name],
        '3_EVENT_ACTION'    AS [Clause-Type],

        a.package + '.' + a.name
                            AS [Parameter-Name],

        '(Not_Applicable)'  AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id

        JOIN  sys.server_event_session_actions  As a

            ON  a.event_session_id = s.event_session_id
            AND a.event_id         = e.event_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name                AS [Session-Name],
        '4_EVENT_PREDICATES'  AS [Clause-Type],
        e.predicate           AS [Parameter-Name],
        '(Not_Applicable)'    AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_events   AS e

            ON  e.event_session_id = s.event_session_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name              AS [Session-Name],
        '5_TARGET'          AS [Clause-Type],
        t.name              AS [Parameter-Name],
        '(Not_Applicable)'  AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_targets  AS t

            ON  t.event_session_id = s.event_session_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name          AS [Session-Name],
        '6_TARGET_SET'  AS [Clause-Type],
        f.name          AS [Parameter-Name],
        f.value         AS [Parameter-Value]
    FROM
              sys.server_event_sessions         AS s
        JOIN  sys.server_event_session_targets  AS t

            ON  t.event_session_id = s.event_session_id

        JOIN  sys.server_event_session_fields   As f

            ON  f.event_session_id = s.event_session_id
            AND f.object_id        = t.target_id
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name               AS [Session-Name],
        '7_WITH_MAX_MEMORY'  AS [Clause-Type],
        'max_memory'         AS [Parameter-Name],
        s.max_memory         AS [Parameter-Value]
    FROM
              sys.server_event_sessions  AS s
    WHERE
        s.name = 'event_session_test3'

UNION ALL
SELECT
        s.name                  AS [Session-Name],
        '7_WITH_STARTUP_STATE'  AS [Clause-Type],
        'startup_state'         AS [Parameter-Name],
        s.startup_state         AS [Parameter-Value]
    FROM
              sys.server_event_sessions  AS s
    WHERE
        s.name = 'event_session_test3'

ORDER BY
    [Session-Name],
    [Clause-Type],
    [Parameter-Name]
;
```


#### <a name="output"></a><span data-ttu-id="6b29c-163">Schließlich können Sie im Abschnitt **Advanced** (Erweitert) erkennen, dass der Wert **Maximum dispatch latency** (Maximale Verteilungslatenzzeit) auf 4 Sekunden reduziert wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-163">Finally, on the **Advanced** section, we see that the **Maximum dispatch latency** value was reduced down to 4 seconds.</span></span>


<span data-ttu-id="6b29c-164">Neue Sitzung > Erweitert, Maximale Verteilungslatenzzeit</span><span class="sxs-lookup"><span data-stu-id="6b29c-164">New Session > Advanced, Maximum dispatch latency</span></span> <span data-ttu-id="6b29c-165">Dadurch ist die Perspektive der SSMS-Benutzeroberfläche mit der Definition der Ereignissitzung abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-165">This completes the SSMS UI perspective on an event session definition.</span></span>


```
Session-Name          Clause-Type            Parameter-Name                  Parameter-Value
------------          -----------            --------------                  ---------------
event_session_test3   1_EVENT                Event-Name                      lock_deadlock
event_session_test3   2_EVENT_SET            collect_database_name           1
event_session_test3   3_EVENT_ACTION         sqlserver.client_hostname       (Not_Applicable)
event_session_test3   3_EVENT_ACTION         sqlserver.collect_system_time   (Not_Applicable)
event_session_test3   3_EVENT_ACTION         sqlserver.event_sequence        (Not_Applicable)
event_session_test3   4_EVENT_PREDICATES     ([sqlserver].[equal_i_sql_unicode_string]([database_name],N'InMemTest2') AND [package0].[counter]<=(16))   (Not_Applicable)
event_session_test3   5_TARGET               event_file                      (Not_Applicable)
event_session_test3   6_TARGET_SET           filename                        C:\Junk\event_session_test3_EF.xel
event_session_test3   6_TARGET_SET           max_file_size                   20
event_session_test3   6_TARGET_SET           max_rollover_files              2
event_session_test3   7_WITH_MAX_MEMORY      max_memory                      4096
event_session_test3   7_WITH_STARTUP_STATE   startup_state                   1
```


<span data-ttu-id="6b29c-166">B.2 Die Perspektive von Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b29c-166">B.2 Transact-SQL perspective</span></span>



<a name="section_C_DMVs"></a>

## <a name="c-dynamic-management-views-dmvs"></a><span data-ttu-id="6b29c-167">Unabhängig davon, wie eine Definition für die Ereignissitzung erstellt wurde, kann die Sitzung der SSMS-Benutzeroberfläche in perfekter Übereinstimmung mit dem Transact-SQL-Skript zurückentwickelt werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-167">Regardless of how an event session definition is created, from the SSMS UI the session can be reversed engineered into a perfectly matching Transact-SQL script.</span></span> <span data-ttu-id="6b29c-168">Sie können die vorhergehenden Screenshots von „New Session“ (Neue Sitzung) überprüfen und anschließend deren sichtbare Spezifikationen mit den Klauseln des folgenden generierten **CREATE EVENT SESSION** -Skript von T-SQL vergleichen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-168">You can examine the preceding New Session screenshots and compare their visible specifications to the clauses in the following generated T-SQL **CREATE EVENT SESSION** script.</span></span>


<span data-ttu-id="6b29c-169">Sie können mit der rechten Maustaste im **Objekt-Explorer** auf den Sitzungsknoten klicken und anschließend **Script Session as** > **CREATE to** > **Clipboard**(Skript für Sitzung als &gt; CREATE to &gt; Zwischenablage) auswählen, um eine Ereignissitzung zurückzuentwickeln.</span><span class="sxs-lookup"><span data-stu-id="6b29c-169">To reverse engineer an event session, in the **Object Explorer** you can right-click your session node, and then choose **Script Session as** > **CREATE to** > **Clipboard**.</span></span> <span data-ttu-id="6b29c-170">Das folgende T-SQL-Skript wurde durch Zurückentwickeln mit SSMS erstellt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-170">The following T-SQL script was created by reverse engineering with SSMS.</span></span> <span data-ttu-id="6b29c-171">Anschließend wurde das Skript manuell durch strategische Bearbeitung der Leerzeichen verschönert.</span><span class="sxs-lookup"><span data-stu-id="6b29c-171">Then the script was manually prettified by strategic manipulation of white space only.</span></span>


<span data-ttu-id="6b29c-172">Dadurch ist die T-SQL-Perspektive abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-172">This completes the T-SQL perspective.</span></span>


<span data-ttu-id="6b29c-173">B.3 Die Perspektive SELECT JOIN UNION der Katalogsicht</span><span class="sxs-lookup"><span data-stu-id="6b29c-173">B.3 Catalog view SELECT JOIN UNION perspective</span></span>

- <span data-ttu-id="6b29c-174">Machen Sie sich keine Sorgen!</span><span class="sxs-lookup"><span data-stu-id="6b29c-174">Do not be afraid!</span></span>
- <span data-ttu-id="6b29c-175">Die folgende SELECT-Anweisung von T-SQL ist nur so lang, da durch die UNION-Klausel mehrere kleine SELECT-Anweisungen vereinigt wurden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-175">The following T-SQL SELECT statement is long only because it UNIONs several small SELECTs together.</span></span>
- <span data-ttu-id="6b29c-176">Jede der kleinen SELECT-Anweisungen kann einzeln ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-176">Any of the small SELECTs can be run on its own.</span></span>
- <span data-ttu-id="6b29c-177">Die kleinen SELECT-Anweisungen zeigen an, wie die verschiedenen Katalogsichten des Systems durch JOIN verknüpft werden müssen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-177">The small SELECTs show how the various system cataloging views should be JOINed together.</span></span>
- <span data-ttu-id="6b29c-178">Output</span><span class="sxs-lookup"><span data-stu-id="6b29c-178">Output</span></span>
- <span data-ttu-id="6b29c-179">Als nächstes wird die tatsächliche Ausgabe nach dem Ausführen von SELECT JOIN UNION angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-179">Next is the actual output from running the preceding SELECT JOIN UNION.</span></span>
- <span data-ttu-id="6b29c-180">Der Ausgabeparameter benennt und bewertet die Zuordnung von dem, was schlicht in der vorherigen CREATE EVENT SESSION-Anweisung zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="6b29c-180">The output parameter names and values map to what is plainly visible in the preceding CREATE EVENT SESSION statement.</span></span>
- <span data-ttu-id="6b29c-181">Dadurch ist der Abschnitt über Katalogsichten abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-181">This completes the section on catalog views.</span></span>



<a name="section_C_1_list_packages"></a>

### <a name="c1-list-of-all-packages"></a><span data-ttu-id="6b29c-182">C.</span><span class="sxs-lookup"><span data-stu-id="6b29c-182">C.</span></span>


<span data-ttu-id="6b29c-183">Dynamische Verwaltungssichten (DMVs)</span><span class="sxs-lookup"><span data-stu-id="6b29c-183">Dynamic management views (DMVs)</span></span> <span data-ttu-id="6b29c-184">Wir wenden uns jetzt den DMVs zu.</span><span class="sxs-lookup"><span data-stu-id="6b29c-184">We now shift to DMVs.</span></span>


```sql
SELECT  --C.1
        p.name         AS [Package],
        p.description  AS [Package-Description]
    FROM
        sys.dm_xe_packages  AS p
    ORDER BY
        p.name;
```


#### <a name="output"></a><span data-ttu-id="6b29c-185">Dieser Abschnitt enthält mehrere Transact-SQL-SELECT-Anweisungen, die jeweils für bestimmte, nützliche Unternehmenszwecke gedacht sind.</span><span class="sxs-lookup"><span data-stu-id="6b29c-185">This section provides several Transact-SQL SELECT statements which each serve a specific useful business purpose.</span></span>

<span data-ttu-id="6b29c-186">Des Weiteren zeigt die SELECT-Anweisung, wie sie mit JOIN die DMVs für jede beliebige Verwendung verknüpfen können.</span><span class="sxs-lookup"><span data-stu-id="6b29c-186">Further, the SELECTs demonstrate how you can JOIN the DMVs together for any new uses you want.</span></span>


```
/***  (The unique p.guid values are not shown.)
Package        Package-Description
-------        -------------------
filestream     Extended events for SQL Server FILESTREAM and FileTable
package0       Default package. Contains all standard types, maps, compare operators, actions and targets
qds            Extended events for Query Store
SecAudit       Security Audit Events
sqlclr         Extended events for SQL CLR
sqlos          Extended events for SQL Operating System
SQLSatellite   Extended events for SQL Satellite
sqlserver      Extended events for Microsoft SQL Server
sqlserver      Extended events for Microsoft SQL Server
sqlserver      Extended events for Microsoft SQL Server
sqlsni         Extended events for Microsoft SQL Server
ucs            Extended events for Unified Communications Stack
XtpCompile     Extended events for the XTP Compile
XtpEngine      Extended events for the XTP Engine
XtpRuntime     Extended events for the XTP Runtime
***/
```


<span data-ttu-id="6b29c-187">Die Referenzdokumentation für die DMVs finden Sie unter [Dynamische Verwaltungssichten für erweiterte Ereignisse](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md).</span><span class="sxs-lookup"><span data-stu-id="6b29c-187">Reference documentation of the DMVs is available at [Extended Events Dynamic Management Views](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)</span></span>

- <span data-ttu-id="6b29c-188">Wenn nicht anders angegeben sind alle tatsächlichen Ausgabezeilen der folgenden SELECT-Anweisungen in diesem Artikel von SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="6b29c-188">In this article, any actual output rows from the following SELECTs are from SQL Server 2016, unless otherwise specified.</span></span>
- <span data-ttu-id="6b29c-189">Hier ist die Liste der SELECT-Anweisungen in dieser DMV aus dem Abschnitt C:</span><span class="sxs-lookup"><span data-stu-id="6b29c-189">Here is list of the SELECTs in this DMV section C:</span></span>
- [<span data-ttu-id="6b29c-190">C.1 Liste aller Pakete</span><span class="sxs-lookup"><span data-stu-id="6b29c-190">C.1 List of all packages</span></span>](#section_C_1_list_packages)
- [<span data-ttu-id="6b29c-191">C.2 Anzahl jedes Objekttyps</span><span class="sxs-lookup"><span data-stu-id="6b29c-191">C.2 Count of every object type</span></span>](#section_C_2_count_object_type)
- [<span data-ttu-id="6b29c-192">C.3 Auswählen aller verfügbaren Elemente nach Typ mit der SELECT-Anweisung</span><span class="sxs-lookup"><span data-stu-id="6b29c-192">C.3 SELECT all available items sorted by type</span></span>](#section_C_3_select_all_available_objects)


<a name="section_C_2_count_object_type"></a>

### <a name="c2-count-of-every-object-type"></a>[<span data-ttu-id="6b29c-193">C.4 Verfügbare Datenfelder für Ihr Ereignis</span><span class="sxs-lookup"><span data-stu-id="6b29c-193">C.4 Data fields available for your event</span></span>](#section_C_4_data_fields)


[<span data-ttu-id="6b29c-194">C.5 *sys.dm_xe_map_values* und Ereignisfelder</span><span class="sxs-lookup"><span data-stu-id="6b29c-194">C.5 *sys.dm_xe_map_values* and event fields</span></span>](#section_C_5_map_values_fields) [<span data-ttu-id="6b29c-195">C.6 Parameter für Ziele</span><span class="sxs-lookup"><span data-stu-id="6b29c-195">C.6 Parameters for targets</span></span>](#section_C_6_parameters_targets)


```sql
SELECT  --C.2
        Count(*)  AS [Count-of-Type],
        o.object_type
    FROM
        sys.dm_xe_objects  AS o
    GROUP BY
        o.object_type
    ORDER BY
        1  DESC;
```


#### <a name="output"></a>[<span data-ttu-id="6b29c-196">C.7 Typumwandlung der target_data-Spalte nach XML durch DMV SELECT</span><span class="sxs-lookup"><span data-stu-id="6b29c-196">C.7 DMV SELECT casting target_data column to XML</span></span>](#section_C_7_dmv_select_target_data_column)

[<span data-ttu-id="6b29c-197">C.8 Auswählen aus einer Funktion zum Abrufen von event_file-Daten vom Laufwerk durch SELECT</span><span class="sxs-lookup"><span data-stu-id="6b29c-197">C.8 SELECT from a function to retrieve event_file data from disk drive</span></span>](#section_C_8_select_function_disk) <span data-ttu-id="6b29c-198">C.1 Liste aller Pakete</span><span class="sxs-lookup"><span data-stu-id="6b29c-198">C.1 List of all packages</span></span>


```
/***  Actual output, sum is about 1915:

Count-of-Type   object_type
-------------   -----------
1303            event
351             map
84              message
77              pred_compare
53              action
46              pred_source
28              type
17              target
***/
```


<a name="section_C_3_select_all_available_objects"></a>

### <a name="c3-select-all-available-items-sorted-by-type"></a><span data-ttu-id="6b29c-199">Alle Objekte, die Sie im Bereich erweitere Ereignisse verwenden können, stammen von Paketen, die in Ihr System geladen werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-199">All the objects you can use in area of extended events come from packages which are loaded into the system.</span></span>


<span data-ttu-id="6b29c-200">In diesem Abschnitt werden alle Pakete und deren Beschreibungen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-200">This section lists all the packages and their descriptions.</span></span>



```sql
SELECT  --C.3
        o.object_type  AS [Type-of-Item],
        p.name         AS [Package],
        o.name         AS [Item],
        o.description  AS [Item-Description]
    FROM
             sys.dm_xe_objects  AS o
        JOIN sys.dm_xe_packages AS p  ON o.package_guid = p.guid
    WHERE
        o.object_type IN ('action' , 'target' , 'pred_source')
        AND
        (
            (o.capabilities & 1) = 0
            OR
            o.capabilities IS NULL
        )
    ORDER BY
        [Type-of-Item],
        [Package],
        [Item];
```


#### <a name="output"></a><span data-ttu-id="6b29c-201">Output</span><span class="sxs-lookup"><span data-stu-id="6b29c-201">Output</span></span>

<span data-ttu-id="6b29c-202">Hier ist die Liste der Pakete.</span><span class="sxs-lookup"><span data-stu-id="6b29c-202">Here is the list of packages.</span></span>


```
/***
Type-of-Item   Package        Item                          Item-Description
------------   -------        ----                          ----------------
action         package0       callstack                     Collect the current call stack
action         package0       debug_break                   Break the process in the default debugger
action         sqlos          task_time                     Collect current task execution time
action         sqlserver      sql_text                      Collect SQL text
event          qds            query_store_aprc_regression   Fired when Query Store detects regression in query plan performance
event          SQLSatellite   connection_accept             Occurs when a new connection is accepted. This event serves to log all connection attempts.
event          XtpCompile     cgen                          Occurs at start of C code generation.
map            qds            aprc_state                    Query Store Automatic Plan Regression Correction state
message        package0       histogram_event_required      A value is required for the parameter 'filtering_event_name' when source type is 0.
pred_compare   package0       equal_ansi_string             Equality operator between two ANSI string values
pred_compare   sqlserver      equal_i_sql_ansi_string       Equality operator between two SQL ANSI string values
pred_source    sqlos          task_execution_time           Get current task execution time
pred_source    sqlserver      client_app_name               Get the current client application name
target         package0       etw_classic_sync_target       Event Tracing for Windows (ETW) Synchronous Target
target         package0       event_counter                 Use the event_counter target to count the number of occurrences of each event in the event session.
target         package0       event_file                    Use the event_file target to save the event data to an XEL file, which can be archived and used for later analysis and review. You can merge multiple XEL files to view the combined data from separate event sessions.
target         package0       histogram                     Use the histogram target to aggregate event data based on a specific event data field or action associated with the event. The histogram allows you to analyze distribution of the event data over the period of the event session.
target         package0       pair_matching                 Pairing target
target         package0       ring_buffer                   Asynchronous ring buffer target.
type           package0       xml                           Well formed XML fragment
***/
```



<a name="section_C_4_data_fields"></a>

### <a name="c4-data-fields-available-for-your-event"></a><span data-ttu-id="6b29c-203">*Definitionen der vorhergehenden Abkürzungen:*</span><span class="sxs-lookup"><span data-stu-id="6b29c-203">*Definitions of the preceding initialisms:*</span></span>


<span data-ttu-id="6b29c-204">clr = Common Language Runtime von .NET</span><span class="sxs-lookup"><span data-stu-id="6b29c-204">clr = Common Language Runtime of .NET</span></span>

- <span data-ttu-id="6b29c-205">qds = Query Data Store (Abfragedatenspeicher)</span><span class="sxs-lookup"><span data-stu-id="6b29c-205">qds = Query Data Store</span></span>
- <span data-ttu-id="6b29c-206">sni = Server Network Interface (Server-Netzwerkschnittstelle)</span><span class="sxs-lookup"><span data-stu-id="6b29c-206">sni = Server Network Interface</span></span>


```sql
SELECT  -- C.4
        p.name         AS [Package],
        c.object_name  AS [Event],
        c.name         AS [Column-for-Predicate-Data],
        c.description  AS [Column-Description]
    FROM
              sys.dm_xe_object_columns  AS c
        JOIN  sys.dm_xe_objects         AS o

            ON  o.name = c.object_name

        JOIN  sys.dm_xe_packages        AS p

            ON  p.guid = o.package_guid
    WHERE
        c.column_type = 'data'
        AND
        o.object_type = 'event'
        AND
        o.name        = '\<EVENT-NAME-HERE!>'  --'lock_deadlock'
    ORDER BY
        [Package],
        [Event],
        [Column-for-Predicate-Data];
```


#### <a name="output"></a><span data-ttu-id="6b29c-207">ucs = Unified Communications Stack (Unified Communications-Stapel)</span><span class="sxs-lookup"><span data-stu-id="6b29c-207">ucs = Unified Communications Stack</span></span>

<span data-ttu-id="6b29c-208">xtp = Extreme Transaction Processing</span><span class="sxs-lookup"><span data-stu-id="6b29c-208">xtp = extreme transaction processing</span></span>

- <span data-ttu-id="6b29c-209">C.2 Anzahl jedes Objekttyps</span><span class="sxs-lookup"><span data-stu-id="6b29c-209">C.2 Count of every object type</span></span>
- <span data-ttu-id="6b29c-210">Dieser Abschnitt beschreibt die Objekttypen, die in Ereignispaketen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="6b29c-210">This section tells us about the type of objects that event packages contain.</span></span> <span data-ttu-id="6b29c-211">Eine vollständige Liste aller Objekttypen, die in *sys.dm\_xe\_objects* zusammen mit der Anzahl der Objekte für jeden Typ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-211">A complete list is displayed of all object types that are in *sys.dm\_xe\_objects*, along with the count for each type.</span></span>


```
/***
Actual output, except for the omitted Description column which is often NULL.
These rows are where object_type = 'lock_deadlock'.

Package     Event           Column-for-Predicate-Data
-------     -----           -------------------------
sqlserver   lock_deadlock   associated_object_id
sqlserver   lock_deadlock   database_id
sqlserver   lock_deadlock   database_name
sqlserver   lock_deadlock   deadlock_id
sqlserver   lock_deadlock   duration
sqlserver   lock_deadlock   lockspace_nest_id
sqlserver   lock_deadlock   lockspace_sub_id
sqlserver   lock_deadlock   lockspace_workspace_id
sqlserver   lock_deadlock   mode
sqlserver   lock_deadlock   object_id
sqlserver   lock_deadlock   owner_type
sqlserver   lock_deadlock   resource_0
sqlserver   lock_deadlock   resource_1
sqlserver   lock_deadlock   resource_2
sqlserver   lock_deadlock   resource_description
sqlserver   lock_deadlock   resource_type
sqlserver   lock_deadlock   transaction_id
***/
```



<a name="section_C_5_map_values_fields"></a>

### <a name="c5-sysdm_xe_map_values-and-event-fields"></a><span data-ttu-id="6b29c-212">Output</span><span class="sxs-lookup"><span data-stu-id="6b29c-212">Output</span></span>


<span data-ttu-id="6b29c-213">Hier ist die Anzahl der Objekte pro Objekttyp.</span><span class="sxs-lookup"><span data-stu-id="6b29c-213">Here is the count of objects per object type.</span></span>

<span data-ttu-id="6b29c-214">Es gibt ungefähr 1915 Objekte.</span><span class="sxs-lookup"><span data-stu-id="6b29c-214">There are about 1915 objects.</span></span> <span data-ttu-id="6b29c-215">C.3 Auswählen aller verfügbaren Elemente nach Typ mit der SELECT-Anweisung</span><span class="sxs-lookup"><span data-stu-id="6b29c-215">C.3 SELECT all available items sorted by type</span></span>

- <span data-ttu-id="6b29c-216">Die folgende SELECT-Anweisung gibt in etwa 1915 Zeilen zurück, eine für jedes Objekt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-216">The following SELECT returns about 1915 rows, one for each object.</span></span>
- <span data-ttu-id="6b29c-217">Output</span><span class="sxs-lookup"><span data-stu-id="6b29c-217">Output</span></span>


```sql
SELECT  --C.5
        dp.name         AS [Package],
        do.name         AS [Object],
        do.object_type  AS [Object-Type],
        'o--c'     AS [O--C],
        dc.name         AS [Column],
        dc.type_name    AS [Column-Type-Name],
        dc.column_type  AS [Column-Type],
        dc.column_value AS [Column-Value],
        'c--m'     AS [C--M],
        dm.map_value    AS [Map-Value],
        dm.map_key      AS [Map-Key]
    FROM
              sys.dm_xe_objects         AS do
        JOIN  sys.dm_xe_object_columns  AS dc

            ON  dc.object_name = do.name

        JOIN  sys.dm_xe_map_values      AS dm

            ON  dm.name = dc.type_name

        JOIN  sys.dm_xe_packages        AS dp

            ON  dp.guid = do.package_guid
    WHERE
        do.object_type = 'event'
        AND
        do.name        = '\<YOUR-EVENT-NAME-HERE!>'  --'lock_deadlock'
    ORDER BY
        [Package],
        [Object],
        [Column],
        [Map-Value];
```


#### <a name="output"></a><span data-ttu-id="6b29c-218">Als nächstes könnten für Sie das willkürliche Sampling der Objekte, die von der vorhergehenden SELECT-Anweisung zurückgegeben wurde, interessant sein.</span><span class="sxs-lookup"><span data-stu-id="6b29c-218">To whet your appetite, next is an arbitrary sampling of the objects returned by the preceding SELECT.</span></span>

<a name="resource_type_dmv_actual_row"></a>

<span data-ttu-id="6b29c-219">C.4 Verfügbare Datenfelder für Ihr Ereignis</span><span class="sxs-lookup"><span data-stu-id="6b29c-219">C.4 Data fields available for your event</span></span> <span data-ttu-id="6b29c-220">Die folgende SELECT-Anweisung gibt alle Datenfelder zurück, die speziell für Ihren Ereignistyp gelten.</span><span class="sxs-lookup"><span data-stu-id="6b29c-220">The following SELECT returns all the data fields that are particular to your event type.</span></span>


```
/***  5 sampled rows from the actual 153 rows returned.
    NOTE:  'resource_type' under 'Column'.

Package     Object          Object-Type   O--C   Column          Column-Type-Name     Column-Type   Column-Value   C--M   Map-Value        Map-Key
-------     ------          -----------   ----   ------          ----------------     -----------   ------------   ----   ---------        -------
sqlserver   lock_deadlock   event         o--c   CHANNEL         etw_channel          readonly      2              c--m   Operational      4
sqlserver   lock_deadlock   event         o--c   KEYWORD         keyword_map          readonly      16             c--m   access_methods   1024
sqlserver   lock_deadlock   event         o--c   mode            lock_mode            data          NULL           c--m   IX               8
sqlserver   lock_deadlock   event         o--c   owner_type      lock_owner_type      data          NULL           c--m   Cursor           2
sqlserver   lock_deadlock   event         o--c   resource_type   lock_resource_type   data          NULL           c--m   PAGE             6

Therefore, on your CREATE EVENT SESSION statement, in its ADD EVENT WHERE clause,
you could put:
    WHERE( ... resource_type = 6 ...)  -- Meaning:  6 = PAGE.
***/
```


<a name="section_C_6_parameters_targets"></a>

### <a name="c6-parameters-for-targets"></a><span data-ttu-id="6b29c-221">Beachten Sie das Klauselelement WHERE: *column_type = 'data'* .</span><span class="sxs-lookup"><span data-stu-id="6b29c-221">Note the WHERE clause item: *column_type = 'data'*.</span></span>


<span data-ttu-id="6b29c-222">Darüber hinaus müssen Sie den Wert der Klausel WHERE für *o.name =* bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="6b29c-222">Also, you would need to edit the WHERE clause value for *o.name =*.</span></span> <span data-ttu-id="6b29c-223">Output</span><span class="sxs-lookup"><span data-stu-id="6b29c-223">Output</span></span> <span data-ttu-id="6b29c-224">Die folgenden Zeilen wurden von der vorhergehenden SELECT-Anweisung zurückgegeben, wobei WHERE `o.name = 'lock_deadlock'`:</span><span class="sxs-lookup"><span data-stu-id="6b29c-224">The following rows were returned by the preceding SELECT, WHERE `o.name = 'lock_deadlock'`:</span></span>

- <span data-ttu-id="6b29c-225">Jede Zeile stellt einen optionalen Filter für das Ereignis *sqlserver.lock_deadlock* dar.</span><span class="sxs-lookup"><span data-stu-id="6b29c-225">Each row represents an optional filter for the *sqlserver.lock_deadlock* event.</span></span>
- <span data-ttu-id="6b29c-226">Die Spalte *\[Column-Description\]* (Spaltenbeschreibung) wird im folgenden Screenshot ausgelassen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-226">The *\[Column-Description\]* column is omitted from the following display.</span></span>


```sql
SELECT  --C.6
        p.name        AS [Package],
        o.name        AS [Target],
        c.name        AS [Parameter],
        c.type_name   AS [Parameter-Type],

        CASE c.capabilities_desc
            WHEN 'mandatory' THEN 'YES_Mandatory'
            ELSE 'Not_mandatory'
        END  AS [IsMandatoryYN],

        c.description AS [Parameter-Description]
    FROM
              sys.dm_xe_objects   AS o
        JOIN  sys.dm_xe_packages  AS p

            ON  o.package_guid = p.guid

        LEFT OUTER JOIN  sys.dm_xe_object_columns  AS c

            ON  o.name        = c.object_name
            AND c.column_type = 'customizable'  -- !
    WHERE
        o.object_type = 'target'
        AND
        o.name     LIKE '%'    -- Or '\<YOUR-TARGET-NAME-HERE!>'.
    ORDER BY
        [Package],
        [Target],
        [IsMandatoryYN]  DESC,
        [Parameter];
```


#### <a name="output"></a><span data-ttu-id="6b29c-227">Der Wert ist häufig NULL.</span><span class="sxs-lookup"><span data-stu-id="6b29c-227">Its value is often NULL.</span></span>

<span data-ttu-id="6b29c-228">C.5 *sys.dm_xe_map_values* und Ereignisfelder</span><span class="sxs-lookup"><span data-stu-id="6b29c-228">C.5 *sys.dm_xe_map_values* and event fields</span></span>


```
/***  Actual output, all rows, where target name = 'event_file'.
Package    Target       Parameter            Parameter-Type       IsMandatoryYN   Parameter-Description
-------    ------       ---------            --------------       -------------   ---------------------
package0   event_file   filename             unicode_string_ptr   YES_Mandatory   Specifies the location and file name of the log
package0   event_file   increment            uint64               Not_mandatory   Size in MB to grow the file
package0   event_file   lazy_create_blob     boolean              Not_mandatory   Create blob upon publishing of first event buffer, not before.
package0   event_file   max_file_size        uint64               Not_mandatory   Maximum file size in MB
package0   event_file   max_rollover_files   uint32               Not_mandatory   Maximum number of files to retain
package0   event_file   metadatafile         unicode_string_ptr   Not_mandatory   Not used
***/
```


<a name="section_C_7_dmv_select_target_data_column"></a>

### <a name="c7-dmv-select-casting-target_data-column-to-xml"></a><span data-ttu-id="6b29c-229">Die folgende SELECT-Anweisung erhält die JOIN-Klausel mit der schwierigen Sicht *sys.dm_xe_map_values*.</span><span class="sxs-lookup"><span data-stu-id="6b29c-229">The following SELECT includes a JOIN to the tricky view named *sys.dm_xe_map_values*.</span></span>


<span data-ttu-id="6b29c-230">Der Zweck der SELECT-Anweisung ist es, die zahlreichen Felder anzuzeigen, aus denen Sie für Ihre Ereignissitzung wählen können.</span><span class="sxs-lookup"><span data-stu-id="6b29c-230">The purpose of the SELECT display the numerous fields that you can choose from for your event session.</span></span> <span data-ttu-id="6b29c-231">Die Ereignisfelder können auf zwei Arten verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="6b29c-231">The event fields can be used in two ways:</span></span>

- <span data-ttu-id="6b29c-232">Zum Auswählen, welche Feldwerte in Ihr Ziel für jedes Ereignisvorkommen geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-232">To choose which field values will be written to your target for each event occurrence..</span></span>
- <span data-ttu-id="6b29c-233">Zum Filtern, welche Ereignisvorkommen zu Ihrem Ziel gesendet werden, bzw. davon abgehalten werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-233">To filter which event occurrences will be sent to versus kept from your target.</span></span>


```sql
SELECT  --C.7
        s.name,
        t.target_name,
        CAST(t.target_data AS XML)  AS [XML-Cast]
    FROM
              sys.dm_xe_session_targets  AS t
        JOIN  sys.dm_xe_sessions         AS s

            ON s.address = t.event_session_address
    WHERE
        s.name = '\<Your-Session-Name-Here!>';
```


#### <a name="output-the-only-row-including-its-xml-cell"></a><span data-ttu-id="6b29c-234">Output</span><span class="sxs-lookup"><span data-stu-id="6b29c-234">Output</span></span>

<span data-ttu-id="6b29c-235">Anschließend wird eine Stichprobe der tatsächlichen 153 Spalten der Ausgabe der vorhergehenden SELECT-Anweisung von T-SQL durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-235">Next is a sampling of the actual 153 rows of output from the preceding T-SQL SELECT.</span></span> <span data-ttu-id="6b29c-236">Die Zeile für **resource_type** ist [relevant](#resource_type_PAGE_cat_view) für das im Beispiel **event_session_test3** durchführte Prädikatfiltern, das an anderer Stelle in diesem Artikel vorgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="6b29c-236">The row for **resource_type** is [relevant](#resource_type_PAGE_cat_view) to the predicate filtering used in the **event_session_test3** example elsewhere in this article.</span></span> <span data-ttu-id="6b29c-237">C.6 Parameter für Ziele</span><span class="sxs-lookup"><span data-stu-id="6b29c-237">C.6 Parameters for targets</span></span>


<span data-ttu-id="6b29c-238">Die folgende SELECT-Anweisung gibt jeden Parameter für Ihr Ziel zurück.</span><span class="sxs-lookup"><span data-stu-id="6b29c-238">The following SELECT returns every parameter for your target.</span></span>

- <span data-ttu-id="6b29c-239">Jeder Parameter ist markiert, um anzuzeigen, ob er verbindlich ist, oder nicht.</span><span class="sxs-lookup"><span data-stu-id="6b29c-239">Each parameter is tagged to indicate whether it is mandatory.</span></span>
- <span data-ttu-id="6b29c-240">Die Werte, die Sie Parametern zuweisen, beeinflussen das Verhalten des Ziels.</span><span class="sxs-lookup"><span data-stu-id="6b29c-240">The values you assign to parameters affect the behavior of the target.</span></span>


```XML
name                              target_name   XML-Cast
----                              -----------   --------
checkpoint_session_ring_buffer2   ring_buffer   <RingBufferTarget truncated="0" processingTime="0" totalEventsProcessed="2" eventCount="2" droppedCount="0" memoryUsed="104"><event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:23.508Z"><data name="database_id"><type name="uint32" package="package0" /><value>5</value></data></event><event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:26.975Z"><data name="database_id"><type name="uint32" package="package0" /><value>5</value></data></event></RingBufferTarget>
```


#### <a name="output-xml-displayed-pretty-when-cell-is-clicked"></a><span data-ttu-id="6b29c-241">Beachten Sie das Klauselelement WHERE: *object_type = 'customizable'* .</span><span class="sxs-lookup"><span data-stu-id="6b29c-241">Note the WHERE clause item: *object_type = 'customizable'*.</span></span>


<span data-ttu-id="6b29c-242">Darüber hinaus müssen Sie den Wert der Klausel WHERE für *o.name =* bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="6b29c-242">Also, you would need to edit the WHERE clause value for *o.name =*.</span></span>


```xml
<RingBufferTarget truncated="0" processingTime="0" totalEventsProcessed="2" eventCount="2" droppedCount="0" memoryUsed="104">
  <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:23.508Z">
    <data name="database_id">
      <type name="uint32" package="package0" />
      <value>5</value>
    </data>
  </event>
  <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T01:28:26.975Z">
    <data name="database_id">
      <type name="uint32" package="package0" />
      <value>5</value>
    </data>
  </event>
</RingBufferTarget>
```


<a name="section_C_8_select_function_disk"></a>

### <a name="c8-select-from-a-function-to-retrieve-event_file-data-from-disk-drive"></a><span data-ttu-id="6b29c-243">Output</span><span class="sxs-lookup"><span data-stu-id="6b29c-243">Output</span></span>


<span data-ttu-id="6b29c-244">Die folgenden Zeilen der Parameter sind eine Teilmenge von denen, die in SQL Server 2016 von der vorhergehenden SELECT-Anweisung zurückgegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-244">The following rows of parameters are a subset of those returned by the preceding SELECT, in SQL Server 2016.</span></span> <span data-ttu-id="6b29c-245">C.7 Typumwandlung der target_data-Spalte nach XML durch DMV SELECT</span><span class="sxs-lookup"><span data-stu-id="6b29c-245">C.7 DMV SELECT casting target_data column to XML</span></span>

- <span data-ttu-id="6b29c-246">Diese DMV SELECT-Anweisung gibt Datenzeilen des Ziels Ihrer aktiven Ereignissitzung zurück.</span><span class="sxs-lookup"><span data-stu-id="6b29c-246">This DMV SELECT returns data rows from the target of your active event session.</span></span>
    - <span data-ttu-id="6b29c-247">Die Daten werden in XML umgewandelt. Dadurch kann die zurückgegebene Zelle zum einfachen Anzeigen in SSMS geklickt werden.</span><span class="sxs-lookup"><span data-stu-id="6b29c-247">The data is cast to XML, which makes its returned cell clickable for easy display in SSMS.</span></span> <span data-ttu-id="6b29c-248">Wenn die Ereignissitzung beendet wird, gibt SELECT null Zeilen zurück.</span><span class="sxs-lookup"><span data-stu-id="6b29c-248">If your event session is stopped, this SELECT will return zero rows.</span></span>


```sql
SELECT  --C.8
        f.module_guid,
        f.package_guid,
        f.object_name,
        f.file_name,
        f.file_offset,
        CAST(f.event_data AS XML)  AS [Event-Data-As-XML]
    FROM
        sys.fn_xe_file_target_read_file(

            '\<YOUR-PATH-FILE-NAME-ROOT-HERE!>*.xel',
            --'C:\Junk\Checkpoint_Begins_ES*.xel',  -- Example.

            NULL, NULL, NULL
        )  AS f;
```


#### <a name="output-rows-returned-by-select-from-the-function"></a><span data-ttu-id="6b29c-249">Sie müssen den Wert der WHERE-Klausel für *s.name =* bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="6b29c-249">You would need to edit the WHERE clause value for *s.name =*.</span></span>


<span data-ttu-id="6b29c-250">Ausgabe der einzelnen Zeile einschließlich der XML-Zelle</span><span class="sxs-lookup"><span data-stu-id="6b29c-250">Output, the only row, including its XML cell</span></span> <span data-ttu-id="6b29c-251">Hier ist die einzige Zeile, die von der vorhergehenden SELECT-Anweisung ausgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="6b29c-251">Here is the only row that is output from the preceding SELECT.</span></span>


```
module_guid                            package_guid                           object_name        file_name                                                           file_offset   Event-Data-As-XML
-----------                            ------------                           -----------        ---------                                                           -----------   -----------------
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_begin   C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5120          <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T03:30:14.023Z"><data name="database_id"><value>5</value></data><action name="session_id" package="sqlserver"><value>60</value></action><action name="database_id" package="sqlserver"><value>5</value></action></event>
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_end     C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5120          <event name="checkpoint_end" package="sqlserver" timestamp="2016-07-09T03:30:14.025Z"><data name="database_id"><value>5</value></data></event>
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_begin   C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5632          <event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T03:30:17.704Z"><data name="database_id"><value>5</value></data><action name="session_id" package="sqlserver"><value>60</value></action><action name="database_id" package="sqlserver"><value>5</value></action></event>
D5149520-6282-11DE-8A39-0800200C9A66   03FDA7D0-91BA-45F8-9875-8B6DD0B8E9F2   checkpoint_end     C:\Junk\Checkpoint_Begins_ES_20160615bb-_0_131125086091700000.xel   5632          <event name="checkpoint_end" package="sqlserver" timestamp="2016-07-09T03:30:17.709Z"><data name="database_id"><value>5</value></data></event>
```


#### <a name="output-one-xml-cell"></a><span data-ttu-id="6b29c-252">Die Spalte *XML-Cast* (XML-Umwandlung) enthält eine XML-Zeichenfolge, die von SSMS auch als XML verstanden wird.</span><span class="sxs-lookup"><span data-stu-id="6b29c-252">The column *XML-Cast* contains a string of XML that SSMS understands is XML.</span></span>


<span data-ttu-id="6b29c-253">Daher erkennt SSMS, dass die Zelle der XML-Umwandlung klickbar gemacht werden sollte.</span><span class="sxs-lookup"><span data-stu-id="6b29c-253">Therefore SSMS understands it should make the XML-Cast cell clickable.</span></span>


```xml
<event name="checkpoint_begin" package="sqlserver" timestamp="2016-07-09T03:30:14.023Z">
  <data name="database_id">
    <value>5</value>
  </data>
  <action name="session_id" package="sqlserver">
    <value>60</value>
  </action>
  <action name="database_id" package="sqlserver">
    <value>5</value>
  </action>
</event>
```

