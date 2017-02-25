---
title: "_umask_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_umask_s"
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
  - "unmask_s"
  - "_umask_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_umask_s (función)"
  - "permisos de archivo [C++]"
  - "archivos [C++], configuración de permisos para"
  - "máscaras"
  - "máscaras, file-permission-setting"
  - "umask_s (función)"
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _umask_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece la máscara predeterminada de los permisos de archivo.  Una versión de [\_umask](../../c-runtime-library/reference/umask.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _umask_s(  
   int mode,  
   int * pOldMode  
);  
```  
  
#### Parámetros  
 \[in\] `mode`  
 Valor de permisos predeterminado.  
  
 \[out\] `oldMode`  
 El valor anterior de la configuración de permisos.  
  
## Valor devuelto  
 Devuelve un código de error si `Mode` no especifica un modo válido o el puntero de `pOldMode` es `NULL`.  
  
### Condiciones de error  
  
|`mode`|`pOldMode`|**Valor devuelto**|**Contents of**  `oldMode`|  
|------------|----------------|------------------------|--------------------------------|  
|any|`NULL`|`EINVAL`|no modificado|  
|modo no válido|any|`EINVAL`|no modificado|  
  
 Si una de las condiciones anteriores se produce, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_umask_s` devuelve `EINVAL` y establece `errno` en `EINVAL`.  
  
## Comentarios  
 La función de `_umask_s` establece la máscara de archivo del proceso actual el modo especificado por *`mode`.* La máscara de archivo modifica la configuración de permisos nuevos archivos creados por `_creat`, `_open`, o `_sopen`.  Si un bit de la máscara es 1, el bit correspondiente en el valor solicitado de permiso del archivo se establece en 0 \(denegado\).  Si un bit de la máscara es 0, el bit correspondiente permanece sin cambios.  La configuración de permisos para un nuevo archivo no se establece hasta que se cierra el archivo por primera vez.  
  
 La expresión de entero `pmode` contiene una o ambas de las constantes de manifiesto siguientes, definidos en SYS\\STAT.H:  
  
 `_S_IWRITE`  
 Escribir permitida.  
  
 `_S_IREAD`  
 Lectura permitida.  
  
 `_S_IREAD | _S_IWRITE`  
 Lectura y escritura permitidas.  
  
 Cuando se dan ambas constantes, se combinan con bit a bit\- OR el operador \(          `|`  \).  Si el argumento de `mode` es `_S_IREAD`, la lectura no se permite \(el archivo es de sólo escritura\).  Si el argumento de `mode` es `_S_IWRITE`, escribir no se permite \(el archivo es de sólo lectura\).  Por ejemplo, si el bit de escritura se establece en la máscara, cualquier nuevo archivo será de sólo lectura.  Observe que con MS\-DOS y los sistemas operativos Windows, todos los archivos son legibles; no es posible asignar el permiso de solo escritura.  Por consiguiente, establecer la lectura mordida con `_umask_s` no tiene ningún efecto en los modos de archivo.  
  
 Si `pmode` no es una combinación de una de las constantes de manifiesto ni escribir un conjunto alternas de constantes, la función omitirá los.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_umask_s`|\<io.h y\> sistema \<\/stat.h y sistema\> \/types.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_umask_s.c  
/* This program uses _umask_s to set  
 * the file-permission mask so that all future  
 * files will be created as read-only files.  
 * It also displays the old mask.  
 */  
  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask, err;  
  
   /* Create read-only files: */  
   err = _umask_s( _S_IWRITE, &oldmask );  
   if (err)  
   {  
      printf("Error setting the umask.\n");  
      exit(1);  
   }  
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
 [\_umask](../../c-runtime-library/reference/umask.md)