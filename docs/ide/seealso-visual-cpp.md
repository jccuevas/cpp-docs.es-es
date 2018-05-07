---
title: '&lt;seealso&gt; (Visual C++) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <seealso>
- seealso
dev_langs:
- C++
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a726a2fa1694fd346a6632fdc5e40bd53547fc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ltseealsogt-visual-c"></a>&lt;seealso&gt; (Visual C++)
La etiqueta \<seealso> le permite especificar el texto que quiere que aparezca en una sección Vea también. Use [\<see>](../ide/see-visual-cpp.md) para especificar un vínculo desde dentro del texto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `member`  
 Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual.  Ponga el nombre entre comillas simples o dobles.  
  
 El compilador comprueba si el elemento de código dado existe y resuelve `member` al nombre de elemento en el resultado XML.  El compilador emite una advertencia si no encuentra `member`.  
  
 Para obtener información sobre cómo crear una referencia cref a un tipo genérico, vea [\<see>](../ide/see-visual-cpp.md).  
  
## <a name="remarks"></a>Comentarios  
 Compile con [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación a un archivo.  
  
 Vea [\<summary>](../ide/summary-visual-cpp.md) para obtener un ejemplo del uso de \<seealso>.  
  
 El compilador de Visual C++ intentará resolver referencias cref en un paso por los comentarios de documentación.  Por tanto, si usa las reglas de búsqueda de C++, un símbolo que no encuentra el compilador se marcará como no resuelto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se hace referencia a un símbolo sin resolver en cref. El comentario XML para el cref a B::Test será `<seealso cref="!:B::Test" />`, mientras que la referencia a A::Test está bien formada `<seealso cref="M:A.Test" />`.  
  
```  
// xml_seealso_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_seealso_tag.dll  
  
/// Text for class A.  
public ref struct A {  
   /// <summary><seealso cref="A::Test"/>  
   /// <seealso cref="B::Test"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void Test() {}  
};  
  
/// Text for class B.  
public ref struct B {  
   void Test() {}  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)