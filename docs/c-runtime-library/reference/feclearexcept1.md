---
title: "feclearexcept | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "feclearexcept"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "feclearexcept"
  - "fenv/feclearexcept"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "feclearexcept (función)"
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# feclearexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Intenta borrar las marcas de excepción de punto flotante especificadas por el argumento.  
  
## Sintaxis  
  
```  
int feclearexcept(  
   int excepts  
);  
```  
  
#### Parámetros  
 `excepts`  
 Los indicadores de estado de excepción para borrar.  
  
## Valor devuelto  
 Devuelve cero si `excepts` es cero, o si se ha borrado correctamente todas las excepciones especificadas. De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 El `feclearexcept` función intenta borrar flotante punto indicadores de estado de excepción especificados por `excepts`. La función admite estas macros de excepción definidas en fenv.h:  
  
|Macros de excepción|Descripción|  
|-------------------------|-----------------|  
|FE\_DIVBYZERO|Se produjo un error de singularidad o polo en una operación punto flotante anteriormente; se creó un valor infinito.|  
|FE\_INEXACT|Se forzó la función redondear el resultado de una operación de punto flotante anteriormente almacenado.|  
|FE\_INVALID|Se produjo un error de dominio en una operación de punto flotante anteriormente.|  
|FE\_OVERFLOW|Se produjo un error de intervalo; un resultado de la operación de punto flotante anterior era demasiado grande para representarse.|  
|FE\_UNDERFLOW|Un resultado de la operación de punto flotante anterior era demasiado pequeño para representarlo en toda la precisión; se creó un valor desnormalizados.|  
|FE\_ALLEXCEPT|La operación OR bit a bit de todos los admite excepciones de punto flotante.|  
  
 El `excepts` argumento puede ser cero o el OR bit a bit de uno o más de las macros de excepción admitidas. El resultado de cualquier otro valor del argumento es indefinido.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`feclearexcept`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)