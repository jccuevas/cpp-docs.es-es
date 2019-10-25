---
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
api_name:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 7aba82e3dfea220f2edc3bd3a689a48e316a0087
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938701"
---
# <a name="_crtmemdumpstatistics"></a>_CrtMemDumpStatistics

Vuelca la información del encabezado de depuración de un estado del montón especificado en un formato legible para el usuario (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Puntero al estado del montón que se va a volcar.

## <a name="remarks"></a>Comentarios

La función **_CrtMemDumpStatistics** vuelca la información del encabezado de depuración de un estado especificado del montón en un formato legible para el usuario. La aplicación puede usar las estadísticas del volcado para realizar el seguimiento de las asignaciones y detectar problemas de memoria. El estado de la memoria puede contener un estado de montón concreto o la diferencia entre dos estados. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtMemDumpStatistics** se quitan durante el preprocesamiento.

El parámetro *State* debe ser un puntero a una estructura _ **crtmemstate** que haya sido rellenada por [_CrtMemCheckpoint](crtmemcheckpoint.md) o que haya devuelto [_CrtMemDifference](crtmemdifference.md) antes de que se llame a **_CrtMemDumpStatistics** . Si el *Estado* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y no se realiza ninguna acción. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Para obtener más información sobre las funciones de estado del montón y la estructura _ **crtmemstate** , consulte [funciones de generación de informes de estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Libre** Solo versiones de depuración de características de la [biblioteca CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
