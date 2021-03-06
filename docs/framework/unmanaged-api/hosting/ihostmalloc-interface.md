---
title: IHostMalloc-Schnittstelle
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea3656fa00e84291ff7b2bdb65f9300cd7933c0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571781"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc-Schnittstelle
Enthält Methoden, die die common Language Runtime (CLR) zum Anfordern von differenzierter Zuordnungen aus dem Heap über den Host zu ermöglichen.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Alloc-Methode](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Fordert an, dass der Host die angeforderte Menge an Arbeitsspeicher aus dem Heap belegen.|  
|[DebugAlloc-Methode](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Fordert an, dass der Host die angeforderte Menge an Arbeitsspeicher aus dem Heap reserviert, und zudem nachverfolgen, in dem der Speicher belegt wurde.|  
|[Free-Methode](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Arbeitsspeicher, die mit zugeordnet wurde freigegeben der `Alloc` Methode.|  
  
## <a name="remarks"></a>Hinweise  
 Die CLR ruft einen Schnittstellenzeiger auf ein `IHostMalloc` -Instanz durch Aufrufen der [IHostMemoryManager:: CreateMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** MSCorEE.h  
  
 **Bibliothek:** Als Ressource in MSCorEE.dll enthalten  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch
- [IHostMemoryManager-Schnittstelle](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Hosten von Schnittstellen](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
