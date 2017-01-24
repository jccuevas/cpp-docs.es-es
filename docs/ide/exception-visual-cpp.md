---
title: "&lt;exception&gt; (Visual C++) | Microsoft Docs"
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
  - "exception"
  - "<exception>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<exception> (etiqueta XML) [C++]"
  - "exception (etiqueta XML) [C++]"
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;exception&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<exception\> permite especificar las excepciones que se pueden producir.  Esta etiqueta se aplica a una definición de método.  
  
## Sintaxis  
  
```  
<exception cref="member">description</exception>  
```  
  
#### Parámetros  
 `member`  
 Referencia a una excepción disponible desde el entorno de compilación actual.  Mediante reglas de búsqueda del nombre, el compilador comprueba que la excepción especificada existe, y convierte `member` al nombre de elemento canónico en la salida XML.  El compilador emite una advertencia si no encuentra `member`.  
  
 Agregue el nombre entre comillas simples o dobles.  
  
 Para obtener información sobre cómo crear una referencia de tipo cref a un tipo genérico, vea [\<see\>](../ide/see-visual-cpp.md).  
  
 `description`  
 Descripción.  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
 El compilador de Visual C\+\+ intentará resolver referencias cref en un paso los comentarios de documentación.  Por consiguiente, si usa las reglas de búsqueda de C\+\+, un símbolo no encontrar por el compilador referencia se marcará como no resuelto.  Para obtener más información, consulte [\<seealso\>](../ide/seealso-visual-cpp.md).  
  
## Ejemplo  
  
```  
// xml_exception_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_exception_tag.dll  
using namespace System;  
  
/// Text for class EClass.  
public ref class EClass : public Exception {  
   // class definition ...  
};  
  
/// <exception cref="System.Exception">Thrown when... .</exception>  
public ref class TestClass {  
   void Test() {  
      try {  
      }  
      catch(EClass^) {  
      }  
   }  
};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)