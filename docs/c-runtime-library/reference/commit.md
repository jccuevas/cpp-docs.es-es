---
title: "_commit | Microsoft Docs"
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
  - "_commit"
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
  - "_commit"
  - "commit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_commit (función)"
  - "commit (función)"
  - "confirmar archivos en disco"
  - "archivos [C++], vaciar"
  - "vaciar archivos en disco"
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _commit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vacía un archivo directamente en el disco.  
  
## Sintaxis  
  
```  
int _commit(   
   int fd   
);  
```  
  
#### Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia al archivo abierto.  
  
## Valor devuelto  
 `_commit` devuelve 0 si el archivo se vaciado correctamente en el disco.  Un valor devuelto de – 1 indica un error.  
  
## Comentarios  
 La función de `_commit` fuerza el sistema operativo para escribir el archivo asociado a `fd` en el disco.  Esta llamada se garantiza que el archivo especificado está vaciado inmediatamente, no en la decisión del sistema operativo.  
  
 Si `fd` es descriptor de archivo no válido, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve \-1 y `errno` se establece en `EBADF`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`_commit`|\<io.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_read](../../c-runtime-library/reference/read.md)   
 [\_write](../../c-runtime-library/reference/write.md)