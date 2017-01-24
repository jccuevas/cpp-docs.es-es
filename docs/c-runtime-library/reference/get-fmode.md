---
title: "_get_fmode | Microsoft Docs"
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
  - "_get_fmode"
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
  - "get_fmode"
  - "_get_fmode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_fmode (función)"
  - "traducción de archivos [C++], modo predeterminado"
  - "get_fmode (función)"
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_fmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el archivo predeterminado de modalidad de traducción para operaciones de E\/S de archivos.  
  
## Sintaxis  
  
```  
errno_t _get_fmode(   
   int * pmode   
);  
```  
  
#### Parámetros  
 \[out\] `pmode`  
 Un puntero a un entero que se rellenará con el modo predeterminado actual: `_O_TEXT` o `_O_BINARY`.  
  
## Valor devuelto  
 Devuelve cero si correctamente; un código de error del error.  Si `pmode` es `NULL`, se invoca el controlador no válido del parámetro tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EINVAL`.  
  
## Comentarios  
 La función obtiene el valor de la variable global de [\_fmode](../../c-runtime-library/fmode.md) .  Esta variable especifica el archivo predeterminado de modalidad de traducción para las operaciones de E\/S de bajo nivel y de la secuencia de archivo, como `_open`, `_pipe`, `fopen`, y `freopen`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_get_fmode`|\<stdlib.h\>|\<fcntl.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo de [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md).  
  
## Equivalente de .NET Framework  
 No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_fmode](../../c-runtime-library/fmode.md)   
 [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [E\/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md)