---
title: "Constantes de uso compartido | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_SH_DENYNO"
  - "_SH_DENYRD"
  - "_SH_DENYRW"
  - "_SH_DENYWR"
  - "_SH_COMPAT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_SH_COMPAT (constante)"
  - "_SH_DENYNO (constante)"
  - "_SH_DENYRD (constante)"
  - "_SH_DENYRW (constante)"
  - "_SH_DENYWR (constante)"
  - "SH_COMPAT (constante)"
  - "SH_DENYNO (constante)"
  - "SH_DENYRD (constante)"
  - "SH_DENYRW (constante)"
  - "SH_DENYWR (constante)"
  - "compartir constantes"
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Constantes de uso compartido
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Constantes de los modos de uso compartido de archivos.  
  
## Sintaxis  
  
```  
  
#include <share.h>  
  
```  
  
## Comentarios  
 El argumento *de shflag* determina el modo compartido, que se compone de una o varias constantes del manifiesto.  Éstos se pueden combinar con argumentos de *oflag* \(vea [Constantes de archivo](../c-runtime-library/file-constants.md)\).  
  
 La tabla siguiente muestra las constantes y sus significados:  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_SH_DENYRW`|Deniega el acceso de lectura y escritura al archivo|  
|`_SH_DENYWR`|Deniega el acceso de escritura al archivo|  
|`_SH_DENYRD`|Deniega el acceso de lectura al archivo|  
|`_SH_DENYNO`|Permite el acceso de lectura y escritura|  
|`_SH_SECURE`|Los conjuntos garantizan el modo \(lectura compartida, acceso de escritura exclusivo\).|  
  
## Vea también  
 [\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_fsopen, \_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)