---
title: ICorProfilerInfo::BeginInprocDebugging-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e23f39f8e7a1812366e15ffec9589f756c73f94
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481689"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging-Methode
Initialisiert in-Process-debugging-Unterstützung. Diese Methode ist in .NET Framework, Version 2.0, veraltet.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>Parameter  
 `fThisThreadOnly`  
 [in] Legen Sie diesen Wert auf `true` zum Initialisieren der debugging-Unterstützung für nur den aktuellen Thread; legen Sie ihn auf `false` Debuggingunterstützung für alle Threads zu initialisieren.  
  
 `pdwProfilerContext`  
 [out] Der Zeiger auf ein Rückgabewert, der die Debugsitzung identifiziert.  
  
## <a name="remarks"></a>Hinweise  
 Die Debugdiensten der CLR unterstützt eingeschränkte prozessinternen Debuggens in .NET Framework, Version 1.0 und 1.1. In-Process-Debuggen aktiviert einen Profiler, die Prüfung Teile der Debug-API zu verwenden. Jedoch aufgrund von Kundenfeedback hat prozessinternen Debuggens wurden entfernt von .NET Framework Version 2.0, und mit einem Satz von Funktionen, die enger an die profilerstellungs-API ersetzt.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework Version:** 1.0  
  
## <a name="see-also"></a>Siehe auch
- [ICorProfilerInfo-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
