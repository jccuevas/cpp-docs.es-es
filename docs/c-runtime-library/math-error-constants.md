---
title: "Constantes de error matem&#225;tico | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_PLOSS"
  - "_UNDERFLOW"
  - "_TLOSS"
  - "_SING"
  - "_DOMAIN"
  - "_OVERFLOW"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_DOMAIN (constante)"
  - "_OVERFLOW (constante)"
  - "_PLOSS (constante)"
  - "_SING (constante)"
  - "_TLOSS (constante)"
  - "_UNDERFLOW (constante)"
  - "DOMAIN (constante)"
  - "constantes de error matemático"
  - "OVERFLOW (constante)"
  - "PLOSS (constante)"
  - "SING (constante)"
  - "TLOSS (constante)"
  - "UNDERFLOW (constante)"
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Constantes de error matem&#225;tico
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <math.h>  
  
```  
  
## Comentarios  
 Las rutinas matemáticas de la biblioteca en tiempo de ejecución pueden generar constantes de error matemáticas.  
  
 Estos errores, descritos como sigue, corresponden a los tipos de excepción definidos en MATH.H y se devolverán por la función de `_matherr` cuando un error math aparece.  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_DOMAIN`|El argumento a trabajar es dominio fuera de la función.|  
|`_OVERFLOW`|El resultado es demasiado grande para representarlo en el tipo de valor devuelto de la función.|  
|`_PLOSS`|Pérdida de significado parcial grave.|  
|`_SING`|Singularidad de argumento: el argumento a trabajar tiene valor no válido. \(Por ejemplo, se pasa el valor 0 para trabajar que requiere un valor distinto de cero.\)|  
|`_TLOSS`|Pérdida total de significado grave.|  
|`_UNDERFLOW`|El resultado es demasiado pequeño para ser representado.|  
  
## Vea también  
 [\_matherr](../c-runtime-library/reference/matherr.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)