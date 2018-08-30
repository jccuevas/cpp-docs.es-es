---
title: _endthread, _endthreadex | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bed0b93b2c9643a19aa8fd97c0e52da2ba1f8be
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198795"
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

*retval* código de salida del subproceso.

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
