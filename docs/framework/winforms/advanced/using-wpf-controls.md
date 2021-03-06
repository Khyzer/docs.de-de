---
title: Verwenden von WPF-Steuerelementen
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 24b88e456628c5a0bdc3cded60b0e52a92057851
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713799"
---
# <a name="using-wpf-controls"></a>Verwenden von WPF-Steuerelementen
Sie können Windows Presentation Foundation (WPF)-Steuerelemente in Windows Forms-basierten Anwendungen verwenden. Obwohl diese beiden Technologien für andere Ansicht sind, zusammenarbeiten sie reibungslos.  
  
 Der Windows Forms-Designer stellt eine visuelle entwurfsumgebung zum Hosten von Windows Presentation Foundation-Steuerelementen bereit. Ein WPF-Steuerelement gehostet wird, von einem speziellen Windows Forms-Steuerelement mit dem Namen <xref:System.Windows.Forms.Integration.ElementHost>. Mit diesem Steuerelement können das WPF-Steuerelement zur Teilnahme an das Layout des Formulars und zum Empfangen von Nachrichten von Tastatur und Maus. Sie können zur Entwurfszeit Anordnen der <xref:System.Windows.Forms.Integration.ElementHost> steuern, wie Sie jedes Windows Forms-Steuerelement.  
  
 Sie können auch Windows Forms-Steuerelementen in WPF-basierten Anwendungen verwenden. Weitere Informationen finden Sie unter [Entwerfen von XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Kopieren und Einfügen eines ElementHost-Steuerelements zur Entwurfszeit](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Zeigt, wie Sie ein Windows Presentation Foundation-Steuerelement in Windows Forms zu kopieren.  
  
 [Exemplarische Vorgehensweise: Anordnen von WPF-Inhalt in Windows Forms zur Entwurfszeit](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Veranschaulicht, wie die Windows Forms-Layoutfunktionen, z. B. Verankern und Ausrichtungslinien, Anordnen von Windows Presentation Foundation-Steuerelementen.
  
 [Exemplarische Vorgehensweise: Erstellen von neuen WPF-Inhalts in Windows Forms zur Entwurfszeit](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Zeigt, wie eine Windows Presentation Foundation-Steuerelement, für die Verwendung in Windows Forms-basierte Anwendungen zu erstellen.
  
 [Exemplarische Vorgehensweise: Zuweisen von WPF-Inhalt in Windows Forms zur Entwurfszeit](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Zeigt, wie die Windows Presentation Foundation-Steuerelementtypen auswählen, die Sie in Ihrem Formular anzeigen möchten.  
  
 [Exemplarische Vorgehensweise: Formatieren von WPF-Inhalt](walkthrough-styling-wpf-content.md)  
 Zeigt den Workflow zwischen dem Windows Forms-Designer und die [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] zum Anwenden von Stilen für Windows Presentation Foundation-Steuerelemente.  
  
## <a name="reference"></a>Referenz  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Beschreibt eine Klasse, die Sie zum Hosten von Windows Presentation Foundation-Steuerelementen in Windows Forms-basierten Anwendungen verwenden können.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Beschreibt eine Klasse, die Sie zum Hosten von Windows Forms-Steuerelementen in der Windows Presentation Foundation-basierte Anwendung verwenden können.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Migration und Interoperabilität](../../wpf/advanced/migration-and-interoperability.md)  
 Beschreibt die Interoperation zwischen der Windows Presentation Foundation und Windows Forms-Technologien.  
  
 [Entwerfen von XAML-Code in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 Beschreibt, wie Windows Presentation Foundation-Steuerelemente in Visual Studio entwerfen.
