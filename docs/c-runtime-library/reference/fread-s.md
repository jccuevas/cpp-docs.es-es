---
title: fread_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fread_s
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
- fread_s
- stdio/fread_s
dev_langs:
- C++
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fedb1419b3558fc773933619de247cfd3685e06
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="freads"></a>fread_s
Lee datos desde una secuencia. Esta versión de [fread](../../c-runtime-library/reference/fread.md) incluye mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t fread_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Ubicación de almacenamiento de los datos.  
  
 `bufferSize`  
 Tamaño del búfer de destino en bytes.  
  
 `elementSize`  
 Tamaño del elemento que se va a leer en bytes.  
  
 `count`  
 Número máximo de elementos que se va a leer.  
  
 `stream`  
 Puntero a la estructura `FILE` .  
  
## <a name="return-value"></a>Valor devuelto  
 `fread_s` devuelve el número de elementos (completos) que se han leído en el búfer, que puede ser menor que `count` si se encuentra un error de lectura o el final del archivo antes de llegar a `count`. Use la función `feof` o `ferror` para distinguir una condición de error de una condición de final de archivo. Si `size` o `count` es 0, `fread_s` devuelve 0 y el contenido del búfer queda sin cambios. Si `stream` o `buffer` es un puntero nulo, `fread_s` invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece `errno` en `EINVAL` y devuelve 0.  
  
 Para obtener más información sobre códigos de error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `fread_s` lee hasta `count` elementos de `elementSize` bytes en la entrada `stream` y los almacena en `buffer`.  El puntero de archivo asociado a `stream` (si lo hay) se incrementa según el número de bytes leídos realmente. Si la secuencia especificada se abre en modo de texto, pares de avance de línea de retorno de carro se reemplazan por caracteres de avance de línea única. Este reemplazo no tiene ningún efecto en el puntero de archivo ni en el valor devuelto. Si se produce un error, la posición del puntero de archivo es indeterminada. No se puede determinar el valor de un elemento leído parcialmente.  
  
 Esta función bloquea otros subprocesos. Si necesita una versión que no sea de bloqueo, use `_fread_nolock`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fread_s`|\<stdio.h>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// crt_fread_s.c  
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c  
//  
// This program opens a file that's named FREAD.OUT and  
// writes characters to the file. It then tries to open  
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
#define BUFFERSIZE 30  
#define DATASIZE 22  
#define ELEMENTCOUNT 2  
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)  
#define FILENAME "FREAD.OUT"  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   for ( i = 0; i < DATASIZE; i++ )  
      list[i] = (char)('z' - i);  
   list[DATASIZE] = '\0'; // terminal null so we can print it  
  
   // Open file in text mode:  
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )  
   {  
      // Write DATASIZE characters to stream   
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );  
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );  
      printf( "Wrote %d items\n\n", numwritten );  
      fclose( stream );  
   } else {  
      printf( "Problem opening the file\n" );  
      return -1;  
   }  
  
   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {  
      // Attempt to read in characters in 2 blocks of 11  
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );  
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );  
      printf( "Contents of buffer after write/read:\n\t%s\n", list );  
      fclose( stream );  
   } else {  
      printf( "File could not be opened\n" );  
      return -1;  
   }  
}  
```  
  
```Output  
Contents of buffer before write/read:   
        zyxwvutsrqponmlkjihgfe  
  
Wrote 22 items  
  
Number of 11-byte elements read = 2  
  
Contents of buffer after write/read:   
        zyxwvutsrqponmlkjihgfe  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [_read](../../c-runtime-library/reference/read.md)