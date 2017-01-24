---
title: "PAGE | Microsoft Docs"
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
  - "PAGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Page directive"
ms.assetid: 6654c094-c1f7-4d10-8d9d-902ddd1ac27e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# PAGE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La primera directiva establece la *longitud* de línea y *el ancho* de caracteres de la lista de programa.  Si no se especifica ningún argumento, genera un salto de página.  La segunda directiva aumenta el número de sección y restablece el número de página en 1.  
  
## Sintaxis  
  
```  
  
      PAGE [[[[length]], width]]  
PAGE +  
```  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)