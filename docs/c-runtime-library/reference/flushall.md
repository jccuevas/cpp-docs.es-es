---
title: _flushall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _flushall
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
- _flushall
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 230d52cf98e7dc563ea5d0067de7df31af8549f9
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="flushall"></a>_flushall
Vacía todos los flujos y borra todos los búferes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _flushall( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 `_flushall` devuelve el número de flujos abiertos (entrada y salida). No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, la función `_flushall` escribe en los archivos correspondientes el contenido de todos los búferes asociados a los flujos de salida abiertos. Se borra el contenido actual de todos los búferes asociados a los flujos de entrada abiertos. Normalmente, el sistema operativo mantiene estos búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra un flujo o cuando un programa finaliza con normalidad sin cerrar flujos.  
  
 Si una lectura sigue a una llamada a `_flushall`, se insertan más datos de los archivos de entrada en los búferes. Todos los flujos permanecen abiertos después de la llamada a `_flushall`.  
  
 La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escribe directamente en el disco y no en los búferes del sistema operativo. Sin tener que volver a escribir un programa existente, puede habilitar esta característica vinculando los archivos objeto del programa a Commode.obj. En el archivo ejecutable resultante, las llamadas a `_flushall` escriben el contenido de todos los búferes en el disco. Commode.obj solo afecta a `_flushall` y `fflush`.  
  
 Para obtener información sobre cómo controlar la característica de confirmación en disco, consulte [E/S de secuencia](../../c-runtime-library/stream-i-o.md), [fopen](../../c-runtime-library/reference/fopen-wfopen.md) y [_fdopen](../../c-runtime-library/reference/fdopen-wfdopen.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_flushall`|\<stdio.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_flushall.c  
// This program uses _flushall  
// to flush all open buffers.  
  
#include <stdio.h>  
  
int main( void )  
{  
   int numflushed;  
  
   numflushed = _flushall();  
   printf( "There were %d streams flushed\n", numflushed );  
}  
```  
  
```Output  
There were 3 streams flushed  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_commit](../../c-runtime-library/reference/commit.md)   
 [fclose, _fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)
