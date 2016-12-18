---
title: "___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "___mb_cur_max_l_func"
  - "__p___mb_cur_max"
  - "___mb_cur_max_func"
  - "__mb_cur_max"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "___mb_cur_max_func"
  - "___mb_cur_max_l_func"
  - "__p___mb_cur_max"
  - "__mb_cur_max"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___mb_cur_max_func"
  - "___mb_cur_max_l_func"
  - "__mb_cur_max"
  - "__p___mb_cur_max"
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Función de CRT interna.  Recupera el número máximo de bytes en un carácter multibyte de la configuración local actual o especificada.  
  
## Sintaxis  
  
```cpp  
int ___mb_cur_max_func(void); int ___mb_cur_max_l_func(_locale_t locale); int * __p___mb_cur_max(void); #define __mb_cur_max (___mb_cur_max_func())  
```  
  
#### Parámetros  
 configuración regional  
 Estructura de configuración local de la que obtener los resultados.  Si este valor es nulo, se usa la configuración regional de subproceso actual.  
  
## Valor devuelto  
 Número máximo de bytes en un carácter multibyte de la configuración local de subproceso actual o de la configuración local especificada.  
  
## Comentarios  
 Se trata de una función interna que CRT usa para recuperar el valor actual de la macro [MB\_CUR\_MAX](../c-runtime-library/mb-cur-max.md) del almacenamiento local de subprocesos.  Le recomendamos usar la macro `MB_CUR_MAX` en su código de cara a la portabilidad.  
  
 La macro `__mb_cur_max` constituye una forma muy cómoda de llamar a la función `___mb_cur_max_func()`.  La función `__p___mb_cur_max` se define para la compatibilidad con Visual C\+\+ 5.0 y versiones anteriores.  
  
 Las funciones de CRT internas son específicas de la implementación y están sujetas a cambio en cada versión.  Se desaconseja usarlas en el código.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h\>, \<stdlib.h\>|  
  
## Vea también  
 [MB\_CUR\_MAX](../c-runtime-library/mb-cur-max.md)