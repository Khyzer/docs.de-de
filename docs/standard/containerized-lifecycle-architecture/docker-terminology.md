---
title: Docker-Terminologie
description: Erfahren Sie, einige grundlegende Terminologie, die täglich verwendet hat, bei der Arbeit mit Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 07371bee6881b1fa7edf64b9bb50d387dcbf9dde
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677173"
---
# <a name="docker-terminology"></a>Docker-Terminologie

In diesem Abschnitt werden die Begriffe und Definitionen aufgelistet, mit denen Sie vertraut sein sollten, bevor Sie sich ausführlicher mit Docker beschäftigen. Weitere Definitionen finden Sie im umfangreichen [Glossar](https://docs.docker.com/glossary/) von Docker bereitgestellten.

**Containerimage:** Ein Paket mit allen benötigten Abhängigkeiten und Informationen zum Erstellen eines Containers. Ein Image enthält alle Abhängigkeiten (z.B. Frameworks) sowie die Bereitstellung und Ausführung der Konfiguration, die von einer Containerruntime verwendet werden. In der Regel wird ein Image aus mehreren zugrundeliegenden Images abgeleitet, die in Schichten übereinander liegen und das Dateisystem des Containers bilden. Ein Image ist unveränderlich, nachdem es erstellt wurde.

**Docker-Datei:** Eine Textdatei, die Anweisungen zum Erstellen eines Docker-Images enthält. Ist wie ein Stapelverarbeitungsskript, die erste Zeile gibt die Basisimages, um mit beginnen, und befolgen dann die Anweisungen zum Installieren der erforderlichen Programme, Kopieren von Dateien, und müssen usw., bis Sie die arbeitsumgebung erhalten.

**Build:** Die Aktion zum Erstellen eines Containerimages auf der Grundlage der Informationen und des Kontexts der Docker-Datei sowie weiteren Dateien im Ordner, in dem das Image erstellt wird. Sie können Images mit Docker erstellen **`docker build`** Befehl.

**Container:** Eine Instanz eines Docker-Images. Ein Container stellt die Ausführung einer einzelnen Anwendung, eines Prozesses oder Diensts dar. Er besteht aus den Inhalten eines Docker-Images, einer Ausführungsumgebung und mehreren Standardanweisungen. Beim Skalieren eines Diensts erstellen Sie mehrere Instanzen eines Containers aus dem gleichen Image. Alternativ kann ein Batchauftrag mehrere Container aus dem gleichen Image erstellen und dabei verschiedene Parameter an jede Instanz übergeben.

**Volumes:** Sie bieten ein Dateisystem mit Schreibzugriff, das vom Container verwendet werden kann. Da Images schreibgeschützt sind, die meisten Programme aber in das Dateisystem schreiben müssen, fügen Volumes eine beschreibbare Schicht oberhalb des Containerimages hinzu, so dass die Programme Zugriff auf ein beschreibbares Dateisystem haben. Das Programm weiß nicht, er greift auf ein überlappende Dateisystem, sondern nur das Dateisystem wie gewohnt. Volumes befinden sich auf dem Hostsystem und werden von Docker verwaltet.

**Tag:** Eine Markierung oder eine Bezeichnung, die Sie auf Images anwenden können, damit verschiedene Images oder Versionen desselben Images (abhängig von der Versionsnummer oder der Zielumgebung) identifiziert werden können.

**Mehrstufige Builds:** Ein Feature seit Docker 17.05 oder höher, das dabei hilft, die Größe der endgültigen Images zu verringern. Kurz gesagt können Sie mit einem mehrstufigen Build beispielsweise ein großes Basisimage verwenden, das das SDK enthält, um die Anwendung zu kompilieren und zu veröffentlichen, und den Veröffentlichungsordner anschließend mit einem kleinen Basisimage verwenden, das nur als Runtime dient, um ein viel kleineres endgültiges Image zu erzeugen.

**Repositoryname (Repo):** Eine Auflistung von zugehörigen Docker-Images mit dem Tag, das die Version des Images angibt. Einige Repositorys enthalten mehrere Varianten eines bestimmtes Images, z.B. ein Image mit SDKs (schwerer), ein Image nur mit Runtimes (leichter), usw. Diese Varianten können mit Tags markiert werden. Ein Repository kann Plattformvarianten enthalten, wie z.B. ein Linux-Image und ein Windows-Image.

**Registrierung:** Ein Dienst, der Zugriff auf Repositorys bereitstellt. Die Standardregistrierung für die meisten öffentlichen Images ist der [Docker-Hub](https://hub.docker.com/) (im Besitz des Docker-Unternehmens). Eine Registrierung enthält in der Regel Repositorys mehrerer Teams. Unternehmen haben häufig private Registrierungen zum Speichern und Verwalten von Images, die sie erstellt haben. Azure Container Registry ist ein weiteres Beispiel.

**Images für mehrere Architekturen:** Für Multi-Architektur ist ein Feature, das die Auswahl des entsprechenden Bilds vereinfacht die Plattform, auf dem Docker, z. B. ausgeführt wird Wenn eine dockerfile-Datei ein Basisimage anfordert **`FROM microsoft/dotnet:2.1-sdk`** aus der Registrierung Tatsächlich wird **`2.1-sdk-nanoserver-1709`**, **`2.1-sdk-nanoserver-1803`** oder **`2.1-sdk-alpine`** je nach Betriebssystem und Version, die dem Docker ausgeführt wird.

**Docker-Hub:** Eine öffentliche Registrierung zum Hochladen von und Arbeiten mit Images. Docker-Hub bietet Docker-Imagehosts, öffentliche oder private Registrierungen, Buildtrigger, Web-Hooks und Integration mit GitHub und Bitbucket.

**Azure Container Registry:** Eine öffentliche Ressource zur Arbeit mit Docker-Images und deren Komponenten in Azure. Dies stellt eine Registrierung ist in der Nähe Ihrer Bereitstellungen in Azure und die Ihnen die Kontrolle über den Zugriff, wodurch es möglich ist, verwenden Sie Ihre Azure Active Directory-Gruppen und Berechtigungen.

**Docker Trusted Registry (DTR):** Ein Docker-Registrierungsdienst (von Docker), der lokal installiert werden kann, sodass er innerhalb des Datencenters und Netzwerks des Unternehmens aktiv ist. Es ist praktisch für private Images, die in Ihrem Unternehmen verwaltet werden sollen. Docker Trusted Registry ist als Bestandteil im Produkt Docker Datacenter enthalten. Weitere Informationen finden Sie unter [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE):** Entwicklungstools für Windows und macOS zum lokalen Erstellen, Ausführen und Testen von Containern. Docker CE für Windows bietet Entwicklungsumgebungen für Linux- und Windows-Container. Der Linux-Docker-Host auf Windows basiert auf einer [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization)-VM. Der Host für die Windows-Container basiert direkt auf Windows. Docker CE für Mac basiert auf dem Apple Hypervisor-Framework und dem [Xhyve-Hypervisor](https://github.com/mist64/xhyve), der eine Linux-Docker-Host-VM auf Mac OS X bereitstellt. Docker CE für Windows und für Mac ersetzt Docker Toolbox, das auf Oracle VirtualBox basiert.

**Docker Enterprise Edition (EE):** Eine Version der Docker-Tools für Unternehmen für die Linux- und Windows-Entwicklung.

**Compose:** Ein Befehlszeilentool und YAML-Dateiformat mit Metadaten zum Definieren und Ausführen von Anwendungen mit mehreren Container. Sie definieren eine einzelne Anwendung basierend auf mehreren Images mit einer oder mehreren .yml-Dateien, die Werte abhängig von der Umgebung überschreiben können. Nachdem Sie die Definitionen erstellt haben, können Sie die Anwendung völlig mit mehreren Containern mit einem einzigen Befehl bereitstellen (Docker-compose-einrichten), einen Container pro Image auf Docker-Host erstellt.

**Cluster:** Eine Sammlung von zur Verfügung gestellten Docker-Hosts, als handele es sich um einen einzelnen, virtuellen Docker-Host, sodass die Anwendung mehrere Instanzen der Dienste skalieren kann, die auf mehrere Hosts im Cluster verteilt sind. Docker-Cluster können mit Kubernetes, Azure Service Fabric, Docker Swarm und Mesosphere DC/OS erstellt werden.

**Orchestrator:** Ein Tool, das die Verwaltung von Clustern und Docker-Hosts vereinfacht. Orchestratoren ermöglichen es Ihnen, ihre Bilder, Container und Hosts über eine Befehlszeilenschnittstelle (CLI) zu verwalten oder eine grafische Benutzeroberfläche. Sie können u.a. Containernetzwerke, Konfigurationen, den Lastenausgleich, die Dienstermittlung, die Hochverfügbarkeit und die Konfiguration des Docker-Hosts verwalten. Ein Orchestrator ist verantwortlich für die Ausführung, Verteilung, Skalierung und Reparatur von Workloads in einer Knotensammlung. Orchestratorprodukte sind in der Regel die gleichen Produkte, die Clusterinfrastruktur bereitstellen, wie Kubernetes und Azure Service Fabric, nebst anderen Angeboten am Markt.

>[!div class="step-by-step"]
>[Zurück](what-is-docker.md)
>[Weiter](docker-containers-images-and-registries.md)