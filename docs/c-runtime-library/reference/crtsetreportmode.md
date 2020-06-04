---
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: ae7e83ac009d572f8a9f6484519b0cdfb7499ce3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938461"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

Especifica el destino o destinos de un tipo de informe específico generado por _ **crtdbgreport** y cualquier macro que llame a _ [crtdbgreport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md), como _ [ASsert, _ Asserte, _ASSERT_EXPR macros](assert-asserte-assert-expr-macros.md), _ Assert [, _ asserte, _ Macros ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, rptfw (macros](rpt-rptf-rptw-rptfw-macros.md)y [_RPT, _RPTF, _RPTW, rptfw (macros](rpt-rptf-rptw-rptfw-macros.md) (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Parámetros

*reportType*<br/>
Tipo de informe: **_CRT_WARN**, **_CRT_ERROR**y **_CRT_ASSERT**.

*reportMode*<br/>
Nuevo modo de informe o modos para *reportType*.

## <a name="return-value"></a>Valor devuelto

Si se completa correctamente, _ **crtsetreportmode** devuelve el modo de informe anterior o los modos para el tipo de informe especificado en *reportType*. Si se pasa un valor no válido como *reportType* o se especifica un modo no válido para *reportMode*, _ **crtsetreportmode** invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve-1. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

_ **Crtsetreportmode** especifica el destino de salida para _ **crtdbgreport**. Dado que las macros _ [Assert](assert-asserte-assert-expr-macros.md), _ [asserte](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md)y [_RPTF](rpt-rptf-rptw-rptfw-macros.md) llaman a _ **crtdbgreport**, _ **crtsetreportmode** especifica el destino de salida del texto especificado con esas macros.

Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a _ **crtsetreportmode** se quitan durante el preprocesamiento.

Si no llama a _ **crtsetreportmode** para definir el destino de salida de los mensajes, se aplican los siguientes valores predeterminados:

- Los errores de aserción y los demás errores se dirigen a una ventana de mensajes de depuración.

- Las advertencias de las aplicaciones se Windows se envían a la ventana de salida del depurador.

- Las advertencias de las aplicaciones de consola no se muestran.

En la tabla siguiente se enumeran los tipos de informe definidos en Crtdbg.h.

|Tipo de informe|DESCRIPCIÓN|
|-----------------|-----------------|
|**_CRT_WARN**|Advertencias, mensajes e información que no requieren atención inmediata.|
|**_CRT_ERROR**|Errores, problemas irrecuperables y problemas que requieren atención inmediata.|
|**_CRT_ASSERT**|Errores de aserción (expresiones declaradas que se evalúan como **false**).|

La función _ **crtsetreportmode** asigna el nuevo modo de informe especificado en *reportMode* al tipo de informe especificado en *reportType* y devuelve el modo de informe previamente definido para *reportType*. En la tabla siguiente se enumeran las opciones disponibles para *reportMode* y el comportamiento resultante de _ **crtdbgreport**. Estas opciones se definen como marcas de bits en Crtdbg.h.

|Modo de informe|Comportamiento de _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Escribe el mensaje en la ventana de salida del depurador.|
|**_CRTDBG_MODE_FILE**|Escribe el mensaje en un identificador de archivos proporcionado por el usuario. Debe llamarse a [_CrtSetReportFile](crtsetreportfile.md) para definir el archivo o la secuencia específicos que se deben usar como destino.|
|**_CRTDBG_MODE_WNDW**|Crea un cuadro de mensaje para mostrar el mensaje junto con los botones [anular](abort.md), **Reintentar**y **omitir** .|
|**_CRTDBG_REPORT_MODE**|Devuelve *reportMode* para el *reportType*especificado:<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2   **_CRTDBG_MODE_DEBUG**<br /><br /> 4   **_CRTDBG_MODE_WNDW**|

Cada tipo de informe se puede designar mediante uno, dos o tres modos, o sin ningún modo. Por consiguiente, es posible tener más de un destino definido para un único tipo de informe. Por ejemplo, el fragmento de código siguiente hace que se envíen errores de aserción a una ventana de mensajes de depuración y a **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

Además, el modo o los modos de informe de cada tipo de informe se pueden controlar por separado. Por ejemplo, es posible especificar que un *reportType* de **_CRT_WARN** se envíe a una cadena de depuración de salida, mientras que **_CRT_ASSERT** se muestra mediante una ventana de mensaje de depuración y se envía a **stderr**, como se mostró anteriormente.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Libre** Solo versiones de depuración de características de la [biblioteca CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
