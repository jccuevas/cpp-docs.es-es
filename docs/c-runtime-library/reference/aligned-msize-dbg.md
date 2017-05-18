---
title: _aligned_msize_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 5a924af887defa6473c4fa8c8beeccb1d27b1411
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg
Devuelve el tamaño de un bloque de memoria asignado en el montón (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `memblock`  
 Puntero al bloque de memoria.  
  
 [in] `alignment`  
 Valor de la alineación, que debe ser un entero potencia de 2.  
  
 [in] `offset`  
 Desplazamiento en la asignación de memoria para imponer la alineación.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño (en bytes) de un entero sin signo.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de `alignment` y `offset` deben ser iguales que los valores que se pasan a la función que asignó el bloque.  
  
 La función `_aligned_msize_dbg` es una versión de depuración de la función [_aligned_msize](../../c-runtime-library/reference/aligned-msize.md). Si no se define [_DEBUG](../../c-runtime-library/debug.md), cada llamada a `_aligned_msize_dbg` se reduce a una llamada a `_aligned_msize`. `_aligned_msize` y `_aligned_msize_dbg` calculan el tamaño de un bloque de memoria del montón base, pero `_aligned_msize_dbg` agrega una característica de depuración: incluye los búferes situados en cada extremo de la parte del usuario del bloque de memoria en el tamaño que devuelve.  
  
 Esta función valida su parámetro. Si `memblock` es un puntero nulo o `alignment` no es una potencia de 2, `_msize` invoca a un controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se controla el error, la función establece `errno` en `EINVAL` y devuelve -1.  
  
 Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre la asignación de tipos de bloque y cómo se usan, consulte [Tipos de bloques en el montón de depuración](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre las diferencias entre llamar a una función estándar del montón y su versión de depuración en una compilación de depuración de una aplicación, consulte [Versiones de depuración de las funciones de asignación del montón](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_aligned_msize_dbg`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)
