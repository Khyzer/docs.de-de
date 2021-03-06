---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: e6bb04364c2f92129993e19c746fd7cb9c18dc8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648533"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
Zeigt die Compilerausgabe mit UTF-8-Codierung an.  
  
## <a name="syntax"></a>Syntax  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Argumente  
 `+` &#124; `-`  
 Dies ist optional. Der Standardwert für diese Option ist `-utf8output-`, was bedeutet der Ausgabe des Compilers nicht UTF-8-Codierung verwendet. Die Angabe von `-utf8output` ist mit der Angabe von `-utf8output+` identisch.  
  
## <a name="remarks"></a>Hinweise  
 Bei einigen internationalen Konfigurationen kann nicht der Ausgabe des Compilers ordnungsgemäß in der Konsole angezeigt werden. Verwenden Sie in solchen Situationen `-utf8output` und Compiler-Ausgabe in eine Datei umleiten.  
  
> [!NOTE]
>  Die `-utf8output` Option ist nicht in der Visual Studio-Entwicklungsumgebung verfügbar, sondern nur, wenn Sie über die Befehlszeile kompilieren.  
  
## <a name="example"></a>Beispiel  
 Der folgende code kompiliert `In.vb` und weist den Compiler anzuzeigende Ausgabe mit UTF-8-Codierung.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Siehe auch
- [Visual Basic-Befehlszeilencompiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Beispiele für Kompilierungsbefehlszeilen](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
