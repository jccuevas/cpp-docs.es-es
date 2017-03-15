---
title: "_umask | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_umask"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_umask"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_umask (función)"
  - "permisos de archivo [C++]"
  - "archivos [C++], configuración de permisos para"
  - "máscaras"
  - "máscaras, file-permission-setting"
  - "umask (función)"
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _umask
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece la máscara predeterminada de los permisos de archivo.  Una versión más segura de esta función está disponible; vea [\_umask\_s](../../c-runtime-library/reference/umask-s.md).  
  
## Sintaxis  
  
```  
int _umask(  
   int pmode   
);  
```  
  
#### Parámetros  
 `pmode`  
 Valor de permisos predeterminado.  
  
## Valor devuelto  
 `_umask` devuelve el valor anterior de `pmode`.  No se devuelve ningún error.  
  
## Comentarios  
 La función de `_umask` establece la máscara de archivo del proceso actual el modo especificado por *`pmode`.* La máscara de archivo modifica la configuración de permisos nuevos archivos creados por `_creat`, `_open`, o `_sopen`.  Si un bit de la máscara es 1, el bit correspondiente en el valor solicitado de permiso del archivo se establece en 0 \(denegado\).  Si un bit de la máscara es 0, el bit correspondiente permanece sin cambios.  La configuración de permisos para un nuevo archivo no se establece hasta que se cierra el archivo por primera vez.  
  
 La expresión de entero `pmode` contiene una o ambas de las constantes de manifiesto siguientes, definidos en SYS\\STAT.H:  
  
 `_S_IWRITE`  
 Escribir permitida.  
  
 `_S_IREAD`  
 Lectura permitida.  
  
 `_S_IREAD | _S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Cuando se dan ambas constantes, se combinan con bit a bit\- OR el operador \(          `|`  \).  Si el argumento de `pmode` es `_S_IREAD`, la lectura no se permite \(el archivo es de sólo escritura\).  Si el argumento de `pmode` es `_S_IWRITE`, escribir no se permite \(el archivo es de sólo lectura\).  Por ejemplo, si el bit de escritura se establece en la máscara, cualquier nuevo archivo será de sólo lectura.  Observe que con MS\-DOS y los sistemas operativos Windows, todos los archivos son legibles; no es posible asignar el permiso de solo escritura.  Por consiguiente, establecer la lectura mordida con `_umask` no tiene ningún efecto en los modos de archivo.  
  
 Si `pmode` no es una combinación de una de las constantes de manifiesto ni escribir un conjunto alternas de constantes, la función omitirá los.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_umask`|\<io.h, sistema\>\<\/stat.h, sistema\/\>types.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_umask.c  
// compile with: /W3  
// This program uses _umask to set  
// the file-permission mask so that all future  
// files will be created as read-only files.  
// It also displays the old mask.  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask;  
  
   /* Create read-only files: */  
   oldmask = _umask( _S_IWRITE ); // C4996  
   // Note: _umask is deprecated; consider using _umask_s instead  
   printf( "Oldmask = 0x%.4x\n", oldmask );  
}  
```  
  
  **Oldmask \= 0x0000**   
## Equivalente en .NET Framework  
 [System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod, \_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_creat, \_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_mkdir, \_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)