---
title: _pclose
ms.date: 11/04/2016
apiname:
- _pclose
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: eb0f54ec27992cd0e62b11d8fec5bd54c3daea4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507723"
---
# <a name="pclose"></a>_pclose

Espera un nuevo procesador de comandos y cierra el flujo en la canalización asociada.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*secuencia*<br/>
Devuelve el valor de la llamada anterior a **_popen**.

## <a name="return-value"></a>Valor devuelto

Devuelve el estado de salida del procesador de comandos de la terminación o -1 si se produce un error. El formato del valor devuelto es el mismo que para **_cwait**, excepto en que se intercambian los bytes de orden inferior y de orden superior. Si la secuencia es **NULL**, **_pclose** establece **errno** a **EINVAL** y devuelve -1.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_pclose** función busca el identificador de proceso del procesador de comandos (Cmd.exe) iniciado por el asociado **_popen** llamada, se ejecuta un [_cwait](cwait.md) llamar en el nuevo comando procesador y cierra la secuencia en la canalización asociada.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen, _wpopen](popen-wpopen.md)<br/>
