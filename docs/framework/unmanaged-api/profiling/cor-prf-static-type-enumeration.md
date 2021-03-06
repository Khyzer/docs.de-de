---
title: COR_PRF_STATIC_TYPE-Enumeration
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34a2ca5b505c504115af47402c3d92a05ec0676f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737632"
---
# <a name="corprfstatictype-enumeration"></a>COR_PRF_STATIC_TYPE-Enumeration
Zeigt an, ob ein Feld statisch ist und, falls dies der Fall ist, ob die statische Qualität für das Feld gilt. Diese Werte können kombiniert werden, die bitweise OR-Operation verwenden, um anzugeben, dass das Feld mehrere verschiedene statische Eigenschaften.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|Das Feld ist nicht statisch.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Das Feld ist die Anwendung statischen Domäne.|  
|`COR_PRF_FIELD_THREAD_STATIC`|Das Feld ist threadstatischen.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Das Feld ist kontextstatische.|  
|`COR_PRF_FIELD_RVA_STATIC`|Das Feld ist die relative virtuelle Adresse (RVA) – statisch.|  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch
- [Profilerstellungsenumerationen](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
