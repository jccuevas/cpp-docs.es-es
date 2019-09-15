---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
api_name:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: edf91cd8c76fd080326e2e5eeac98f7f81ab90cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942357"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

Obtiene el estado actual del montón de depuración y lo almacena en una estructura _ **crtmemstate** proporcionada por la aplicación (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Puntero a la estructura _ **crtmemstate** para rellenar con el punto de control de memoria.

## <a name="remarks"></a>Comentarios

La función **_CrtMemCheckpoint** crea una instantánea del estado actual del montón de depuración en un momento dado. Esta instantánea la pueden usar otras funciones de estado del montón, como [_CrtMemDifference](crtmemdifference.md) , para ayudar a detectar pérdidas de memoria y otros problemas. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a _ **crtmemstate** se quitan durante el preprocesamiento.

La aplicación debe pasar un puntero a una instancia asignada previamente de la estructura _ **crtmemstate** , definida en CRTDBG. h, en el parámetro *State* . Si **_CrtMemCheckpoint** detecta un error durante la creación del punto de comprobación, la función genera un informe de depuración de **_CRT_WARN** que describe el problema.

Para obtener más información sobre las funciones de estado del montón y la estructura _ **crtmemstate** , consulte [funciones de generación de informes de estado del montón](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si el *Estado* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establecen en **EINVAL** y la función devuelve.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Libre** Solo versiones de depuración de UCRT.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
