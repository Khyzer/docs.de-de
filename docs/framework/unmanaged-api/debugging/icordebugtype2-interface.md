---
title: ICorDebugType2 Interface
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f61efdecfb87ed598dd9675c0b8804259849e64c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706263"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2 Interface
Erweitert die Schnittstelle "ICorDebugType" die Typ-ID von einem Basistyp oder einen komplexen Typ auf (Benutzerdefiniert) abgerufen.  
  
## <a name="methods"></a>Methoden  
  
|Methode||  
|------------|-|  
|[GetTypeID-Methode](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Ruft eine [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) für diesen Typ.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ist eine logische Erweiterung der ICorDebugType-Schnittstelle.  
  
> [!NOTE]
>  Diese Schnittstelle kann weder computerübergreifend noch prozessübergreifend remote aufgerufen werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codefragment veranschaulicht die Verwendung von der [icordebugtype2:: GetTypeId](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) Methode.  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch
- [Debuggen von Schnittstellen](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
