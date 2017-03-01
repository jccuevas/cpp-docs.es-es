---
title: _CrtDumpMemoryLeaks | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 11
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 3fca6935525d9654c7f78f81e879497fc3e0e5af
ms.lasthandoff: 02/24/2017

---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks
Vuelca todos los bloques de memoria del montón de depuración cuando se ha producido una fuga de memoria (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 `_CrtDumpMemoryLeaks` devuelve TRUE si se encuentra una pérdida de memoria. De lo contrario, la función devuelve el FALSE.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtDumpMemoryLeaks` determina si se ha producido una pérdida de memoria desde que se inició la ejecución del programa. Cuando se encuentra una pérdida, la información de encabezado de depuración de todos los objetos del montón se vuelca en un formato legible para usuario. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtDumpMemoryLeaks` se quitan durante el preprocesamiento.  
  
 A menudo, se llama a `_CrtDumpMemoryLeaks` al final de la ejecución del programa para comprobar que se ha liberado toda la memoria asignada por la aplicación. Se puede llamar a la función automáticamente cuando finaliza el programa activando el campo de bits `_CRTDBG_LEAK_CHECK_DF` de la marca [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) mediante la función [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md).  
  
 `_CrtDumpMemoryLeaks` llama a [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) para obtener el estado actual del montón y luego examina el estado para detectar bloques que no se hayan liberado. Cuando se encuentra un bloque no liberado, `_CrtDumpMemoryLeaks` llama a [_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) para volcar la información de todos los objetos asignados en el montón desde que se inició la ejecución del programa.  
  
 De forma predeterminada, los bloques internos en tiempo de ejecución de C (`_CRT_BLOCK`) no se incluyen en las operaciones de volcado de la memoria. Se puede usar la función [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) para activar el bit `_CRTDBG_CHECK_CRT_DF` de `_crtDbgFlag` de forma que incluya estos bloques en el proceso de detección de pérdidas.  
  
 Para obtener más información sobre las funciones de estado del montón y la estructura `_CrtMemState`, consulte [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de cómo usar `_CrtDumpMemoryLeaks`, consulte [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
