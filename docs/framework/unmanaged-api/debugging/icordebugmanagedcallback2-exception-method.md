---
title: ICorDebugManagedCallback2::Exception-Methode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f776f20f163df91d65509e5dbab31fe9c29a965
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492100"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception-Methode
Benachrichtigt den Debugger, dass eine Suche nach einem Ausnahmehandler gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `pAppDomain`  
 [in] Ein Zeiger auf ein ICorDebugAppDomain-Objekt, das mit dem Thread, der auf dem die Ausnahme ausgelöst wurde der Anwendungsdomäne darstellt.  
  
 `pThread`  
 [in] Ein Zeiger auf ein ICorDebugThread-Objekt, das den Thread darstellt, auf dem die Ausnahme ausgelöst wurde.  
  
 `pFrame`  
 [in] Ein Zeiger auf ein ICorDebugFrame-Objekt, das einen Frame darstellt, durch die `dwEventType` Parameter. Weitere Informationen finden Sie in der Tabelle im Abschnitt "Hinweise".  
  
 `nOffset`  
 [in] Eine ganze Zahl, die einen Offset angibt, laut der `dwEventType` Parameter. Weitere Informationen finden Sie in der Tabelle im Abschnitt "Hinweise".  
  
 `dwEventType`  
 [in] Der Wert CorDebugExceptionCallbackType-Enumeration, die der den von diesem Ausnahmerückruf angibt.  
  
 `dwFlags`  
 [in] Der Wert der [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) Enumeration, die zusätzliche Informationen über die Ausnahme angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die `Exception` Rückruf zu verschiedenen Zeitpunkten während der Suche Phase des Prozesses für die Ausnahmebehandlung aufgerufen wird. D. h. es kann aufgerufen werden, mehr als einmal während eine Ausnahme entladen.  
  
 Die Ausnahme, die verarbeitet werden kann abgerufen werden, aus der ICorDebugThread-Objekt, das auf die `pThread` Parameter.  
  
 Der bestimmten Frame und Offset hängen von der `dwEventType` Parameter wie folgt:  
  
|Wert von `dwEventType`|Wert von `pFrame`|Wert von `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Der Frame, der die Ausnahme ausgelöst hat.|Der Anweisungszeiger im Frame.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Der Rahmen Benutzercode dem Punkt der ausgelösten Ausnahme am nächsten ist.|Der Anweisungszeiger im Frame.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Der Frame, der den Catch-Handler enthält.|Der Microsoft intermediate Language (MSIL)-Offset des Anfangs des Catch-Handler.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Ist nicht definiert.|  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch
- [ICorDebugManagedCallback2-Schnittstelle](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback-Schnittstelle](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
