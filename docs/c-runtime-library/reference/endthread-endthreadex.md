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
ms.openlocfilehash: 5afbc907356d4c5b14b749de5de0c8d36280891e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499961"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Finaliza un subproceso; _ **endthread** termina un subproceso creado por _ **beginthread** y _ **endthreadex** finaliza un subproceso creado por _ **beginthreadex**.

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

Puede llamar a _ **endthread** o _ **endthreadex** explícitamente para terminar un subproceso; sin embargo, se llama a _ **endthread** o _ **endthreadex** automáticamente cuando el subproceso vuelve de la rutina pasada como un parámetro a _ **beginthread** o _ **beginthreadex**. La finalización de un subproceso con una llamada a **endthread** o _ **endthreadex** ayuda a garantizar la recuperación correcta de los recursos asignados para el subproceso.

> [!NOTE]
> En el caso de un archivo ejecutable vinculado a Libcmt.lib, no llame a la API [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) de Win32 porque esto impide que el sistema en tiempo de ejecución reclame los recursos asignados. _ **endthread** y _ **endthreadex** reclaman recursos de subprocesos asignados y después llaman a **ExitThread**.

_ **endthread** cierra automáticamente el identificador del subproceso. (Este comportamiento difiere de la API **ExitThread** de Win32). Por lo tanto, cuando use _ **beginthread** y _ **endthread**, no cierre explícitamente el identificador del subproceso llamando a la API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) de Win32.

Al igual que la API **ExitThread** de Win32, _ **endthreadex** no cierra el identificador del subproceso. Por lo tanto, cuando use _ **beginthreadex** y _ **endthreadex**, debe cerrar el identificador de subproceso llamando a la API **CloseHandle** de Win32.

> [!NOTE]
> _ **endthread** y _ C++ **endthreadex** provocan que no se llame a los destructores pendientes en el subproceso.

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
