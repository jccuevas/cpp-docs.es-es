---
title: "_creat, _wcreat | Microsoft Docs"
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
  - "_creat"
  - "_wcreat"
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
  - "wcreat"
  - "_wcreat"
  - "_creat"
  - "tcreat"
  - "_tcreat"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcreat (función)"
  - "_wcreat (función)"
  - "archivos [C++], crear"
  - "_creat (función)"
  - "tcreat (función)"
  - "creat (función)"
  - "_tcreat (función)"
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _creat, _wcreat
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crear un archivo nuevo.  están desusadas`_creat` y `_wcreat` ; uso [\_sopen\_s, \_wsopen\_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md) en su lugar.  
  
## Sintaxis  
  
```  
int _creat(   
   const char *filename,  
   int pmode   
);  
int _wcreat(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### Parámetros  
 `filename`  
 Nombre del nuevo archivo.  
  
 `pmode`  
 Configuración de permisos.  
  
## Valor devuelto  
 Estas funciones, si son correctas, devuelven descriptor de archivo al archivo creado.  Si no, las funciones devuelven – 1 y `errno` establecido como se muestra en la tabla siguiente.  
  
|Valor de `errno`|Descripción|  
|----------------------|-----------------|  
|`EACCES`|`filename` especifica un archivo de sólo lectura existente o especifica un directorio en lugar de un archivo.|  
|`EMFILE`|No más de descriptores de archivo están disponibles.|  
|`ENOENT`|El archivo especificado no se encontró.|  
  
 Si `filename` es NULL, estas funciones se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_creat` crea un nuevo archivo o se abre y trunca existente.  `_wcreat` es una versión con caracteres anchos de `_creat`; el argumento `filename` para `_wcreat` es una cadena de caracteres anchos.  Por lo demás, `_wcreat` y `_creat` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcreat`|`_creat`|`_creat`|`_wcreat`|  
  
 Si no existe el archivo especificado por `filename` , un nuevo archivo se crea con la configuración de permisos especificada y se abrirá para escribir.  Si el archivo ya existe y la configuración de permisos permite escribir, `_creat` trunca el archivo a la longitud 0, destruyendo el contenido anteriores, y lo abre para escribir.  La configuración de permisos, `pmode`, se aplica a archivos creados recientemente únicamente.  El nuevo archivo recibe la configuración de permisos especificada después de cerrar por primera vez.  La expresión de entero `pmode` contiene una o ambas de las constantes del manifiesto `_S_IWRITE` y `_S_IREAD`, definido en SYS\\Stat.h.  Cuando se dan ambas constantes, se combinan con el operador bit a bit de `OR` \(  **&#124;**\).  El parámetro de `pmode` se establece en uno de los valores siguientes.  
  
|Valor|Definición|  
|-----------|----------------|  
|`_S_IWRITE`|Escribir permitida.|  
|`_S_IREAD`|Lectura permitida.|  
|`_S_IREAD &#124; _S_IWRITE`|Lectura y escritura permitidas.|  
  
 Si el permiso de escritura no se especifica, el archivo es de sólo lectura.  Todos los archivos siempre son legibles; no se puede asignar el permiso de solo escritura.  Los modos `_S_IWRITE` y `_S_IREAD``| _S_IWRITE` constituyen equivalentes.  Los archivos abiertos mediante `_creat` se abren siempre en modo de compatibilidad \(vea [\_sopen](../../c-runtime-library/reference/sopen-wsopen.md)\) con `_SH_DENYNO`.  
  
 `_creat` aplica la máscara actual de los permisos de archivo a `pmode` antes de establecer los permisos \(vea [\_umask](../../c-runtime-library/reference/umask.md)\).  `_creat` se proporciona principalmente para la compatibilidad bibliotecas anteriores.  Una llamada a `_open` con `_O_CREAT` y a `_O_TRUNC` en el parámetro de `oflag` es equivalente a `_creat` y es preferible para el nuevo código.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_creat`|\<io.h\>|\<sistema\/types.h, sistema\>\<\/stat.h, errno.h\>\<\>|  
|`_wcreat`|\<io.h o\> wchar.h \<\>|\<sistema\/types.h, sistema\>\<\/stat.h, errno.h\>\<\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_creat.c  
// compile with: /W3  
// This program uses _creat to create  
// the file (or truncate the existing file)  
// named data and open it for writing.  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int fh;  
  
   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996  
   // Note: _creat is deprecated; use _sopen_s instead  
   if( fh == -1 )  
      perror( "Couldn't create data file" );  
   else  
   {  
      printf( "Created data file.\n" );  
      _close( fh );  
   }  
}  
```  
  
  **Archivo de datos creado.**   
## Vea también  
 [E\/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod, \_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_dup, \_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_sopen, \_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [\_umask](../../c-runtime-library/reference/umask.md)