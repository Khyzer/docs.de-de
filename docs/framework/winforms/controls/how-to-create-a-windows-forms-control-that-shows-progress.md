---
title: 'Vorgehensweise: Erstellen Sie ein Windows Forms-Steuerelement, das ausgeführt wird.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 6910a7e2e68a3807e08a8b196dde003e1d5bc9af
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720243"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Vorgehensweise: Erstellen Sie ein Windows Forms-Steuerelement, das ausgeführt wird.
Das folgende Codebeispiel zeigt ein benutzerdefiniertes Steuerelement mit dem Namen `FlashTrackBar`, mit dem der Benutzer die Ebene oder den Fortschritt einer Anwendung anzeigen lassen kann. Es verwendet Farbverläufe, um den Fortschritt darzustellen.  
  
 Das `FlashTrackBar`-Steuerelement stellt die folgenden Konzepte dar:  
  
-   Speichern benutzerdefinierter Eigenschaften.  
  
-   Definieren benutzerdefinierter Ereignisse. (`FlashTrackBar` definiert das `ValueChanged`-Ereignis.)  
  
-   Überschreiben der <xref:System.Windows.Forms.Control.OnPaint%2A> Methode, um die Logik zum Zeichnen des Steuerelements bereitzustellen.  
  
-   Berechnen des verfügbaren Bereichs für das Zeichnen des Steuerelements mit dessen <xref:System.Windows.Forms.Control.ClientRectangle%2A> Eigenschaft. Dies erfolgt normalerweise durch `FlashTrackBar` in der Methode `OptimizedInvalidate`.  
  
-   Implementieren der Serialisierung oder Dauerhaftigkeit für eine Eigenschaft, wenn sie in Windows Forms-Designer geändert wird. `FlashTrackBar` definiert die Methoden `ShouldSerializeStartColor` und `ShouldSerializeEndColor` für die Serialisierung der Eigenschaften `StartColor` und `EndColor`.  
  
 In der folgenden Tabelle werden die von `FlashTrackBar` benutzerdefinierten Eigenschaften dargestellt.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|`AllowUserEdit`|Gibt an, ob der Benutzer den Wert der Flash-Trackleiste durch Klicken und Ziehen verändern kann.|  
|`EndColor`|Gibt die Farbe am Ende der Trackleiste an.|  
|`DarkenBy`|Gibt an, wie viel dunkler der Hintergrund in Bezug auf den Farbverlauf des Vordergrunds angezeigt wird.|  
|`Max`|Gibt den maximalen Wert der Trackleiste an.|  
|`Min`|Gibt den minimalen Wert der Trackleiste an.|  
|`StartColor`|Gibt die verwendete Anfangsfarbe des Farbverlaufs an.|  
|`ShowPercentage`|Gibt an, ob über dem Farbverlauf ein Prozentsatz angezeigt wird.|  
|`ShowValue`|Gibt an, ob über dem Farbverlauf der aktuelle Wert angezeigt wird.|  
|`ShowGradient`|Gibt an, ob die Trackleiste einen Farbverlauf mit dem aktuellen Wert anzeigen soll.|  
|-   `Value`|Gibt den aktuellen Wert der Trackleiste an.|  
  
 In der folgenden Tabelle werden zusätzliche von `FlashTrackBar:` definierte Member gezeigt: das durch eine geänderte Eigenschaft ausgelöste Ereignis und die Methode, die das Ereignis auslöst.  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`ValueChanged`|Das Ereignis, das ausgelöst wird, wenn die Eigenschaft `Value` der Trackleiste verändert wird.|  
|`OnValueChanged`|Die Methode, die das `ValueChanged`-Ereignis auslöst.|  
  
> [!NOTE]
>  `FlashTrackBar` verwendet die <xref:System.EventArgs> -Klasse für Ereignisdaten und <xref:System.EventHandler> für den Ereignisdelegat.  
  
 Zum Behandeln der entsprechenden *EventName* Ereignisse `FlashTrackBar` überschreibt die folgenden Methoden, die es erbt <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Um die entsprechenden durch geänderte Eigenschaften ausgelöste Ereignisse behandeln `FlashTrackBar` überschreibt die folgenden Methoden, die es erbt <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Beispiel  
 Das `FlashTrackBar`-Steuerelement definiert zwei UI-Typ-Editoren, `FlashTrackBarValueEditor` und `FlashTrackBarDarkenByEditor`, die in den folgenden Codeauflistungen veranschaulicht werden. Die `HostApp` -Klasse verwendet das `FlashTrackBar`-Steuerelement in einem Windows Form.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Siehe auch
- [Erweitern der Entwurfszeitunterstützung](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Grundlagen für das Entwickeln von Windows Forms-Steuerelementen](windows-forms-control-development-basics.md)
