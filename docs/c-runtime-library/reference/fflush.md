---
title: fflush | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fflush
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
- fflush
dev_langs:
- C++
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: f2a11a29ba0eec3c66cf23f72e8fe0e7106d5a5c
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="fflush"></a>fflush
Vacía una secuencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fflush(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` .  
  
## <a name="return-value"></a>Valor devuelto  
 `fflush` devuelve 0 si el búfer se ha vaciado correctamente. También se devuelve el valor 0 en los casos en que la secuencia especificada no tiene ningún búfer o solo se abre para lectura. Un valor devuelto de `EOF` indica un error.  
  
> [!NOTE]
>  Si `fflush` devuelve `EOF`, es posible que se hayan perdido datos debido a un error de escritura. Al configurar un controlador de errores críticos, resulta más seguro desactivar el almacenamiento en búfer con la función `setvbuf` o usar rutinas de E/S de bajo nivel, como `_open`, `_close` y `_write`, en lugar de las funciones de E/S de secuencia.  
  
## <a name="remarks"></a>Comentarios  
 La función `fflush` vacía la secuencia `stream`. Si la secuencia se ha abierto en modo de escritura, o se ha abierto en modo de actualización y la última operación ha sido una operación de escritura, el contenido del búfer de la secuencia se escribe en el archivo o dispositivo subyacentes y el búfer se descarta. Si la secuencia se ha abierto en modo de lectura, o no tiene ningún búfer, la llamada a `fflush` no tiene ningún efecto y no se conserva ningún búfer. Una llamada a `fflush` anula el efecto de cualquier llamada anterior a `ungetc` en la secuencia. La secuencia sigue abierta después de la llamada.  
  
 Si `stream` es `NULL`, el comportamiento es igual al de una llamada a `fflush` en cada secuencia abierta. Se vacían todas las secuencias abiertas en modo de escritura y en modo de actualización en las que la última operación ha sido de escritura. La llamada no tiene ningún efecto en otras secuencias.  
  
 Normalmente, el sistema operativo mantiene los búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra una secuencia o cuando un programa finaliza con normalidad sin cerrar la secuencia. La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escriben directamente en el disco y no en los búferes del sistema operativo. Sin tener que volver a escribir un programa existente, puede habilitar esta característica vinculando los archivos objeto del programa a COMMODE.OBJ. En el archivo ejecutable resultante, las llamadas a `_flushall` escriben el contenido de todos los búferes en el disco. COMMODE.OBJ solo afecta a `_flushall` y `fflush`.  
  
 Para obtener información sobre cómo controlar la característica de confirmación en disco, consulte [E/S de secuencia](../../c-runtime-library/stream-i-o.md), [fopen](../../c-runtime-library/reference/fopen-wfopen.md) y [_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md).  
  
 Esta función bloquea el subproceso de llamada y por lo tanto es segura para subprocesos. Para consultar una versión que no realiza el bloqueo, vea `_fflush_nolock`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fflush`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_fflush.c  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int integer;  
   char string[81];  
  
   // Read each word as a string.  
   printf( "Enter a sentence of four words with scanf: " );  
   for( integer = 0; integer < 4; integer++ )  
   {  
      scanf_s( "%s", string, sizeof(string) );        
      printf( "%s\n", string );  
   }  
  
   // You must flush the input buffer before using gets.   
   // fflush on input stream is an extension to the C standard   
   fflush( stdin );     
   printf( "Enter the same sentence with gets: " );  
   gets_s( string, sizeof(string) );  
   printf( "%s\n", string );  
}  
```  
  
```Output  
  
      This is a test  
This is a test  
  
```  
  
```Output  
  
      This is a test  
This is a testEnter a sentence of four words with scanf: This is a test  
This  
is  
a  
test  
Enter the same sentence with gets: This is a test  
This is a test  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)
