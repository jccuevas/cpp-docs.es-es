---
title: "/LINKERMEMBER | Microsoft Docs"
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
  - "/linkermember"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LINKERMEMBER (opción de dumpbin)"
  - "LINKERMEMBER (opción de dumpbin)"
  - "-LINKERMEMBER (opción de dumpbin)"
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LINKERMEMBER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LINKERMEMBER[:{1|2}]  
```  
  
## Comentarios  
 Esta opción muestra los símbolos públicos definidos en una biblioteca.  Para mostrar los símbolos por orden de objetos, junto con sus desplazamientos, debe especificar el argumento 1.  Para mostrar desplazamientos y números de índice de objetos, y después mostrar los símbolos en orden alfabético, junto con el índice de objeto para cada símbolo, especifique el argumento 2.  Si desea obtener los dos resultados, especifique \/LINKERMEMBER sin el argumento numérico.  
  
 En los archivos producidos con la opción de compilador [\/GL](../../build/reference/gl-whole-program-optimization.md) sólo está disponible la opción [\/HEADERS](../../build/reference/headers.md) de DUMPBIN.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)