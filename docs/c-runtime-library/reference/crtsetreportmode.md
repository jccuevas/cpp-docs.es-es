---
title: _CrtSetReportMode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd4ac54cd4bd8877e8a6ba32f585ef5d5e29e65c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403266"
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode

Especifica el destino o destinos para un tipo específico de informe generado por **_CrtDbgReport** y las macros que se llame a [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md), como [_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)](assert-asserte-assert-expr-macros.md), [_ASSERT, _ASSERTE, _ASSERT_EXPR (Macros)](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _RPTFW (Macros)](rpt-rptf-rptw-rptfw-macros.md), y [_RPT, _RPTF, _RPTW, _RPTFW (Macros)](rpt-rptf-rptw-rptfw-macros.md) (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Parámetros

*reportType*<br/>
Tipo de informe: **_CRT_WARN**, **_CRT_ERROR**, y **_CRT_ASSERT**.

*reportMode*<br/>
Nuevo modo de informe o modos para *reportType*.

## <a name="return-value"></a>Valor devuelto

Cuando se finaliza correctamente, **_CrtSetReportMode** devuelve el modo de informe anterior o modos para el tipo de informe especificado en *reportType*. Si se pasa un valor no válido como *reportType* o se ha especificado un modo no válido para *reportMode*, **_CrtSetReportMode** se invoca el controlador de parámetros no válidos como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve -1. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

**_CrtSetReportMode** especifica el destino de salida para **_CrtDbgReport**. Dado que las macros [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md), y [_RPTF](rpt-rptf-rptw-rptfw-macros.md) llamar a **_CrtDbgReport**, **_CrtSetReportMode** especifica el destino de salida de texto especificado con las macros.

Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtSetReportMode** se quitan durante el preprocesamiento.

Si no se llama **_CrtSetReportMode** para definir el destino de salida de mensajes, a continuación, los siguientes valores predeterminados están en vigor:

- Los errores de aserción y los demás errores se dirigen a una ventana de mensajes de depuración.

- Las advertencias de las aplicaciones se Windows se envían a la ventana de salida del depurador.

- Las advertencias de las aplicaciones de consola no se muestran.

En la tabla siguiente se enumeran los tipos de informe definidos en Crtdbg.h.

|Tipo de informe|Descripción|
|-----------------|-----------------|
|**_CRT_WARN**|Advertencias, mensajes e información que no requieren atención inmediata.|
|**_CRT_ERROR**|Errores, problemas irrecuperables y problemas que requieren atención inmediata.|
|**_CRT_ASSERT**|Errores de aserción (expresiones declaradas que se evalúan como **FALSE**).|

El **_CrtSetReportMode** función asigna el nuevo modo de informe especificado en *reportMode* para el tipo de informe especificado en *reportType* y devuelve definida previamente modo de informe para *reportType*. En la tabla siguiente se enumera las opciones disponibles para *reportMode* y el comportamiento resultante de **_CrtDbgReport**. Estas opciones se definen como marcas de bits en Crtdbg.h.

|Modo de informe|Comportamiento de _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Escribe el mensaje en la ventana de salida del depurador.|
|**_CRTDBG_MODE_FILE**|Escribe el mensaje en un identificador de archivos proporcionado por el usuario. Debe llamarse a [_CrtSetReportFile](crtsetreportfile.md) para definir el archivo o la secuencia específicos que se deben usar como destino.|
|**_CRTDBG_MODE_WNDW**|Crea un cuadro de mensaje para mostrar el mensaje junto con el [anular](abort.md), **vuelva a intentar**, y **omitir** botones.|
|**_CRTDBG_REPORT_MODE**|Devuelve *reportMode* para el elemento especificado *reportType*:<br /><br /> 1 **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

Cada tipo de informe se puede designar mediante uno, dos o tres modos, o sin ningún modo. Por consiguiente, es posible tener más de un destino definido para un único tipo de informe. Por ejemplo, el fragmento de código siguiente hace que se envíen a una ventana de mensajes de depuración y a los errores de aserción **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

Además, el modo o los modos de informe de cada tipo de informe se pueden controlar por separado. Por ejemplo, es posible especificar que un *reportType* de **_CRT_WARN** ser envía a una cadena de depuración de salida, mientras **_CRT_ASSERT** pueden mostrar mediante una ventana de mensaje de depuración y se envía a **stderr**, como ya se ha mostrado.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** solo versiones de depuración de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
