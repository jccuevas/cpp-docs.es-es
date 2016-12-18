---
title: "&lt;see&gt; (Visual C++) | Microsoft Docs"
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
  - "<see>"
  - "see"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<see> (etiqueta XML) [C++]"
  - "see (etiqueta XML) [C++]"
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;see&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<see\> permite especificar un vínculo desde dentro del texto.  Uso [\<seealso\>](../ide/seealso-visual-cpp.md) para indicar el texto que quizás desee que aparezcan en la sección vea también.  
  
## Sintaxis  
  
```  
<see cref="member"/>  
```  
  
#### Parámetros  
 `member`  
 Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual.  Agregue el nombre entre comillas simples o dobles.  
  
 El compilador comprueba que el elemento de código especificado existe y resuelve `member` al nombre de elemento en la salida XML.  El compilador emite una advertencia si no encuentra `member`.  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
 Vea [\<summary\>](../ide/summary-visual-cpp.md) para obtener un ejemplo de \<see\>mediante.  
  
 El compilador de Visual C\+\+ intentará resolver referencias cref en un paso los comentarios de documentación.  Por consiguiente, si usa las reglas de búsqueda de C\+\+, un símbolo no encontrar por el compilador referencia se marcará como no resuelto.  Para obtener más información, consulte [\<seealso\>](../ide/seealso-visual-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo crear referencia cref a un tipo genérico, de modo que, el compilador resolverá la referencia.  
  
```  
// xml_see_cref_example.cpp  
// compile with: /LD /clr /doc  
// the following cref shows how to specify the reference, such that,  
// the compiler will resolve the reference  
/// <see cref="C{T}">  
/// </see>  
ref class A {};  
  
// the following cref shows another way to specify the reference,   
// such that, the compiler will resolve the reference  
/// <see cref="C < T >"/>  
  
// the following cref shows how to hard-code the reference  
/// <see cref="T:C`1">  
/// </see>  
ref class B {};  
  
/// <see cref="A">  
/// </see>  
/// <typeparam name="T"></typeparam>  
generic<class T>  
ref class C {};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)