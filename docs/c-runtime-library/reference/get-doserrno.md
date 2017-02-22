---
title: "_get_doserrno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_doserrno"
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
  - "_get_doserrno"
  - "get_doserrno"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_doserrno (función)"
  - "get_doserrno (función)"
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _get_doserrno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene un valor de error del sistema operativo antes de traducirse a un valor `errno`.  
  
## Sintaxis  
  
```  
errno_t _get_doserrno(     int * pValue  );   
```  
  
#### Parámetros  
 \[out\] `pValue`  
 Puntero a un entero que se va a rellenar con el valor actual de la macro global `_doserrno`.  
  
## Valor devuelto  
 Si `_get_doserrno` es correcto, devuelve cero; si no, devuelve un código de error.  Si `pValue` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
## Comentarios  
 La macro global `_doserrno` se establece en cero durante la inicialización de CRT, antes de que la ejecución del proceso comience.  Se establece en el valor de error de sistema operativo devuelto por una llamada de función de nivel de sistema que devuelve un error de sistema operativo, y nunca se restablece a cero durante la ejecución.  Cuando escriba código para comprobar el valor de error devuelto por una función, borre siempre `_doserrno` mediante [\_set\_doserrno](../../c-runtime-library/reference/set-doserrno.md) antes de la llamada de función.  Dado que existe la posibilidad de que otra llamada de función sobrescriba `_doserrno`, compruebe el valor usando `_get_doserrno` inmediatamente después de la llamada de función.  
  
 Recomendamos usar [\_get\_errno](../../c-runtime-library/reference/get-errno.md) en vez de `_get_doserrno` para los códigos de error portables.  
  
 Los posibles valores de `_doserrno` se definen en \<errno.h\>.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_get_doserrno`|\<stdlib.h\>, \<cstdlib\> \(C\+\+\)|\<errno.h\>, \<cerrno\> \(C\+\+\)|  
  
 `_get_doserrno` es una extensión de Microsoft.  Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [\_set\_doserrno](../../c-runtime-library/reference/set-doserrno.md)   
 [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)