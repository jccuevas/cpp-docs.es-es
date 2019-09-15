---
title: _getpid
ms.date: 11/04/2016
api_name:
- _getpid
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getpid
helpviewer_keywords:
- getpid function
- _getpid function
- process identification numbers
ms.assetid: d3e13bae-9a0c-4f33-86d3-ec9df9519285
ms.openlocfilehash: b0848e5eb01f39c009fcdc650ea551f18e23c6fb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954996"
---
# <a name="_getpid"></a>_getpid

Obtiene el identificador del proceso.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _getpid( void );
```

## <a name="return-value"></a>Valor devuelto

Devuelve el identificador del proceso obtenido del sistema. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

La función **_getpid** obtiene el identificador de proceso del sistema. El identificador del proceso identifica el proceso de llamada de forma única.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getpid**|\<process.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_getpid.c
// This program uses _getpid to obtain
// the process ID and then prints the ID.

#include <stdio.h>
#include <process.h>

int main( void )
{
   // If run from command line, shows different ID for
   // command line than for operating system shell.

   printf( "Process id: %d\n", _getpid() );
}
```

```Output
Process id: 3584
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_mktemp, _wmktemp](mktemp-wmktemp.md)<br/>
