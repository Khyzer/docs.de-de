---
title: 'Vorgehensweise: Ändern der Darstellung von ToolStrip-Text und-Bildern in Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: cd15e581e646f53ed56af654917c7543bf18617e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705401"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Vorgehensweise: Ändern der Darstellung von ToolStrip-Text und-Bildern in Windows Forms
Sie können steuern, ob Text und Bilder angezeigt werden, auf eine <xref:System.Windows.Forms.ToolStripItem> und wie diese im Verhältnis zueinander ausgerichtet sind und die <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Definieren Sie die Anzeige auf einem ToolStripItem  
  
-   Legen Sie die <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Eigenschaft auf den gewünschten Wert. Mögliche Werte sind `Image`, `ImageAndText`, `None`, und `Text`. Die Standardeinstellung ist `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Ausrichten von Text auf einem ToolStripItem  
  
-   Legen Sie die <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> Eigenschaft auf den gewünschten Wert. Mögliche Werte sind eine beliebige Kombination von Top, Middle und unten mit Links, zentriert und rechts. Die Standardeinstellung ist `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Anpassung an das ein Bild auf einem ToolStripItem  
  
-   Legen Sie die <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> Eigenschaft auf den gewünschten Wert. Mögliche Werte sind eine beliebige Kombination von Top, Middle und unten mit Links, zentriert und rechts. Die Standardeinstellung ist `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Definieren Sie, wie im Verhältnis zueinander ToolStripItem-Text und Bilder angezeigt werden  
  
-   Legen Sie die <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Eigenschaft auf den gewünschten Wert. Mögliche Werte sind `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, und `TextBeforeImage`. Die Standardeinstellung ist `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Siehe auch
- <xref:System.Windows.Forms.ToolStrip>
- [Übersicht über das ToolStrip-Steuerelement](toolstrip-control-overview-windows-forms.md)
- [Architektur des ToolStrip-Steuerelements](toolstrip-control-architecture.md)
- [Zusammenfassung der ToolStrip-Technologie](toolstrip-technology-summary.md)
