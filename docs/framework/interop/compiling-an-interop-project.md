---
title: Kompilieren eines Interop-Projekts
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b9f0cd44e5ab9a33db4dd2ef52681f40ca54080
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835160"
---
# <a name="compiling-an-interop-project"></a>Kompilieren eines Interop-Projekts

COM-Interop-Projekte, die auf eine oder mehrere Assemblys mit importierten COM-Typen verweisen, werden wie jedes andere verwaltete Projekt kompiliert. Sie können auf Interop-Assemblys in einer Entwicklungsumgebung wie Visual Studio verweisen, oder Sie können darauf verweisen, wenn Sie einen Befehlszeilencompiler verwenden. In beiden Fällen muss die Interop-Assembly zur ordnungsgemäßen Kompilierung im selben Verzeichnis wie die anderen Projektdateien sein.

 Es gibt zwei Möglichkeiten zur Verweisung auf Interop-Assemblys:

-   Eingebettete Interoptypen: Ab [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] und Visual Studio 2010 können Sie den Compiler anweisen, die Typinformationen aus einer Interopassembly in die ausführbare Datei einzubetten. Dies ist das empfohlene Verfahren.

-   Bereitstellen von Interopassemblys: Sie können einen Standardverweis auf eine Interopassembly erstellen. In diesem Fall muss die Interop-Assembly mit Ihrer Anwendung bereitgestellt werden.

 Die Unterschiede zwischen diesen beiden Verfahren werden ausführlich in [Verwenden von COM-Typen in verwaltetem Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)) erläutert.

 Wie Interoptypen mit Visual Studio eingebettet werden, sehen Sie unter [Exemplarische Vorgehensweise: Einbetten von Typen aus verwalteten Assemblys in Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) und [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) (Exemplarische Vorgehensweise: Einbetten von Typen aus verwalteten Assemblys in Visual Studio (Visual Basic)).

 Verwenden Sie zum Verweisen auf eine Interop-Assembly mit einem Befehlszeilencompiler und Einbetten von Typinformationen in Ihre ausführbaren Dateien die Compilerschalter [/Link (C#-Compileroptionen)](../../csharp/language-reference/compiler-options/link-compiler-option.md) oder [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md), und geben Sie den Namen der Interop-Assembly an.

> [!NOTE]
> Visual C++-Anwendungen können keine Typinformationen einbetten, aber sie können mit Anwendungen oder Add-Ins zusammenarbeiten, die dies können.

 Verwenden Sie zum Kompilieren einer Anwendung, die bei der Bereitstellung eine primäre Interop-Assembly enthält, einen **/Referenz**-Compilerschalter, und geben Sie den Namen der Interop-Assembly an.

## <a name="see-also"></a>Siehe auch

- [Verfügbarmachen von COM-Komponenten für .NET Framework](exposing-com-components.md)
- [Sprachunabhängigkeit und sprachunabhängige Komponenten](../../standard/language-independence-and-language-independent-components.md)
- [Verwenden von COM-Typen in verwaltetem Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Exemplarische Vorgehensweise: Einbetten von Typen aus verwalteten Assemblys in Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [Exemplarische Vorgehensweise: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md) (Exemplarische Vorgehensweise: Einbetten von Typen aus verwalteten Assemblys in Visual Studio (Visual Basic))
- [Importing a Type Library as an Assembly (Importieren einer Typbibliothek als Assembly)](importing-a-type-library-as-an-assembly.md)