---
title: _endthread, _endthreadex
ms.date: 11/04/2016
apiname:
- _endthread
- _endthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: 48a2ce90b6bc90d40f6071898e1e5182502e938f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597488"
---
# <a name="endthread-endthreadex"></a>_endthread, _endthreadex

Termina un subproceso; **_endthread** termina un subproceso creado por **_beginthread** y **_endthreadex** termina un subproceso creado por **_beginthreadex**.

## <a name="syntax"></a>Sintaxis

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Parámetros

*retval*<br/>
Código de salida del subproceso.

## <a name="remarks"></a>Comentarios

Puede llamar a **_endthread** o **_endthreadex** explícitamente para terminar el subproceso; sin embargo, **_endthread** o **_endthreadex** se denomina Cuando el subproceso vuelve de la rutina pasa automáticamente como un parámetro a **_beginthread** o **_beginthreadex**. Si se finaliza un subproceso con una llamada a **endthread** o **_endthreadex** ayuda a garantiza la recuperación correcta de los recursos asignados para el subproceso.

> [!NOTE]
> En el caso de un archivo ejecutable vinculado a Libcmt.lib, no llame a la API [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) de Win32 porque esto impide que el sistema en tiempo de ejecución reclame los recursos asignados. **_endthread** y **_endthreadex** reclamar recursos de subprocesos asignados y, a continuación, llame a **ExitThread**.

**_endthread** cierra automáticamente el identificador de subproceso. (Este comportamiento difiere de Win32 **ExitThread** API.) Por lo tanto, cuando usa **_beginthread** y **_endthread**, no cierre explícitamente el identificador de subproceso mediante una llamada a Win32 [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) API.

Al igual que Win32 **ExitThread** API, **_endthreadex** no cierra el identificador de subproceso. Por lo tanto, cuando usa **_beginthreadex** y **_endthreadex**, debe cerrar el identificador de subproceso mediante una llamada a Win32 **CloseHandle** API.

> [!NOTE]
> **_endthread** y **_endthreadex** hacer que los destructores de C++ pendientes en el subproceso no se puede llamar.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo las versiones de multiproceso de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
