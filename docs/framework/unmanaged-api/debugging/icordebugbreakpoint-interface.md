---
title: ICorDebugBreakpoint-Schnittstelle
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7e454c15ddfa977a6d06921a5d80a6c05dca92f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973573"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint-Schnittstelle

Stellt einen Haltepunkt in einer Funktion oder einen Beobachtungspunkt für einen Wert dar.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Activate-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|Legt den aktiven Zustand dieses `ICorDebugBreakpoint`.|  
|[IsActive-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|Ruft einen Wert, der angibt, ob dies `ICorDebugBreakpoint` aktiv ist.|  
  
## <a name="remarks"></a>Hinweise  
 Haltepunkte unterstützen die bedingte Ausdrücke nicht direkt. Wenn eine solche Funktionalität gewünscht ist, muss ein Debugger implementieren oberhalb des `ICorDebugBreakpoint`.  
  
 ICorDebugFunctionBreakpoint-Schnittstelle erweitert `ICorDebugBreakpoint` um Haltepunkte innerhalb von Funktionen zu unterstützen.  
  
> [!NOTE]
>  Diese Schnittstelle kann weder computerübergreifend noch prozessübergreifend remote aufgerufen werden.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch
- [Debuggen von Schnittstellen](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
