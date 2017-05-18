---
title: _msize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _msize
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- msize
- _msize
dev_langs:
- C++
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
caps.latest.revision: 12
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
ms.openlocfilehash: f669b35ab67ff08835e3335f702027d61581b868
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="msize"></a>_msize
Devuelve el tamaño de un bloque de memoria asignado en el montón.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      size_t _msize(  
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `memblock`  
 Puntero al bloque de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 `_msize` devuelve el tamaño (en bytes) de un entero sin signo.  
  
## <a name="remarks"></a>Comentarios  
 La función `_msize` devuelve el tamaño, en bytes, del bloque de memoria asignado por una llamada a `calloc`, `malloc` o `realloc`.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, `_msize` se resuelve como [_msize_dbg](../../c-runtime-library/reference/msize-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Esta función valida su parámetro. Si `memblock` es un puntero nulo, `_msize` invoca a un controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se controla el error, la función establece `errno` en `EINVAL` y devuelve -1.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_msize`|\<malloc.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [realloc](../../c-runtime-library/reference/realloc.md).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [_expand](../../c-runtime-library/reference/expand.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)
