---
title: _CrtMemDifference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 2d8cba0ada845e7e75bfe15945700a1385c8bcbb
ms.lasthandoff: 02/24/2017

---
# <a name="crtmemdifference"></a>_CrtMemDifference
Compara dos estados de memoria y devuelve sus diferencias (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stateDiff`  
 Puntero a una estructura de `_CrtMemState` que se usa para almacenar las diferencias entre los dos estados de memoria (devueltas).  
  
 `oldState`  
 Puntero a un estado de memoria anterior (estructura de`_CrtMemState` ).  
  
 `newState`  
 Puntero a un estado de memoria posterior (estructura de`_CrtMemState` ).  
  
## <a name="return-value"></a>Valor devuelto  
 Si los estados de memoria son significativamente distintos, `_CrtMemDifference` devuelve TRUE. De lo contrario, la función devuelve el FALSE.  
  
## <a name="remarks"></a>Comentarios  
 La función `_CrtMemDifference` compara `oldState` y `newState` , y almacena sus diferencias en `stateDiff`, que la aplicación puede usar para detectar pérdidas y otros problemas de memoria. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtMemDifference` se quitan durante el preprocesamiento.  
  
 `newState` y `oldState` deben ser punteros válidos a una estructura `_CrtMemState`, que se define en Crtdbg.h, que [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) ha rellenado antes de llamar a `_CrtMemDifference`. `stateDiff` debe ser un puntero a una instancia asignada previamente de la estructura de `_CrtMemState`. Si `stateDiff`, `newState` o `oldState` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en `EINVAL` y la función devuelve FALSE.  
  
 `_CrtMemDifference` compara los valores de campo de `_CrtMemState` de los bloques de `oldState` con los de `newState`, y almacena el resultado en `stateDiff`. Cuando el número de tipos de bloque asignados o el número total de bloques asignados para cada tipo no es igual en los dos estados de memoria, los estados se consideran significativamente diferentes. La diferencia entre la mayor cantidad que se haya asignado en algún momento simultáneamente a los dos estados y la diferencia entre las asignaciones totales a los dos estados también se almacenan en `stateDiff`.  
  
 De forma predeterminada, los bloques internos en tiempo de ejecución de C (`_CRT_BLOCK`) no se incluyen en las operaciones de estado de la memoria. Se puede usar la función [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) para activar el bit `_CRTDBG_CHECK_CRT_DF` de `_crtDbgFlag` de forma que incluya estos bloques en el proceso de detección de pérdidas y otras operaciones de estado de la memoria. Los bloques de memoria liberados (`_FREE_BLOCK`) no hacen que `_CrtMemDifference` devuelva TRUE.  
  
 Para obtener más información sobre las funciones de estado del montón y la estructura `_CrtMemState`, consulte [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_CrtMemDifference`|\<crtdbg.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** solo versiones de depuración de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)
