---
title: "&lt;seealso&gt; (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<seealso>"
  - "seealso"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<seealso> (etiqueta XML) [C++]"
  - "seealso (etiqueta XML) [C++]"
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;seealso&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<seealso\> permite especificar el texto que se desea que aparezca en una sección Vea también.  Utilice [\<see\>](../ide/see-visual-cpp.md) para especificar un vínculo desde dentro del texto.  
  
## Sintaxis  
  
```  
<seealso cref="member"/>  
```  
  
#### Parámetros  
 `member`  
 Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual.  Agregue el nombre entre comillas simples o dobles.  
  
 El compilador comprueba que el elemento de código especificado existe y resuelve `member` al nombre de elemento en la salida XML.  El compilador emite una advertencia si no encuentra `member`.  
  
 Para obtener información sobre cómo crear una referencia de tipo cref a un tipo genérico, vea [\<see\>](../ide/see-visual-cpp.md).  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
 Vea [\<summary\>](../ide/summary-visual-cpp.md) para obtener un ejemplo de \<seealso\>mediante.  
  
 El compilador de Visual C\+\+ intentará resolver referencias cref en un paso los comentarios de documentación.  Por consiguiente, si usa las reglas de búsqueda de C\+\+, un símbolo no encontrar por el compilador referencia se marcará como no resuelto.  
  
## Ejemplo  
 En el ejemplo siguiente, un símbolo no resuelto se hace referencia en un cref.  El comentario XML para el cref a B::Test se `<seealso cref="!:B::Test" />`, mientras que la referencia a A::Test es `<seealso cref="M:A.Test" />`correcto.  
  
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
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)