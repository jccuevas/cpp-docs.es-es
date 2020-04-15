---
title: _endthread, _endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c76f479255080400e07678ef5dbde572b7a9dffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348038"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

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

## <a name="remarks"></a>Observaciones

Puede llamar a **_endthread** o **_endthreadex** explícitamente para terminar un subproceso; sin embargo, **_endthread** o **_endthreadex** se llama automáticamente cuando el subproceso vuelve de la rutina pasada como parámetro a **_beginthread** o **_beginthreadex**. Terminar un subproceso con una llamada a **endthread** o **_endthreadex** ayuda a garantizar la recuperación adecuada de los recursos asignados para el subproceso.

> [!NOTE]
> En el caso de un archivo ejecutable vinculado a Libcmt.lib, no llame a la API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) de Win32 porque esto impide que el sistema en tiempo de ejecución reclame los recursos asignados. **_endthread** y **_endthreadex** reclamar recursos de subproceso asignados y, a continuación, llamar a **ExitThread**.

**_endthread** cierra automáticamente el identificador de subproceso. (Este comportamiento difiere de la API **ExitThread** de Win32.) Por lo tanto, cuando utilice **_beginthread** y **_endthread**, no cierre explícitamente el identificador de subproceso llamando a la API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) de Win32.

Al igual que la API **ExitThread** de Win32, **_endthreadex** no cierra el identificador de subproceso. Por lo tanto, cuando se usa **_beginthreadex** y **_endthreadex**, debe cerrar el identificador de subproceso mediante una llamada a la API **CloseHandle** de Win32.

> [!NOTE]
> **_endthread** y **_endthreadex** hacer que no se llame a los destructores C++ pendientes en el subproceso.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo las versiones de multiproceso de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
