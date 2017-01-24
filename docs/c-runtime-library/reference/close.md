---
title: "_close | Microsoft Docs"
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
  - "_close"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_close"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_close (función)"
  - "close (función)"
  - "archivos [C++], cerrar"
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cerrar un archivo.  
  
## Sintaxis  
  
```  
int _close(   
   int fd   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia al archivo abierto.  
  
## Valor devuelto  
 `_close` devuelve 0 si el archivo se cerró correctamente.  Un valor devuelto de – 1 indica un error.  
  
## Comentarios  
 La función de `_close` cierra el archivo asociado a `fd`.  
  
 Descriptor de archivo y el identificador de archivo subyacente de SO cerrados.  Por tanto, no es necesario llamar a `CloseHandle` si se ha abierto el archivo mediante la función `CreateFile` de Win32 y convertir originalmente descriptor de archivo mediante `_open_osfhandle`.  
  
 Esta función valida sus parámetros.  Si `fd` es un archivo dañado descriptor, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven \-1 y `errno` se establece en `EBADF`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_close`|\<io.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [\_open](../../c-runtime-library/reference/open-wopen.md).  
  
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_dup, \_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_unlink, \_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)