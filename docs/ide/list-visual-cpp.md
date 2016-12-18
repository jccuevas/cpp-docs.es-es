---
title: "&lt;list&gt; (Visual C++) | Microsoft Docs"
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
  - "list"
  - "<list>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<list> (etiqueta XML) [C++]"
  - "list (etiqueta XML) [C++]"
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;list&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El bloque \<listheader\> se utiliza para definir la fila de encabezado de una tabla o de una lista de definiciones.  Cuando se define una tabla, sólo es necesario suministrar una entrada para un término en el encabezado.  
  
## Sintaxis  
  
```  
<list type="bullet" | "number" | "table">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### Parámetros  
 `term`  
 Término que se define en `description`.  
  
 `description`  
 Elemento de una lista numerada o con viñetas, o definición de un `term`.  
  
## Comentarios  
 Cada elemento de la lista se especifica con un bloque \<item\>.  Cuando se crea una lista de definiciones, se deberán especificar tanto `term` como `description`.  Sin embargo, para una tabla, lista con viñetas o lista numerada, sólo es necesario suministrar una entrada para `description`.  
  
 Una lista o una tabla pueden tener tantos bloques \<item\> como sean necesarios.  
  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
  
```  
// xml_list_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_list_tag.dll  
/// <remarks>Here is an example of a bulleted list:  
/// <list type="bullet">  
/// <item>  
/// <description>Item 1.</description>  
/// </item>  
/// <item>  
/// <description>Item 2.</description>  
/// </item>  
/// </list>  
/// </remarks>  
class MyClass {};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)