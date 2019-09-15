---
title: _CrtMemDifference
ms.date: 11/04/2016
api_name:
- _CrtMemDifference
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtMemDifference
- CrtMemDifference
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: 51bfa014d54f55843fcb112f318f143774abf8f3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938708"
---
# <a name="_crtmemdifference"></a>_CrtMemDifference

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
Puntero a una estructura _ **crtmemstate** que se usa para almacenar las diferencias entre los dos Estados de memoria (devueltos).

*oldState*<br/>
Puntero a un estado de memoria anterior (estructura _**crtmemstate** ).

*newState*<br/>
Puntero a un estado de memoria posterior (estructura _**crtmemstate** ).

## <a name="return-value"></a>Valor devuelto

Si los Estados de memoria son significativamente diferentes, **_CrtMemDifference** devuelve true. De lo contrario, la función devuelve el FALSE.

## <a name="remarks"></a>Comentarios

La función **_CrtMemDifference** compara *oldState* y *newState* y almacena sus diferencias en *stateDiff*, que la aplicación puede usar para detectar pérdidas de memoria y otros problemas de memoria. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtMemDifference** se quitan durante el preprocesamiento.

*newState* y *oldState* deben ser un puntero válido a una estructura _ **crtmemstate** , definida en CRTDBG. h, que ha sido rellenada por [_CrtMemCheckpoint](crtmemcheckpoint.md) antes de llamar a **_CrtMemDifference**. *stateDiff* debe ser un puntero a una instancia asignada previamente de la estructura _ **crtmemstate** . Si *stateDiff*, *newState*o *oldState* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en **EINVAL** y la función devuelve false.

**_CrtMemDifference** compara los valores de campo _ **crtmemstate** de los bloques de *oldState* con los de *newState* y almacena el resultado en *stateDiff*. Cuando el número de tipos de bloque asignados o el número total de bloques asignados para cada tipo no es igual en los dos estados de memoria, los estados se consideran significativamente diferentes. La diferencia entre la cantidad más grande que se haya asignado al mismo tiempo para los dos Estados y la diferencia entre las asignaciones totales de los dos Estados también se almacenan en *stateDiff*.

De forma predeterminada, los bloques internos en tiempo de ejecución de C (_**crt_block**) no se incluyen en las operaciones de estado de memoria. La función _ [crtsetdbgflag](crtsetdbgflag.md) se puede usar para activar el bit **_CRTDBG_CHECK_CRT_DF** de _ **crtdbgflag** para incluir estos bloques en la detección de pérdidas y otras operaciones de estado de memoria. Los bloques de memoria liberados ( **_FREE_BLOCK**) no hacen que **_CRTMEMDIFFERENCE** devuelva true.

Para obtener más información sobre las funciones de estado del montón y la estructura _ **crtmemstate** , consulte [funciones de generación de informes de estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para obtener información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Libre** Solo versiones de depuración de características de la [biblioteca CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
