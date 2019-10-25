---
title: _pclose
ms.date: 11/04/2016
api_name:
- _pclose
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: 383dd96553463a2619537cf06fc6534770ed88d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951082"
---
# <a name="_pclose"></a>_pclose

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

*stream*<br/>
Valor devuelto de la llamada anterior a **_popen**.

## <a name="return-value"></a>Valor devuelto

Devuelve el estado de salida del procesador de comandos de terminación o-1 si se produce un error. El formato del valor devuelto es el mismo que el de **_cwait**, excepto que se intercambian los bytes de orden inferior y de orden superior. Si Stream es **null**, **_pclose** establece **errno** en **EINVAL** y devuelve-1.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_pclose** busca el identificador de proceso del procesador de comandos (cmd. exe) iniciado por la llamada **_popen** asociada, ejecuta una llamada [_cwait](cwait.md) en el nuevo procesador de comandos y cierra el flujo en la canalización asociada.

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
