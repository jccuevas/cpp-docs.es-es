---
title: "malloc | Microsoft Docs"
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
  - "malloc"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "malloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "malloc (función)"
  - "asignación de memoria"
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigna bloques de memoria.  
  
## Sintaxis  
  
```  
void *malloc(  
   size_t size   
);  
```  
  
#### Parámetros  
 `size`  
 Bytes a asignar.  
  
## Valor devuelto  
 `malloc` devuelve un puntero void al espacio asignado, o `NULL` si no hay disponible memoria suficiente.  Para devolver un puntero a un tipo distinto de `void`, utilice una conversión de tipo en el valor devuelto.  El espacio de almacenamiento apuntado por el valor devuelto se garantiza para que se alinee adecuadamente para el almacenamiento de cualquier tipo de objeto que tiene un requisito de alineación inferior o igual al de la alineación fundamental. \(En Visual C\+\+, la alineación fundamental es la alineación necesaria para `double` u 8 bytes.  En el código destinado a plataformas de 64 bits, son 16 bytes\). Use [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) para asignar espacio de almacenamiento para los objetos que tienen un requisito de alineación mayor, por ejemplo, los tipos SSE [\_\_m128](../../cpp/m128.md) y `__m256`, y los tipos que se declaran con `__declspec(align(``n``))`, donde `n` es mayor que 8.  Si `size` es 0, `malloc` asigna un elemento de longitud cero en el montón y devuelve un puntero válido a ese elemento.  Compruebe siempre lo que devuelve `malloc`, aunque la cantidad de memoria solicitada sea pequeña.  
  
## Comentarios  
 La función `malloc` asigna un bloque de memoria de al menos `size` bytes.  Puede que el bloque tenga más de `size` bytes debido al espacio necesario para la información de mantenimiento y alineación.  
  
 `malloc` establece `errno` en `ENOMEM` si se produce un error al asignar una memoria o si la cantidad de memoria solicitada supera `_HEAP_MAXREQ`.  Para obtener más información sobre este y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 El código de inicio usa `malloc` para asignar el almacenamiento de las variables `_environ`, `envp` y `argv`.  Las siguientes funciones y sus equivalentes de caracteres anchos también llaman a `malloc`.  
  
|||||  
|-|-|-|-|  
|[calloc](../../c-runtime-library/reference/calloc.md)|[fscanf](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[\_getw](../../c-runtime-library/reference/getw.md)|[setvbuf](../../c-runtime-library/reference/setvbuf.md)|  
|[Funciones \_exec](../../c-runtime-library/exec-wexec-functions.md)|[fseek](../../c-runtime-library/reference/fseek-fseeki64.md)|[\_popen](../../c-runtime-library/reference/popen-wpopen.md)|[Funciones \_spawn](../../c-runtime-library/spawn-wspawn-functions.md)|  
|[fgetc](../../c-runtime-library/reference/fgetc-fgetwc.md)|[fsetpos](../../c-runtime-library/reference/fsetpos.md)|[printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[\_strdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)|  
|[\_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md)|[\_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[putc](../../c-runtime-library/reference/putc-putwc.md)|[sistema](../../c-runtime-library/reference/system-wsystem.md)|  
|[fgets](../../c-runtime-library/reference/fgets-fgetws.md)|[fwrite](../../c-runtime-library/reference/fwrite.md)|[putchar](../../c-runtime-library/reference/putc-putwc.md)|[\_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](../../c-runtime-library/reference/getc-getwc.md)|[\_putenv](../../c-runtime-library/reference/putenv-wputenv.md)|[ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md)|  
|[fputc](../../c-runtime-library/reference/fputc-fputwc.md)|[getchar](../../c-runtime-library/reference/getc-getwc.md)|[coloca](../../c-runtime-library/reference/puts-putws.md)|[vfprintf](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[\_fputchar](../../c-runtime-library/reference/fputc-fputwc.md)|[\_getcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[\_putw](../../c-runtime-library/reference/putw.md)|[vprintf](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|  
|[fputs](../../c-runtime-library/reference/fputs-fputws.md)|[\_getdcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)||  
|[fread](../../c-runtime-library/reference/fread.md)|[obtiene](../../c-runtime-library/gets-getws.md)|[\_searchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)||  
  
 La función [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) de C\+\+ establece el nuevo modo de controlador para `malloc`.  El nuevo modo de controlador indica si, en caso de error, `malloc` debe llamar a la nueva rutina de controlador como se establece por [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md).  De forma predeterminada, `malloc` no llama a la nueva rutina del controlador si no se puede asignar memoria.  Puede invalidar este comportamiento predeterminado para que, cuando `malloc` no puede asignar memoria, `malloc` llama a la nueva rutina de controlador de la misma manera que hace el operador `new` cuando produce errores por la misma razón.  Para reemplazar el valor predeterminado, llame  
  
```cpp  
_set_new_mode(1)  
```  
  
 al principio del programa, o vincularlo con NEWMODE.OBJ \(vea [Opciones de vínculo](../../c-runtime-library/link-options.md)\).  
  
 Cuando la aplicación está vinculada con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `malloc` se resuelve en [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md).  Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, vea [Detalles del montón de depuración de CRT](../Topic/CRT%20Debug%20Heap%20Details.md).  
  
 `malloc` se marca como `__declspec(noalias)` y `__declspec(restrict)`; esto significa que hay garantías de que la función no modifica variables globales y de que no se ha creado un alias para el puntero devuelto.  Para obtener más información, vea [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`malloc`|\<stdlib.h\> y \<malloc.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```c  
// crt_malloc.c  
// This program allocates memory with  
// malloc, then frees the memory with free.  
  
#include <stdlib.h>   // For _MAX_PATH definition  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   char *string;  
  
   // Allocate space for a path name  
   string = malloc( _MAX_PATH );  
  
   // In a C++ file, explicitly cast malloc's return.  For example,   
   // string = (char *)malloc( _MAX_PATH );  
  
   if( string == NULL )  
      printf( "Insufficient memory available\n" );  
   else  
   {  
      printf( "Memory space allocated for path name\n" );  
      free( string );  
      printf( "Memory freed\n" );  
   }  
}  
```  
  
  **Espacio de memoria asignado para el nombre de ruta de acceso**  
**Memoria liberada**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)