---
title: "&lt;para&gt; (Visual C++) | Microsoft Docs"
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
  - "<para>"
  - "para"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<para> (etiqueta XML) [C++]"
  - "para (etiqueta XML) [C++]"
ms.assetid: 35f2a1b3-bc14-4f13-bcb0-c39ccbf74d59
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;para&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La etiqueta \<para\> se utiliza dentro de otra etiqueta, tal como [\<summary\>](../ide/summary-visual-cpp.md), [\<remarks\>](../ide/remarks-visual-cpp.md) o [\<returns\>](../ide/returns-visual-cpp.md), y permite dar una estructura al texto.  
  
## Sintaxis  
  
```  
<para>content</para>  
```  
  
#### Parámetros  
 `content`  
 Texto del párrafo.  
  
## Comentarios  
 Compile con el parámetro [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para procesar los comentarios de documentación y generar un archivo con ellos.  
  
## Ejemplo  
 Vea [\<summary\>](../ide/summary-visual-cpp.md) para obtener un ejemplo del uso de \<para\>.  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)