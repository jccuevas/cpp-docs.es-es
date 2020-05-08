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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a3889adcc90bd62e766102b72aae68577915e55b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915086"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Finaliza un subproceso; **_endthread** termina un subproceso creado por **_beginthread** y **_endthreadex** finaliza un subproceso creado por **_beginthreadex**.

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

Puede llamar a **_endthread** o **_endthreadex** explícitamente para terminar un subproceso; sin embargo, **_endthread** o **_endthreadex** se llama automáticamente cuando el subproceso vuelve de la rutina pasada como un parámetro a **_beginthread** o **_beginthreadex**. La terminación de un subproceso con una llamada a **endthread** o **_endthreadex** ayuda a garantizar la recuperación correcta de los recursos asignados para el subproceso.

> [!NOTE]
> En el caso de un archivo ejecutable vinculado a Libcmt.lib, no llame a la API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) de Win32 porque esto impide que el sistema en tiempo de ejecución reclame los recursos asignados. **_endthread** y **_endthreadex** reclaman recursos de subprocesos asignados y después llaman a **ExitThread**.

**_endthread** cierra automáticamente el identificador del subproceso. (Este comportamiento difiere de la API **ExitThread** de Win32). Por lo tanto, cuando utilice **_beginthread** y **_endthread**, no cierre explícitamente el identificador del subproceso llamando a la API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) de Win32.

Al igual que la API **ExitThread** de Win32, **_endthreadex** no cierra el identificador del subproceso. Por lo tanto, cuando utilice **_beginthreadex** y **_endthreadex**, debe cerrar el identificador de subproceso llamando a la API **CloseHandle** de Win32.

> [!NOTE]
> **_endthread** y **_endthreadex** provocan que no se llame a los destructores de C++ pendientes en el subproceso.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

## <a name="see-also"></a>Consulta también

[Control de proceso y entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
