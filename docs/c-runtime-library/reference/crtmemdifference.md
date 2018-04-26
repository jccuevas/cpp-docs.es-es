---
title: _CrtMemDifference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: 27fb436c438daac7415ba3c0e7581611414c9c4a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="crtmemdifference"></a>_CrtMemDifference

Compara dos estados de memoria y devuelve sus diferencias (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>Parámetros

*stateDiff*<br/>
Puntero a un **_CrtMemState** estructura que se utiliza para almacenar las diferencias entre los dos Estados de memoria (devueltas).

*oldState*<br/>
Puntero a un estado de memoria anterior (**_CrtMemState** estructura).

*newState*<br/>
Puntero a un estado de memoria posterior (**_CrtMemState** estructura).

## <a name="return-value"></a>Valor devuelto

Si los Estados de memoria son significativamente distintos, **_CrtMemDifference** devuelve TRUE. De lo contrario, la función devuelve el FALSE.

## <a name="remarks"></a>Comentarios

El **_CrtMemDifference** función compara *oldState* y *newState* y almacena sus diferencias en *stateDiff*, lo que puede, a continuación, utilizará la aplicación para detectar pérdidas de memoria y otros problemas de memoria. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtMemDifference** se quitan durante el preprocesamiento.

*newState* y *oldState* cada uno debe ser un puntero válido a una **_CrtMemState** estructura, definida en Crtdbg.h, que ha sido rellenada por [_CrtMemCheckpoint](crtmemcheckpoint.md)antes de llamar a **_CrtMemDifference**. *stateDiff* debe ser un puntero a una instancia asignada previamente de la **_CrtMemState** estructura. Si *stateDiff*, *newState*, o *oldState* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) está establecido en **EINVAL** y la función devuelve FALSE.

**_CrtMemDifference** compara el **_CrtMemState** campo valores de los bloques de *oldState* a los de *newState* y almacena el resultado en *stateDiff*. Cuando el número de tipos de bloque asignados o el número total de bloques asignados para cada tipo no es igual en los dos estados de memoria, los estados se consideran significativamente diferentes. La diferencia entre la mayor cantidad que se haya asignado a la vez a los dos Estados y la diferencia entre las asignaciones totales a los dos Estados también se almacenan en *stateDiff*.

De forma predeterminada, los bloques de tiempo de ejecución de C internos (**_CRT_BLOCK**) no se incluyen en las operaciones de estado de memoria. El [_CrtSetDbgFlag](crtsetdbgflag.md) función puede utilizarse para activar el **_CRTDBG_CHECK_CRT_DF** de bits de **_crtDbgFlag** para incluir estos bloques de detección de pérdidas y otro estado de memoria operaciones. Bloques de memoria liberados (**_FREE_BLOCK**) no se realiza **_CrtMemDifference** devuelva TRUE.

Para obtener más información sobre las funciones de estado del montón y la **_CrtMemState** estructura, vea [funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** solo versiones de depuración de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
