---
title: SaveToHistory-Funktion (WPF nicht verwaltete API-Referenz)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: 853931b7b968f8103af8bf9c33c07d40ac653069
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489097"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a>SaveToHistory-Funktion (WPF nicht verwaltete API-Referenz)
Diese API unterstützt die Infrastruktur von Windows Presentation Foundation (WPF) und nicht direkt aus Ihrem Code verwendet werden soll.  
  
 Von der Windows Presentation Foundation (WPF)-Infrastruktur verwendet, für die Windows-Verwaltung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
## <a name="parameters"></a>Parameter  
 pHistoryStream  
 Ein Zeiger auf den Verlauf-Datenstrom.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Finden Sie unter [Systemanforderungen für .NET Framework](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 In .NET Framework 3.0 und 3.5: PresentationHostDLL.dll  
  
 In .NET Framework 4 und höher: PresentationHost_v0400.dll  
  
 **.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch
- [WPF – Referenz zur nicht verwalteten API](wpf-unmanaged-api-reference.md)
