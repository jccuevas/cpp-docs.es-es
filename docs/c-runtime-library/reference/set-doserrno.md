---
title: "_set_doserrno | Microsoft Docs"
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
  - "_set_doserrno"
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
  - "_set_doserrno"
  - "set_doserrno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_doserrno (variable global)"
  - "_set_doserrno (función)"
  - "doserrno (variable global)"
  - "set_doserrno (función)"
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_doserrno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el valor de la variable global de [\_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .  
  
## Sintaxis  
  
```  
errno_t _set_doserrno(   
   int value   
);  
```  
  
#### Parámetros  
 \[in\] `value`  
 Nuevo valor de `_doserrno`.  
  
## Valor devuelto  
 Devuelve cero si correctamente.  
  
## Comentarios  
 Los valores posibles se definen en Errno.h.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_set_doserrno`|\<stdlib.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [\_get\_doserrno](../../c-runtime-library/reference/get-doserrno.md)   
 [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)