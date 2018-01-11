---
title: ftell, _ftelli64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ftelli64
- ftell
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftelli64
- ftell
dev_langs: C++
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: df0feee9beb2b2fc5144974f1fc06ff2b8d02b80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ftell-ftelli64"></a>ftell, _ftelli64
Obtiene la posición actual de un puntero de archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
long ftell(   
   FILE *stream   
);  
__int64 _ftelli64(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Estructura `FILE` de destino.  
  
## <a name="return-value"></a>Valor devuelto  
 `ftell` y `_ftelli64` devuelven la posición de archivo actual. El valor devuelto por `ftell` y `_ftelli64` pueden no reflejar el desplazamiento de bytes físico para las secuencias que se abre en modo de texto, porque el modo de texto hace que la traducción de avance de línea de retorno de carro. Use `ftell` con `fseek` o `_ftelli64` con `_fseeki64` para volver a ubicaciones de archivos correctamente. En caso de error, `ftell` y `_ftelli64` invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1 L y establecen `errno` a uno de dos constantes, definidas en ERRNO. H. La constante `EBADF` indica que el argumento `stream` no es un valor de puntero de archivo válido o no hace referencia a un archivo abierto. `EINVAL` indica que se ha pasado un argumento `stream` no válido a la función. En dispositivos que no pueden realizar búsquedas (como terminales e impresoras) o cuando `stream` no hace referencia a un archivo abierto, el valor devuelto es indefinido.  
  
 Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## <a name="remarks"></a>Comentarios  
 El `ftell` y `_ftelli64` funciones recuperan la posición actual del puntero de archivo (si existe) asociada a `stream`. La posición se expresa como un desplazamiento en relación con el principio del flujo.  
  
 Tenga en cuenta que cuando un archivo se abre para anexar datos, la posición de archivo actual se determina con la última operación de E/S, no en función de dónde se produciría la siguiente escritura. Por ejemplo, si un archivo se abre para anexar y la última operación fue de lectura, la posición de archivo es el punto donde empezaría la siguiente operación de lectura, no donde empezaría la siguiente escritura. (Cuando se abre un archivo para anexar, la posición de archivo se mueve al final del archivo antes de cualquier operación de escritura). Si todavía no se ha producido ninguna operación de E/S en un archivo abierto para anexar, la posición de archivo se sitúa al principio del archivo.  
  
 En modo de texto, CTRL+Z se interpreta como un carácter de final de archivo en la entrada. En archivos abiertos para lectura/escritura, `fopen` y todas las rutinas relacionadas buscan un CTRL+Z al final del archivo y, si es posible, lo eliminan. Se hace así porque el uso de `ftell` y `fseek` o `_ftelli64` y `_fseeki64` para desplazarse por un archivo que finaliza con un CTRL+Z puede hacer que `ftell` o `_ftelli64` se comporten de forma incorrecta cerca del final del archivo.  
  
 Esta función bloquea el subproceso de llamada durante la ejecución y por lo tanto es segura para subprocesos. Para consultar una versión que no realiza el bloqueo, vea `_ftell_nolock`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|Encabezados opcionales|  
|--------------|---------------------|----------------------|  
|`ftell`|\<stdio.h>|\<errno.h>|  
|`_ftelli64`|\<stdio.h>|\<errno.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_ftell.c  
// This program opens a file named CRT_FTELL.C  
// for reading and tries to read 100 characters. It  
// then uses ftell to determine the position of the  
// file pointer and displays this position.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long position;  
   char list[100];  
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )  
   {  
      // Move the pointer by reading data:   
      fread( list, sizeof( char ), 100, stream );  
      // Get position after read:   
      position = ftell( stream );  
      printf( "Position after trying to read 100 bytes: %ld\n",  
              position );  
      fclose( stream );  
   }  
}  
```  
  
```Output  
Position after trying to read 100 bytes: 100  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek, _lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)