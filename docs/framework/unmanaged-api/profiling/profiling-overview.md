---
title: Übersicht über die Profilerstellung
ms.date: 03/30/2017
helpviewer_keywords:
- managed code, profiling API support
- unmanaged code, combining with managed code in profiling
- notification threads [.NET Framework profiling]
- unmanaged code, profiling
- profiling API [.NET Framework], and COM
- profiling API [.NET Framework], unmanaged code profiling
- profilers, writing
- profiling API [.NET Framework], call stacks
- code profilers, writing
- profiling API [.NET Framework], security considerations
- profiling API [.NET Framework], managed code support
- common language runtime, profiling
- profiling API [.NET Framework], notification threads
- call stacks [.NET Framework profiling]
- profiling API [.NET Framework], stack depth
- common language runtime, writing a profiler
- profiling API [.NET Framework], information retrieval interfaces
- shadow stacks [.NET Framework profiling]
- COM, using in the profiling API
- stack snapshots [.NET Framework profiling]
- profiling API [.NET Framework], supported features
- profiling API [.NET Framework], overview
- security, profiling API considerations
- stack depth [.NET Framework profiling]
ms.assetid: 864c2344-71dc-46f9-96b2-ed59fb6427a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd0fef0e8a2c4b94cd5dd7beb140e669c52a07a8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862315"
---
# <a name="profiling-overview"></a>Übersicht über die Profilerstellung
<a name="top"></a> Ein Profiler ist ein Tool, das die Ausführung einer anderen Anwendung überwacht. Ein Common Language Runtime (CLR)-Profiler ist eine Dynamic Link Library (DLL), die aus Funktionen besteht, die mithilfe der Profilerstellungs-API Meldungen von der CLR empfangen und an diese senden. Die Profiler-DLL wird zur Laufzeit von der CLR geladen.  
  
 Herkömmliche Profilerstellungstools dienen vorwiegend dazu, die Ausführung der Anwendung zu messen. Das bedeutet, dass sie die für jede Funktion aufgebrachte Zeit und die Speicherauslastung der Anwendung über einen bestimmten Zeitraum messen. Die Profilerstellungs-API zielt auf eine breitere Klasse von Diagnosetools ab, z. B. Dienstprogramme zur Codeabdeckung und sogar erweiterte Debughilfen. Diese Verwendungsmöglichkeiten sind ausnahmslos von diagnostischer Natur. Die Profilerstellungs-API misst nicht nur die Ausführung einer Anwendung, sondern überwacht sie auch. Aus diesem Grund sollte die Profilerstellungs-API nie von der Anwendung selbst verwendet werden, und die Ausführung der Anwendung sollte nicht vom Profiler abhängen (oder davon beeinflusst werden).  
  
 Die Profilerstellung für eine CLR-Anwendung erfordert eine weiter reichende Unterstützung als die Profilerstellung für Computercode, der auf herkömmliche Weise kompiliert wurde. Dies liegt darin begründet, dass von der CLR Konzepte wie Anwendungsdomänen, Garbage Collection, verwaltete Ausnahmenbehandlung, Just-In-Time (JIT)-Kompilierung von Code (die Konvertierung von Microsoft Intermediate Language- bzw. MSIL-Code in systemeigenen Computercode) und ähnliche Features eingeführt werden. Herkömmliche Profilerstellungsmechanismen können keine nützlichen Informationen über diese Features identifizieren oder bereitstellen. Die Profilerstellungs-API liefert diese fehlenden Informationen hingegen in effizienter Weise und mit minimalen Auswirkungen auf die Leistung der CLR und die Anwendung, für die das Profil erstellt wird.  
  
 Die JIT-Kompilierung zur Laufzeit bietet hervorragende Möglichkeiten zur Profilerstellung. Die Profilerstellungs-API ermöglicht einem Profiler, den speicherinternen MSIL-Codestream für eine Routine zu ändern, bevor er JIT-kompiliert wird. Auf diese Weise kann der Profiler bestimmten Routinen, die genauer überprüft werden müssen, Instrumentationscode dynamisch hinzufügen. Dieser Ansatz ist zwar auch in herkömmlichen Szenarios möglich, lässt sich aber für die CLR mit der Profilerstellungs-API wesentlich einfacher umsetzen.  
  
 Diese Übersicht enthält folgende Abschnitte:  
  
