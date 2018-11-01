---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
apiname:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: ee435ba3e9e40795280dee0f97feaad32c8b0fc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589522"
---
# <a name="crtmemcheckpoint"></a>_CrtMemCheckpoint

Obtiene el estado actual del montón de depuración y lo almacena en una proporcionada por la aplicación **_CrtMemState** estructura (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Puntero a **_CrtMemState** estructura que se rellena con el punto de comprobación de memoria.

## <a name="remarks"></a>Comentarios

El **_CrtMemCheckpoint** función crea una instantánea del estado actual del montón de depuración en un momento dado. Esta instantánea la pueden usar otras funciones de estado del montón, como [_CrtMemDifference](crtmemdifference.md) , para ayudar a detectar pérdidas de memoria y otros problemas. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtMemState** se quitan durante el preprocesamiento.

La aplicación debe pasar un puntero a una instancia asignada previamente de la **_CrtMemState** estructura, definida en Crtdbg.h, en el *estado* parámetro. Si **_CrtMemCheckpoint** encuentra un error durante la creación del punto de comprobación, la función genera una **_CRT_WARN** depurar informes que describe el problema.

Para obtener más información sobre las funciones de estado del montón y la **_CrtMemState** estructura, vea [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details). Para más información sobre cómo se asignan, inicializan y administran los bloques de memoria en la versión de depuración del montón base, vea [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Si *estado* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) está establecido en **EINVAL** y devuelve la función.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** solo versiones de depuración de la UCRT.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
