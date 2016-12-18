---
title: "Constantes de mont&#243;n | Microsoft Docs"
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
  - "_HEAPBADPTR"
  - "_HEAPEMPTY"
  - "_HEAPBADBEGIN"
  - "_HEAPOK"
  - "_HEAPBADNODE"
  - "_HEAPEND"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_HEAPBADBEGIN (constantes)"
  - "_HEAPBADNODE (constantes)"
  - "_HEAPBADPTR (constantes)"
  - "_HEAPEMPTY (constantes)"
  - "_HEAPEND (constantes)"
  - "_HEAPOK (constantes)"
  - "constantes de montón"
  - "HEAPBADBEGIN (constantes)"
  - "HEAPBADNODE (constantes)"
  - "HEAPBADPTR (constantes)"
  - "HEAPEMPTY (constantes)"
  - "HEAPEND (constantes)"
  - "HEAPOK (constantes)"
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes de mont&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <malloc.h>  
  
```  
  
## Comentarios  
 Estas constantes proporcionan el valor devuelto que indica el estado de la pila.  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_HEAPBADBEGIN`|La información de encabezado inicial no se encuentra o no está no válida.|  
|`_HEAPBADNODE`|El nodo incorrecta se encontró, o está dañado la pila.|  
|`_HEAPBADPTR`|el campo de**\_pentry** de la estructura de **\_HEAPINFO** no contiene el puntero válido en la pila \(rutina de`_heapwalk` solo\).|  
|`_HEAPEMPTY`|Pila no se ha inicializado.|  
|`_HEAPEND`|Al final de la pila se tuvo acceso correctamente \(rutina de`_heapwalk` solo\).|  
|`_HEAPOK`|La pila es coherente \(`_heapset` y rutinas de `_heapchk` solo\).  Ningún error hasta ahora; la estructura de **\_HEAPINFO** contiene información sobre la entrada siguiente \(rutina de`_heapwalk` solo\).|  
  
## Vea también  
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapset](../c-runtime-library/heapset.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)