-   [Die Profilerstellungs-API](#profiling_api)  
  
-   [Unterstützte Funktionen](#support)  
  
-   [Benachrichtigungsthreads](#notification_threads)  
  
-   [Sicherheit](#security)  
  
-   [Kombination von verwaltetem und nicht verwaltetem Code in einem Code-Profiler](#combining_managed_unmanaged)  
  
-   [Profilerstellung für nicht verwalteten Code](#unmanaged)  
  
-   [Verwenden von COM](#com)  
  
-   [Aufruflisten](#call_stacks)  
  
-   [Rückrufe und Stapeltiefe](#callbacks)  
  
-   [Verwandte Themen](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>Die Profilerstellungs-API  
 In der Regel wird die profilerstellungs-API verwendet, um das Schreiben einer *code Profiler*, dies ist ein Programm, das die Ausführung einer verwalteten Anwendung überwacht.  
  
 Die Profilerstellungs-API wird von einer Profiler-DLL verwendet, die in den gleichen Prozess geladen wird wie die Anwendung, für die ein Profil erstellt wird. Die Profiler-DLL implementiert eine Rückrufschnittstelle ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) in .NET Framework, Version 1.0 und 1.1, [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) in Version 2.0 oder höher). Die CLR ruft die Methoden in dieser Schnittstelle auf, um den Profiler über Ereignisse im profilierten Prozess zu benachrichtigen. Der Profiler kann einen Rückruf in die Laufzeit mit den Methoden in der [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) und [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) Schnittstellen zum Abrufen von Informationen über den Status der profilierten Anwendung.  
  
> [!NOTE]
>  Lediglich der zur Datenerfassung verwendete Teil der Profilerlösung sollte im gleichen Prozess ausgeführt werden wie die Anwendung, für die ein Profil erstellt wird. Alle Benutzeroberflächen- und Datenanalysevorgänge sollten in einem separaten Prozess ausgeführt werden.  
  
 Die folgende Abbildung zeigt, wie die Profiler-DLL mit der Anwendung, für die ein Profil erstellt wird, und der CLR interagiert.  
  
 ![Profilarchitektur](../../../../docs/framework/unmanaged-api/profiling/media/profilingarch.png "ProfilingArch")  
Profilerstellungsarchitektur  
  
### <a name="the-notification-interfaces"></a>Die Benachrichtigungsschnittstellen  
 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) und [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) können als Benachrichtigungsschnittstellen betrachtet werden. Diese Schnittstellen bestehen aus Methoden wie z. B. [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), und [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Jedes Mal, wenn die CLR eine Klasse lädt oder entlädt, eine Funktion kompiliert usw., ruft sie die entsprechende Methode in der `ICorProfilerCallback`-Schnittstelle oder in der `ICorProfilerCallback2`-Schnittstelle des Profilers auf.  
  
 Beispielsweise kann ein Profiler codeleistung anhand von zwei Benachrichtigungsfunktionen messen: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) und [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Dazu versieht er lediglich jede Benachrichtigung mit einem Zeitstempel, sammelt Ergebnisse und gibt eine Liste aus, aus der ersichtlich ist, welche Funktionen während der Anwendungsausführung die meiste CPU- oder Realzeit in Anspruch genommen haben.  
  
### <a name="the-information-retrieval-interfaces"></a>Die Datenabrufschnittstellen  
 Die andere bei der profilerstellung main Schnittstellen sind [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) und [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Der Profiler ruft diese Schnittstellen nach Bedarf auf, um weitere Daten für seine Analysen abzurufen. Beispielsweise jedes Mal, wenn die CLR ruft die [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) -Funktion, er stellt einen Funktionsbezeichner bereit. Der Profiler erhalten weitere Informationen zu dieser Funktion durch Aufrufen der [ICorProfilerInfo2:: Getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) Methode, um die übergeordnete Klasse der Funktion, die Namen usw. zu ermitteln.  
  
 [Zurück zum Anfang](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Unterstützte Funktionen  
 Die Profilerstellungs-API bietet Informationen über verschiedene Ereignisse und Aktionen in der Common Language Runtime. Sie können diese Informationen zum Überwachen der internen Funktionsweise von Prozessen und zum Analysieren der Leistung Ihrer .NET Framework-Anwendung verwenden.  
  
 Die Profilerstellungs-API ruft Informationen über die folgenden Aktionen und die Ereignisse ab, die in der CLR auftreten:  
  
-   CLR-Ereignisse beim Starten und Herunterfahren.  
  
-   Ereignisse bei der Anwendungsdomänenerstellung und beim Herunterfahren.  
  
-   Ereignisse beim Laden und Entladen von Assemblys.  
  
-   Ereignisse beim Laden und Entladen von Ereignissen.  
  
-   Ereignisse beim Erstellen und Löschen von COM-vtable.  
  
-   Ereignisse bei der JIT-Kompilierung (Just-In-Time) und beim Codepitching.  
  
-   Ereignisse beim Laden und Entladen von Klassen.  
  
-   Ereignisse beim Erstellen und Löschen von Threads.  
  
-   Ereignisse beim Funktionseinstieg und Funktionsende.  
  
-   Ausnahmen.  
  
-   Übergänge zwischen verwalteter und nicht verwalteter Codeausführung.  
  
-   Übergänge zwischen verschiedenen Laufzeitkontexten.  
  
-   Informationen über Laufzeitunterbrechungen.  
  
-   Informationen über den Laufzeitspeicherheap und die Garbage Collection-Aktivität.  
  
 Die Profilerstellungs-API kann von jeder (nicht verwalteten) COM-kompatiblen Sprache aufgerufen werden.  
  
 Die API ist im Hinblick auf die Prozessor- und Speicherauslastung effizient. Durch die Profilerstellung werden an der Anwendung mit Profil keine Änderungen durchgeführt, die so signifikant sind, dass es zu falschen Ergebnissen kommt.  
  
 Die Profilerstellungs-API ist sowohl für Samplingprofiler als auch für andere Profiler nützlich. Ein *Beispielprofiler* auf 5 Millisekunden das Profil in regelmäßigen Teilstrichen, z. B. untersucht. Ein *nicht-Samplingprofiler* wird darüber informiert, eines Ereignisses synchron mit dem Thread, der das Ereignis auslöst.  
  
### <a name="unsupported-functionality"></a>Nicht unterstützte Funktionalität  
 Die Profilerstellungs-API unterstützt die folgenden Funktionen nicht:  
  
-   Nicht verwalteter Code, der mit konventionellen Win32-Methoden profiliert werden muss. Der CLR-Profiler umfasst jedoch Übergangsereignisse, um die Grenzen zwischen verwaltetem und nicht verwaltetem Code zu ermitteln.  
  
-   Sich selbst ändernde Anwendungen, die ihren eigenen Code zu bestimmten Zwecken, beispielsweise bei der aspektorientierten Programmierung, selbsttätig ändern.  
  
-   Grenzüberprüfung, da die Profilerstellungs-API diese Informationen nicht bereitstellt. Die CLR bietet systeminterne Unterstützung für die Überprüfung von Grenzen des gesamten verwalteten Codes.  
  
-   Remoteprofilerstellung, die aus den folgenden Gründen nicht unterstützt wird:  
  
    -   Durch die Remoteprofilerstellung verlängert sich die Ausführungszeit. Bei der Verwendung der Profilerstellungsschnittstellen müssen Sie die Ausführungszeit minimieren, damit die Auswirkungen auf die Profilerstellungsergebnisse möglichst gering bleiben. Dies trifft insbesondere dann zu, wenn die Ausführungsleistung überwacht wird. Dabei stellt die Remoteprofilerstellung jedoch keine Einschränkung dar, wenn Profilerstellungsschnittstellen zum Überwachen der Speicherauslastung oder zum Abrufen von Laufzeitinformationen über Stapelrahmen, Objekte usw. verwendet werden.  
  
    -   Der CLR-Codeprofiler muss mindestens eine Rückrufschnittstelle bei der Laufzeit des lokalen Computers registrieren, auf dem die Anwendung mit Profil ausgeführt wird. Hierdurch wird die Möglichkeit eingeschränkt, einen Remotecodeprofiler zu erstellen.  
  
-   Profilerstellung in Produktionsumgebungen, die eine hohe Verfügbarkeit erfordern. Die Profilerstellungs-API wurde erstellt, um die Diagnose bei der Entwicklung zu unterstützen. Sie wurde nicht den strengen Tests unterzogen, die für die Unterstützung einer Produktionsumgebung erforderlich sind.  
  
 [Zurück zum Anfang](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Benachrichtigungsthreads  
 In den meisten Fällen führt der Thread, der ein Ereignis generiert, auch Benachrichtigungen aus. Diese e-Mail-Benachrichtigungen (z. B. [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) und [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) müssen nicht den expliziten angeben `ThreadID`. Zudem kann der Profiler basierend auf der `ThreadID` des jeweiligen Threads entscheiden, seine Analyseblöcke im lokalen Threadspeicher zu speichern und zu aktualisieren, anstatt die Analyseblöcke im globalen Speicher zu indizieren.  
  
 Beachten Sie, dass diese Rückrufe nicht serialisiert werden. Benutzer müssen ihren Code schützen, indem sie threadsichere Datenstrukturen erstellen und den Profilercode ggf. sperren, um zu verhindern, dass mehrere Threads parallel darauf zugreifen. Deshalb kann es in bestimmten Fällen passieren, dass Sie eine ungewöhnliche Sequenz von Rückrufen erhalten. Nehmen Sie z. B. an, dass eine verwaltete Anwendung zwei Threads erzeugt, die identischen Code ausführen. In diesem Fall ist es möglich, dass eine [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) -Ereignis für eine Funktion von einem Thread und einen `FunctionEnter` -Rückruf von dem anderen Thread empfangen, bevor die [ ICorProfilerCallback:: JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) Rückruf. In diesem Fall erhält der Benutzer einen `FunctionEnter`-Rückruf für eine Funktion, für die möglicherweise noch keine vollständige JIT-Kompilierung (Just-In-Time) erfolgt ist.  
  
 [Zurück zum Anfang](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Sicherheit  
 Eine Profilerstellungs-DLL ist eine nicht verwaltete DLL, die als Teil der Common Language Runtime-Ausführungs-Engine ausgeführt wird. Daher gelten die Einschränkungen für die Sicherheit des Zugriffs auf verwalteten Code nicht für den Code in der Profilerstellungs-DLL. Für die Profilerstellungs-DLL gelten nur die Einschränkungen, die das Betriebssystem für den Benutzer erzwingt, der die Anwendung mit Profil ausführt.  
  
 Entwickler von Profilern sollten entsprechende Vorkehrungen treffen, um sicherheitsrelevante Probleme zu vermeiden. So sollte beispielsweise eine Profilerstellungs-DLL während der Installation in eine Zugriffssteuerungsliste (ACL) aufgenommen werden, damit sie nicht durch böswillige Benutzer geändert werden kann.  
  
 [Zurück zum Anfang](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Kombination von verwaltetem und nicht verwaltetem Code in einem Codeprofiler  
 Ein falsch geschriebener Profiler kann zirkuläre Verweise auf sich selbst verursachen und zu unvorhersehbarem Verhalten führen.  
  
 Bei näherer Betrachtung der Profilerstellungs-API kann der Eindruck entstehen, dass es möglich wäre, einen Profiler mit verwalteten und nicht verwalteten Komponenten zu schreiben, die sich gegenseitig über COM-Interop oder indirekte Aufrufe aufrufen.  
  
 Obwohl dies aus der Entwurfsperspektive möglich ist, unterstützt die Profilerstellungs-API keine verwalteten Komponenten. Ein CLR-Profiler darf keinerlei verwaltete Komponenten enthalten. Versuche, verwalteten und nicht verwalteten Code in einem CLR-Profiler zu kombinieren, können Regelverletzungen, Programmausfälle oder Deadlocks verursachen. Die verwalteten Komponenten des Profilers verweisen Ereignisse zurück an ihre nicht verwalteten Komponenten, die in der Folge erneut die verwalteten Komponenten aufrufen. Dies führt zu zirkulären Verweisen.  
  
 Der einzige Ort, an dem ein CLR-Profiler verwalteten Code sicher aufrufen kann, ist innerhalb des Texts einer Methode im MSIL-Code (Microsoft Intermediate Language). Die empfohlene Vorgehensweise zum Ändern der MSIL-Texts ist die Verwendung von der JIT-neukompilierungsmethoden in der [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) Schnittstelle.  
  
 Es können auch die älteren Instrumentierungsmethoden zum Ändern von MSIL verwendet werden. Bevor die just-in-Time (JIT)-Kompilierung einer Funktion abgeschlossen ist, kann der Profiler verwaltete Aufrufe einfügen, in den MSIL-Text, der eine Methode und klicken Sie dann eine JIT-kompiliert es (finden Sie unter den [ICorProfilerInfo:: GetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) Methode). Diese Technik lässt sich erfolgreich für die selektive Instrumentierung von verwaltetem Code oder für die Erfassung von Statistik- und Leistungsdaten für JIT verwenden.  
  
 Alternativ dazu kann ein Codeprofiler native Hooks in den MSIL-Text jeder verwalteten Funktion einfügen, die nicht verwalteten Code aufruft. Diese Technik kann für Instrumentation und Abdeckung verwendet werden. So kann beispielsweise ein Codeprofiler Instrumentationshooks nach jedem MSIL-Block einfügen, um sicherzustellen, dass der Block ausgeführt wurde. Bei der Modifikation des MSIL-Texts einer Methode muss sehr sorgfältig vorgegangen werden, und eine Vielzahl von Faktoren muss berücksichtigt werden.  
  
 [Zurück zum Anfang](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Profilerstellung für nicht verwalteten Code  
 Die Profilerstellungs-API der Common Language Runtime (CLR) bietet minimale Unterstützung zur Profilerstellung für nicht verwalteten Code. Die folgende Funktionalität wird bereitgestellt:  
  
-   Enumeration von Stapelketten. Dieses Feature ermöglicht einem Codeprofiler, die Grenze zwischen verwaltetem und nicht verwaltetem Code zu bestimmen.  
  
-   Feststellung, ob eine Stapelkette verwaltetem oder systemeigenem Code entspricht.  
  
 In .NET Framework, Version 1.0 und 1.1, sind diese Methoden über den prozessinternen Teil der Debug-API der CLR verfügbar. Sie sind in der Datei "CorDebug.idl" definiert.  
  
 In .NET Framework 2.0 und höher können Sie die [ICorProfilerInfo2:: DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) -Methode für diese Funktionalität.  
  
 [Zurück zum Anfang](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>Verwenden von COM  
 Obwohl die Profilerstellungsschnittstellen als COM-Schnittstellen definiert sind, initialisiert die Common Language Runtime (CLR) COM tatsächlich nicht zur Verwendung dieser Schnittstellen. Der Grund dafür ist, um zu vermeiden, dass Festlegen des Threadingmodells durch Verwendung der [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) funktionieren, bevor die verwaltete Anwendung die Möglichkeit, die das gewünschte Threadingmodell festzulegen hatte. Ähnlich sollte auch der Profiler selbst `CoInitialize`, nicht aufrufen, da sonst ein Threadingmodell ausgewählt werden könnte, das mit der Anwendung, für die ein Profil erstellt wird, nicht kompatibel ist und es daher zu einem Anwendungsfehler kommen kann.  
  
 [Zurück zum Anfang](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Aufruflisten  
 Die Profilerstellungs-API bietet zwei Methoden zum Abrufen von Aufruflisten: eine Stapelmomentaufnahmemethode, mit der Anruflisten sporadisch überwacht werden können, und eine Schattenstapelmethode, mit der Anruflisten laufend überwacht werden können.  
  
### <a name="stack-snapshot"></a>Stapelmomentaufnahme  
 Unter einer Stapelmomentaufnahme versteht man die Überwachung eines Threadstapels zu einem bestimmten Zeitpunkt. Die Profilerstellungs-API unterstützt die Überwachung von verwalteten Funktionen im Stapel, überlässt jedoch die Überwachung nicht verwalteter Funktionen dem Stackwalker des Profilers.  
  
 Weitere Informationen dazu, wie Sie den Profiler zum Durchlaufen verwalteter Stapel programmieren, finden Sie die [ICorProfilerInfo2:: DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) Methode in dieser Dokumentation und [Profiler Durchlaufen von Stapeln im .NET Framework 2.0: Grundlagen und mehr](https://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Schattenstapel  
 Die allzu häufige Verwendung der Momentaufnahmemethode kann schnell zu Leistungseinbußen führen. Wenn stapelüberwachungen werden sollen, Ihr Profiler sollten stattdessen erstellen Sie mit einem Schattenstapel mithilfe der [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), und [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) ausnahmerückrufen. Der Schattenstapel ist immer aktuell und kann schnell in den Speicher kopiert werden, wenn eine Stapelmomentaufnahme benötigt wird.  
  
 Mit einem Schattenstapel können Funktionsargumente, Rückgabewerte und Informationen über generische Instanziierungen abgerufen werden. Diese Informationen sind nur über den Schattenstapel verfügbar und können abgerufen werden, wenn die Steuerung an eine Funktion übergeben wird. Sobald die Funktion ausgeführt wird, sind diese Informationen u. U. jedoch nicht mehr verfügbar.  
  
 [Zurück zum Anfang](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Rückrufe und Stapeltiefe  
 Profilerrückrufe können ausgegeben werden, wenn der Stapel stark eingeschränkt ist, und ein Stapelüberlauf in einem Profilerrückruf führt zum sofortigen Prozessende. Ein Profiler sollte bei der Reaktion auf Rückrufe möglichst wenige Stapel verwenden. Wenn der Profiler für Prozesse verwendet werden soll, die vor Stapelüberlauf geschützt sind, sollte der Profiler selbst möglichst auch keinen Stapelüberlauf auslösen.  
  
 [Zurück zum Anfang](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Einrichten einer Profilerstellungsumgebung](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Erklärt, wie ein Profiler initialisiert, Ereignisbenachrichtigungen festgelegt und ein Profil für einen Windows-Dienst erstellt werden.|  
|[Profilerstellungsschnittstellen](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Beschreibt die nicht verwalteten Schnittstellen, die die Profilerstellungs-API verwendet.|  
|[Profilerstellung für globale statische Funktionen](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Beschreibt die nicht verwalteten globalen statischen Funktionen, die die Profilerstellungs-API verwendet.|  
|[Profilerstellungsenumerationen](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Beschreibt die nicht verwalteten Enumerationen, die die Profilerstellungs-API verwendet.|  
|[Profilerstellungsstrukturen](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Beschreibt die nicht verwalteten Strukturen, die die Profilerstellungs-API verwendet.|
