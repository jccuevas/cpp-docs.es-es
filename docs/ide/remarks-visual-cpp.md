---
title: "&lt;remarks&gt; (Visual C++) | Microsoft Docs"
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
  - "remarks"
  - "<remarks>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<remarks> (etiqueta XML) [C++]"
  - "remarks (etiqueta XML) [C++]"
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;remarks&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<remarks\> se utiliza para agregar información sobre un tipo, de modo que completa la información especificada con [\<summary\>](../ide/summary-visual-cpp.md).  Esta información se muestra en [Examinador de objetos](http://msdn.microsoft.com/es-es/f89acfc5-1152-413d-9f56-3dc16e3f0470) y en el informe web de comentarios de código.  
  
## Sintaxis  
  
```  
<remarks>description</remarks>  
```  
  
#### Parámetros  
 `description`  
 Descripción del miembro.  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
  
```  
// xml_remarks_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_remarks_tag.dll  
  
using namespace System;  
  
/// <summary>  
/// You may have some primary information about this class.  
/// </summary>  
/// <remarks>  
/// You may have some additional information about this class.  
/// </remarks>  
public ref class MyClass {};  
```  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)