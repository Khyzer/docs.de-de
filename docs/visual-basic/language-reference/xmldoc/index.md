---
title: Empfohlene XML-Tags für Dokumentationskommentare (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
  - vb.XmlDocComment
helpviewer_keywords:
  - 'tags, XML'
  - 'XML comments, recommended tags [Visual Basic]'
  - 'comments, recommended XML tags'
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Empfohlene XML-Tags für Dokumentationskommentare (Visual Basic)
Visual Basic-Compiler kann Dokumentationskommentaren in Ihrem Code in eine XML-Datei verarbeitet werden. Sie können zusätzliche Tools verwenden, zum Verarbeiten der XML-Datei in der Dokumentation.  
  
 XML-Kommentare dürfen in Codekonstrukten wie Typen und Typmember. Für partielle Typen haben nur ein Teil des Typs XML-Kommentaren, aber es keine Einschränkung gibt für die Kommentierung von Membern.  
  
> [!NOTE]
>  Dokumentationskommentare können nicht auf Namespaces angewendet werden. Der Grund ist, dass ein Namespace mehrere Assemblys umfassen kann und nicht alle Assemblys gleichzeitig geladen werden.  
  
 Der Compiler verarbeitet alle Tags, die gültigen XML-Code ist. Die folgenden Tags stellen häufig verwendete Funktionen in der Dokumentation für die Benutzer bereit.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> der Compiler überprüft die Syntax.)  
  
> [!NOTE]
>  Wenn die Spitze Klammern im Text eines Dokumentationskommentars angezeigt werden soll, verwenden Sie `&lt;` und `&gt;`. Z. B. die Zeichenfolge `"&lt;text in angle brackets&gt;"` hostnamensadresse `<text in angle brackets>`.  
  
## <a name="see-also"></a>Siehe auch
- [Dokumentieren von Code mit XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Vorgehensweise: Erstellen von XML-Dokumentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
