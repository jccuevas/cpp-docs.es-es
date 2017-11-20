---
title: _getw | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _getw
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
f1_keywords: _getw
dev_langs: C++
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d5cf5147f3225c9cd5c6f0c91d60bcaeb75b188
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="getw"></a>_getw
Obtiene un entero de una secuencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _getw(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## <a name="return-value"></a>Valor devuelto  
 `_getw` devuelve el valor entero leído. Un valor devuelto de `EOF` indica un error o el final del archivo. Pero, como el valor `EOF` también es un valor entero legítimo, puede usar `feof` o `ferror` para comprobar una condición de error o de final de archivo. Si `stream` es `NULL`, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EOF`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_getw` lee el siguiente valor binario de tipo `int` desde el archivo asociado a `stream` y aumenta el puntero del archivo asociado (si hay alguno) para señalar al siguiente carácter no leído. `_getw` no supone ninguna alineación especial de elementos en la secuencia. Se pueden producir problemas de portabilidad con `_getw` porque el tamaño del tipo `int` y el orden de bytes en el tipo `int` son distintos en los sistemas.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_getw`|\<stdio.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_getw.c  
// This program uses _getw to read a word  
// from a stream, then performs an error check.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   int i;  
  
   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )  
      printf( "Couldn't open file\n" );  
   else  
   {  
      // Read a word from the stream:  
      i = _getw( stream );  
  
      // If there is an error...  
      if( ferror( stream ) )  
      {  
         printf( "_getw failed\n" );  
         clearerr_s( stream );  
      }  
      else  
         printf( "First data word in file: 0x%.4x\n", i );  
      fclose( stream );  
   }  
}  
```  
  
## <a name="input-crtgetwtxt"></a>Entrada: crt_getw.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Resultado  
  
```  
First data word in file: 0x656e694c  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_putw](../../c-runtime-library/reference/putw.md)