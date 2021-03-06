---
title: Übersicht über Grafiken
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: 8d8e1ab286d4e5723f5ca6bca0b6eeff53ac1d43
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711342"
---
# <a name="overview-of-graphics"></a>Übersicht über Grafiken
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ist eine Anwendungsprogrammierschnittstelle (API), die das Subsystem des Betriebssystems Microsoft Windows bildet. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ist verantwortlich für die Anzeige von Informationen auf Bildschirmen und Druckern. Wie der Name andeutet, ist [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] der Nachfolger von [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], die Schnittstelle für Grafikgeräte (Graphics Device Interface), die in früheren Versionen von Windows enthalten ist.  
  
## <a name="managed-class-interface"></a>Schnittstelle für verwaltete Klassen  
 Die [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API wird über eine Reihe von Klassen, die als verwalteter Code verfügbar gemacht. Dieser Satz von Klassen heißt die *Schnittstelle für verwaltete Klassen* zu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Die Schnittstelle für verwaltete Klassen besteht aus den folgenden Namespaces:  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 Mit einem Graphics Device Interface wie z. B. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], Sie können die Informationen auf einem Bildschirm oder Drucker anzeigen, ohne sich Gedanken über die Details des jeweiligen Ausgabegeräts machen. Der Programmierer ruft Methoden auf, die von [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]-Klassen bereitgestellt werden. In diesen Methoden wiederum werden die speziellen Gerätetreiber aufgerufen. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] isoliert die jeweilige Anwendung von der Grafikhardware. Es ist diese Isolierung, die Programmierer geräteunabhängige Anwendungen erstellen kann.  
  
## <a name="see-also"></a>Siehe auch
- [Übersicht über Grafiken](graphics-overview-windows-forms.md)
