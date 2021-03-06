---
title: 'Vorgehensweise: Deaktivieren von ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: 3c18935239a4355d5416a0a79d0fa9f5c504cc7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720211"
---
# <a name="how-to-disable-toolstripmenuitems"></a>Vorgehensweise: Deaktivieren von ToolStripMenuItems
Können Sie einschränken oder erweitern die Befehle, die ein Benutzer aktivieren und Deaktivieren von Menüelementen in Benutzeraktivitäten herstellen kann. Menüelemente sind standardmäßig aktiviert, wenn sie erstellt wurden, aber dies die angepasst werden kann, über die <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> Eigenschaft. Sie können diese Eigenschaft zur Entwurfszeit im Bearbeiten der **Eigenschaften** Fenster oder programmgesteuert, indem sie im Code festlegen.  
  
### <a name="to-disable-a-menu-item-programmatically"></a>So deaktivieren Sie ein Menüelement programmgesteuert  
  
-   Fügen Sie innerhalb der Methode, in dem Sie die Eigenschaften des Menüelements festlegen, Code aus, um die <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> Eigenschaft `false`.  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  Deaktivieren das erste oder der obersten Ebene Menüelement in einem Menü Blendet alle Menüelemente im Menü enthalten, aber nicht deaktiviert werden. Ebenso Deaktivieren eines Menüelements, das über Untermenüelemente verfügt die Untermenüelemente ausgeblendet, aber nicht deaktiviert werden. Wenn alle Befehle in einem bestimmten Menü für den Benutzer nicht verfügbar sind, gilt die guten Programmierstil, ausgeblendet und deaktiviert das gesamte Menü, wie dies führt zu eine sauberen-Benutzeroberfläche. Sie sollten ausblenden und deaktivieren das Menü und jedes Element und ein Untermenüelement, das Sie im Menü deaktiviert werden, da der Zugriff auf einen Menübefehl über eine Tastenkombination ausblenden allein nicht verhindert wird. Legen Sie die <xref:System.Windows.Forms.ToolStripItem.Visible%2A> Eigenschaft eines Elements zum Menü der obersten Ebene `false` das gesamte Menü ausblenden.  
  
## <a name="see-also"></a>Siehe auch
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [Vorgehensweise: Ausblenden von ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [Übersicht über das MenuStrip-Steuerelement](menustrip-control-overview-windows-forms.md)
