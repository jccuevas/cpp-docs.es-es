---
title: "_set_errno | Microsoft Docs"
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
  - "_set_errno"
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
  - "set_errno"
  - "_set_errno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_errno (función)"
  - "errno (variable global)"
  - "set_errno (función)"
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_errno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establezca el valor de la variable global de `errno` .  
  
## Sintaxis  
  
```  
errno_t _set_errno(   
   int value   
);  
```  
  
#### Parámetros  
 \[in\] `value`  
 Nuevo valor de `errno`.  
  
## Valor devuelto  
 Devuelve cero si correctamente.  
  
## Comentarios  
 Los valores posibles se definen en Errno.h.  Vea también [errno \(Constantes\)](../../c-runtime-library/errno-constants.md).  
  
## Ejemplo  
  
```  
// crt_set_errno.c  
#include <stdio.h>  
#include <errno.h>  
  
int main()  
{  
   _set_errno( EILSEQ );  
   perror( "Oops" );  
}  
```  
  
  **Oops: Secuencia no válida de byte**   
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_set_errno`|\<stdlib.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [\_get\_errno](../../c-runtime-library/reference/get-errno.md)   
 [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)