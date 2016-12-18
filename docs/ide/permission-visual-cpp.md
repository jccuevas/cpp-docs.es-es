---
title: "&lt;permission&gt; (Visual C++) | Microsoft Docs"
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
  - "permission"
  - "<permission>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<permission> (etiqueta XML) [C++]"
  - "permission (etiqueta XML) [C++]"
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;permission&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<permission\> permite documentar el acceso de un miembro.  <xref:System.Security.PermissionSet> permite especificar el acceso a un miembro.  
  
## Sintaxis  
  
```  
<permission cref="member">description</permission>  
```  
  
#### Parámetros  
 `member`  
 Referencia a un miembro o campo al cual se puede llamar desde el entorno de compilación actual.  El compilador comprueba si el elemento de código dado existe y traduce `member` al nombre de elemento canónico en el resultado XML.  Agregue el nombre entre comillas simples o dobles.  
  
 El compilador emite una advertencia si no encuentra `member`.  
  
 Para obtener información sobre cómo crear una referencia de tipo cref a un tipo genérico, vea [\<see\>](../ide/see-visual-cpp.md).  
  
 `description`  
 Descripción del acceso al miembro.  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
 El compilador de Visual C\+\+ intentará resolver referencias cref en un paso los comentarios de documentación.  Por consiguiente, si usa las reglas de búsqueda de C\+\+, un símbolo no encontrar por el compilador referencia se marcará como no resuelto.  Para obtener más información, consulte [\<seealso\>](../ide/seealso-visual-cpp.md).  
  
## Ejemplo  
  
```  
// xml_permission_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_permission_tag.dll  
using namespace System;  
/// Text for class TestClass.  
public ref class TestClass {  
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>  
   void Test() {}  
};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)