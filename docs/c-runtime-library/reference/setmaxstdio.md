---
title: "_setmaxstdio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_setmaxstdio"
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
  - "setmaxstdio"
  - "_setmaxstdio"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_setmaxstdio (función)"
  - "máximo de archivos abiertos"
  - "archivos abiertos, máxima"
  - "setmaxstdio (función)"
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _setmaxstdio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece un máximo para el número de archivos simultáneamente abierto en `stdio` normal.  
  
## Sintaxis  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### Parámetros  
 `newmax`  
 Nuevo máximo para el número de archivos simultáneamente abierto en `stdio` normal.  
  
## Valor devuelto  
 Devuelve `newmax` si correctamente; – 1 de otra manera.  
  
 Si `newmax` es menor que `_IOB_ENTRIES` o superior al número máximo de identificadores disponibles en el sistema operativo, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, esta función devuelve \-1 y establece `errno` a `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Los cambios de función de `_setmaxstdio` el valor máximo para el número de archivos que podrían ser simultáneamente abierto en `stdio` normal.  
  
 E\/S de tiempo de ejecución de C ahora admite muchos más archivos abiertos en plataformas Win32 que en versiones anteriores.  Hasta 2.048 archivos pueden abrir simultáneamente en [lowio level](../../c-runtime-library/low-level-i-o.md) \(es decir, abra y accesible mediante `_open`, `_read`, `_write`, etc. familia de las funciones de E\/S\).  Hasta 512 archivos pueden abrir simultáneamente en [stdio level](../../c-runtime-library/stream-i-o.md) \(es decir, abra y accesible mediante `fopen`, `fgetc`, `fputc`, etc. familia de funciones\).  El límite de 512 archivos abiertos en el nivel de `stdio` se puede aumentar hasta un máximo de 2.048 mediante la función de `_setmaxstdio` .  
  
 Dado que `stdio`\- funciones de nivel, como `fopen`, se compilan sobre las funciones de `lowio` , el máximo de 2.048 son un límite superior duro para el número de archivos simultáneamente abierto tiene acceso a través de la biblioteca en tiempo de ejecución de C.  
  
> [!NOTE]
>  Este límite superior puede estar más allá de lo admitida por una plataforma Win32 y una configuración determinada.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_setmaxstdio`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea [\_getmaxstdio](../../c-runtime-library/reference/getmaxstdio.md) para obtener un ejemplo de `_setmaxstdio`mediante.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)