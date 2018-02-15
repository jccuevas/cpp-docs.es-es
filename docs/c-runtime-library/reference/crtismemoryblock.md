---
title: _CrtIsMemoryBlock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtIsMemoryBlock
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
apitype: DLLExport
f1_keywords:
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
dev_langs:
- C++
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58faccd95e831dd264910abf063529db12701bf6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock
Comprueba que un bloque de memoria especificado está en el montón local y que tiene un identificador válido de tipo de bloque del montón de depuración (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _CrtIsMemoryBlock(   
   const void *userData,  
   unsigned int size,  
   long *requestNumber,  
   char **filename,  
   int *linenumber   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `userData`  
 Puntero al principio del bloque de memoria que se va a comprobar.  
  
 [in] `size`  
 Tamaño del bloque especificado, en bytes.  
  
 [out] `requestNumber`  
 Puntero al número de asignación del bloque o `NULL`.  
  
 [out] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó el bloque o `NULL`.  
  
 [out] `linenumber`  
 Puntero al número de línea del archivo de código fuente o `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 `_CrtIsMemoryBlock` devuelve `TRUE` si el bloque de memoria especificado está en el montón local y tiene un identificador válido de tipo de bloque del montón de depuración; de lo contrario, la función devuelve `FALSE`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtIsMemoryBlock` comprueba que un bloque de memoria especificado está en el montón local de la aplicación y que tiene un identificador de tipo de bloque válido. Esta función también se puede usar para obtener el número de orden de la asignación de objetos, y el nombre y el número de línea del archivo de código fuente en el que se solicitó la asignación del bloque de memoria originalmente. Si se pasan valores no nulos para los parámetros `requestNumber`, `filename` o `linenumber`, `_CrtIsMemoryBlock` establece estos parámetros en los valores del encabezado de depuración del bloque de memoria, si encuentra el bloque en el montón local. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtIsMemoryBlock` se quitan durante el preprocesamiento.  
  
 Si `_CrtIsMemoryBlock` produce un error, devuelve `FALSE` y los parámetros de salida se inicializan con los valores predeterminados: `requestNumber` y `lineNumber` se establecen en 0 y `filename` se establece en `NULL`.  
  
 Dado que esta función devuelve `TRUE` o `FALSE`, se puede pasar a una de las macros [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) para crear un mecanismo sencillo de control de errores de depuración. En el ejemplo siguiente se genera un error de aserción si la dirección especificada no se está en el montón local:  
  
```  
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,   
&filename, &linenumber ) );  
```  
  
 Para obtener más información sobre cómo usar `_CrtIsMemoryBlock` con otras macros y funciones de depuración, consulte [Macros para los informes](/visualstudio/debugger/macros-for-reporting). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtIsMemoryBlock`|\<crtdbg.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo del tema [_CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)