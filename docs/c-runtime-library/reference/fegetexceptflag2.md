---
title: "fegetexceptflag2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fegetexceptflag"
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
  - "fegetexceptflag"
  - "fenv/fegetexceptflag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fegetexceptflag (función)"
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# fegetexceptflag
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Almacena el estado actual de las marcas de excepción de punto flotante especificado.  
  
## Sintaxis  
  
```  
int fegetexceptflag(   
   fexcept_t* pstatus,   
   int excepts   
);  
  
```  
  
#### Parámetros  
 `pstatus`  
 Un puntero a un `fexcept_t` objeto que contiene los valores actuales de las marcas de excepción especificados por `excepts`.  
  
 `excepts`  
 Las marcas de excepción de punto flotante para almacenar en `pstatus`.  
  
## Valor devuelto  
 Si se ejecuta correctamente, devuelve 0. De lo contrario, devuelve un valor distinto de cero.  
  
## Comentarios  
 El `fegetexceptflag` función almacena el estado actual de las marcas de estado de excepción de punto flotante especificado por `excepts` en la `fexcept_t` objeto señalado por `pstatus`.`pstatus` debe apuntar a una `fexcept_t` objeto o comportamiento subsiguiente es indefinido. El `fegetexceptflag` función admite estas macros de excepción, definidas en \< fenv.h \>:  
  
|Macros de excepción|Descripción|  
|-------------------------|-----------------|  
|FE\_DIVBYZERO|Se produjo un error de singularidad o polo en una operación punto flotante anteriormente; se creó un valor infinito.|  
|FE\_INEXACT|Se forzó la función redondear el resultado de una operación de punto flotante anteriormente almacenado.|  
|FE\_INVALID|Se produjo un error de dominio en una operación de punto flotante anteriormente.|  
|FE\_OVERFLOW|Se produjo un error de intervalo; un resultado de la operación de punto flotante anterior era demasiado grande para representarse.|  
|FE\_UNDERFLOW|Un resultado de la operación de punto flotante anterior era demasiado pequeño para representarlo en toda la precisión; se creó un valor desnormalizados.|  
|FE\_ALLEXCEPT|La operación OR bit a bit de todos los admite excepciones de punto flotante.|  
  
 El `excepts` argumento puede ser cero, una de las macros de excepción de punto flotante compatibles o bit a bit o de dos o más de las macros. El efecto de cualquier otro valor del argumento es indefinido.  
  
 Para utilizar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante el uso de la `#pragma fenv_access(on)` Directiva antes de la llamada. Para obtener más información, consulta [fenv\_access](../../preprocessor/fenv-access.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fegetexceptflag`|\<fenv.h\>|\<cfenv\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)