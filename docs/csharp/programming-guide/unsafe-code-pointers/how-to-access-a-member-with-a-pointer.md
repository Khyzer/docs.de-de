---
title: 'Vorgehensweise: Zugreifen auf einen Member mit einem Zeiger – C#-Programmierhandbuch'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 9762b9e2487c30b81b7ef6ae22827b64e3cb02e2
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200350"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Zugreifen auf einen Member mit einem Zeiger (C#-Programmierhandbuch)
Um auf einen Member einer Struktur zuzugreifen, die in einem unsicheren Kontext deklariert ist, können Sie den Memberzugriffsoperator verwenden, wie im folgenden Beispiel gezeigt. Dabei ist `p` ein Zeiger auf eine [Struktur](../../../csharp/language-reference/keywords/struct.md), die den Member `x` enthält.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die [Struktur](../../../csharp/language-reference/keywords/struct.md) `CoOrds` deklariert und instanziiert, die die beiden Koordinaten `x` und `y` enthält. Mithilfe des Memberzugriffsoperators `->` und eines Zeigers auf die Instanz `home` werden `x` und `y` Werte zugewiesen.  
  
> [!NOTE]
>  Beachten Sie, dass der Ausdruck `p->x` und der Ausdruck `(*p).x` äquivalent sind. Sie erhalten dasselbe Ergebnis, unabhängig davon, welchen Ausdruck Sie verwenden.  
  
 [!code-csharp[csProgGuidePointers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#9)]  
  
 [!code-csharp[csProgGuidePointers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#10)]  
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)
- [Zeigerausdrücke](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Zeigertypen](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typen](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed-Anweisung](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
