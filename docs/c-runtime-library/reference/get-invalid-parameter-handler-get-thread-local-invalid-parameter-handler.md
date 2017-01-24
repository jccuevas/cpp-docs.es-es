---
title: "_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler | Microsoft Docs"
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
  - "_get_invalid_parameter_handler"
  - "_get_thread_local_invalid_parameter_handler"
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
  - "_get_invalid_parameter_handler"
  - "stdlib/_get_invalid_parameter_handler"
  - "_get_thread_local_invalid_parameter_handler"
  - "stdlib/_get_thread_local_invalid_parameter_handler"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "_get_thread_local_invalid_parameter_handler (función)"
  - "_get_invalid_parameter_handler (función)"
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la función que se llama cuando el CRT detecta un argumento no válido.  
  
## Sintaxis  
  
```  
_invalid_parameter_handler _get_invalid_parameter_handler(void);  
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);  
```  
  
## Valor devuelto  
 Un puntero a establecido actualmente la función de controlador de parámetros no válidos o un puntero null si no se ha establecido.  
  
## Comentarios  
 El `_get_invalid_parameter_handler` función obtiene el controlador de parámetros no válidos global. Devuelve un puntero nulo si se ha establecido ningún controlador global de parámetro no válido. De forma similar, la `_get_thread_local_invalid_parameter_handler` Obtiene el controlador de parámetros no válidos de subproceso local actual del subproceso se llama en, o un puntero null si se ha establecido ningún controlador. Para obtener información acerca de cómo establecer controladores globales y locales de subproceso parámetros no válidos, consulte [\_set\_invalid\_parameter\_handler, \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).  
  
 El puntero de función de controlador de parámetro no válido devuelto tiene el siguiente tipo:  
  
```c  
typedef void (__cdecl* _invalid_parameter_handler)(  
    wchar_t const*,  
    wchar_t const*,  
    wchar_t const*,   
    unsigned int,  
    uintptr_t  
    );  
```  
  
 Para obtener más información sobre el controlador de parámetros no válidos, consulte el prototipo en [\_set\_invalid\_parameter\_handler, \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_invalid_parameter_handler`, `_get_thread_local_invalid_parameter_handler`|C: \< stdlib.h \><br /><br /> C\+\+: \< cstdlib \> o \< stdlib.h \>|  
  
 El `_get_invalid_parameter_handler` y `_get_thread_local_invalid_parameter_handler` funciones son específicos de Microsoft. Para obtener información de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [\_set\_invalid\_parameter\_handler, \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)   
 [Versiones de funciones de CRT con seguridad mejorada](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)