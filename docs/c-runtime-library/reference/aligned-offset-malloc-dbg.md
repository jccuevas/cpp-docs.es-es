---
title: _aligned_offset_malloc_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 67f314989e0069902ae983805a4f8ce839307ea5
ms.lasthandoff: 02/24/2017

---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg
Asigna memoria en un límite de alineación especificado (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void * _aligned_offset_malloc_dbg(  
   size_t size,   
   size_t alignment,   
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `size`  
 Tamaño de la asignación de memoria solicitada.  
  
 [in] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 [in] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
 [in] `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor NULL.  
  
 [in] `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero al bloque de memoria que se asignó o `NULL` si se produjo un error en la operación.  
  
## <a name="remarks"></a>Comentarios  
 La función `_aligned_offset_malloc_dbg` es una versión de depuración de la función [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md). Si no se define [_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_offset_malloc_dbg` se reduce a una llamada a `_aligned_offset_malloc`. `_aligned_offset_malloc` y `_aligned_offset_malloc_dbg` asignan un bloque de memoria del montón base, pero `_aligned_offset_malloc_dbg` proporciona varias características de depuración: búferes situados a cada lado de la parte del usuario del bloque en el que se va a comprobar si hay pérdidas, un parámetro de tipo de bloque para realizar el seguimiento de tipos de asignación concretos, así como información sobre `filename`/`linenumber` para determinar el origen de las solicitudes de asignación.  
  
 `_aligned_offset_malloc_dbg` asigna el bloque de memoria con un poco más de espacio que el `size` solicitado. El administrador del montón de depuración usa el espacio adicional para vincular los bloques de memoria de depuración, y para proporcionar a la aplicación información de encabezado de depuración y sobrescribir los búferes. Cuando se asigna el bloque, la parte del usuario de bloque se rellena con el valor 0xCD y cada uno de los búferes sobrescritos se rellena con 0xFD.  
  
 `_aligned_offset_malloc_dbg` es útil en situaciones en las que la alineación se necesita en un elemento anidado, por ejemplo si se necesitara la alineación en una clase anidada.  
  
 `_aligned_offset_malloc_dbg` se basa en `malloc`. Para obtener más información, consulte [malloc](../../c-runtime-library/reference/malloc.md).  
  
 Esta función establece `errno` en `ENOMEM` si se produce un error en la asignación de memoria o si el tamaño solicitado es mayor que `_HEAP_MAXREQ`. Para obtener más información sobre `errno`, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Además, `_aligned_offset_malloc` valida sus parámetros. Si `alignment` no es una potencia de 2, o `offset` es mayor o igual que `size` y distinto de cero, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `NULL` y establece `errno` en `EINVAL`.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_offset_malloc_dbg`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
