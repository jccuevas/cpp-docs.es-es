---
title: _CrtDbgReport, _CrtDbgReportW | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57290d2985036ea3df2863e175d742c819a3fe03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Genera un informe con un mensaje de depuración y lo envía a tres destinos posibles (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>Parámetros

*reportType*<br/>
Tipo de informe: **_CRT_WARN**, **_CRT_ERROR**, y **_CRT_ASSERT**.

*filename*<br/>
Puntero al nombre del archivo de origen donde se produjo la aserción o el informe o **NULL**.

*linenumber*<br/>
Número de línea en el archivo de código fuente donde se produjo la aserción o el informe o **NULL**.

*moduleName*<br/>
Puntero al nombre del módulo (.exe o .dll) donde se produjo la aserción o el informe.

*format*<br/>
Puntero a la cadena de control de formato utilizada para crear el mensaje de usuario.

*Argumento*<br/>
Argumentos de sustitución opcionales utilizados por *formato*.

## <a name="return-value"></a>Valor devuelto

Para todos los destinos de informe, **_CrtDbgReport** y **_CrtDbgReportW** devuelve -1 si se produce un error y 0 si no se encuentran errores. En cambio, cuando el destino del informe es una ventana de mensajes de depuración y el usuario hace clic en el botón **Reintentar**, estas funciones devuelven 1. Si el usuario hace clic en el botón **Anular** de la ventana de mensajes de depuración, estas funciones se anulan inmediatamente y no devuelven ningún valor.

El [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) depurar macros llamada **_CrtDbgReport** para su depuración de generar informes. Las versiones de caracteres anchos de estas macros, así como [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) y [_RPTFW](rpt-rptf-rptw-rptfw-macros.md), use **_CrtDbgReportW** a generar sus informes de depuración. Cuando **_CrtDbgReport** o **_CrtDbgReportW** devuelven 1, estas macros inician el depurador, siempre que está habilitada la depuración just-in-time (JIT).

## <a name="remarks"></a>Comentarios

**_CrtDbgReport** y **_CrtDbgReportW** puede enviar el informe de depuración a tres destinos distintos: un archivo de informe de depuración, un monitor de depuración (el depurador de Visual Studio) o una ventana de mensaje de depuración. Se usan dos funciones de configuración, [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md), para especificar los destinos de cada tipo de informe. Estas funciones permiten controlar por separado los destinos de los informes de cada tipo de informe. Por ejemplo, es posible especificar que un *reportType* de **_CRT_WARN** solo ser enviados al monitor de depuración, mientras un *reportType* de **_CRT_ASSERT** enviará a una ventana de mensaje de depuración y un archivo de informe definido por el usuario.

**_CrtDbgReportW** es la versión con caracteres anchos de **_CrtDbgReport**. Todos sus parámetros de salida y de cadena son cadenas de caracteres anchos; por lo demás, es idéntica a la versión de caracteres de un solo byte.

**_CrtDbgReport** y **_CrtDbgReportW** crean el mensaje de usuario para el informe de depuración sustituyendo el *argumento*[**n**] argumentos a la *formato* de cadena, utilizando las mismas reglas definidas por el **printf** o **wprintf** funciones. Estas funciones, a continuación, generan el informe de depuración y determinan el destino o destinos, en función de los modos de informe actual y el archivo definidos para *reportType*. Cuando el informe se envía a una ventana de mensaje de depuración, el *filename*, **lineNumber**, y *moduleName* se incluyen en la información mostrada en la ventana.

En la tabla siguiente se enumera las opciones disponibles para el modo de informe o modos de archivo y el comportamiento resultante de **_CrtDbgReport** y **_CrtDbgReportW**. Estas opciones se definen como marcas de bits en \<crtdbg.h>.

|Modo de informe|Archivo de informe|**_CrtDbgReport**, **_CrtDbgReportW** comportamiento|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|No es aplicable|Escribe el mensaje mediante la API [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) de Windows.|
|**_CRTDBG_MODE_WNDW**|No es aplicable|Llama a la API [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) de Windows para crear el cuadro de mensaje en el que se mostrará el mensaje junto con los botones **Anular**, **Reintentar** y **Omitir**. Si un usuario hace clic en **anular**, **_CrtDbgReport** o **_CrtDbgReport** anula inmediatamente. Si un usuario hace clic en **Reintentar**, devuelve 1. Si un usuario hace clic en **omitir**, la ejecución continúa y **_CrtDbgReport** y **_CrtDbgReportW** devuelven 0. Observe que si se hace clic en **Omitir** cuando existe una condición de error, se suele producir un "comportamiento indefinido".|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Escribe el mensaje proporcionado por el usuario **controlar**, con las ventanas de [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) API y no se comprueba la validez del identificador de archivo; la aplicación es responsable de abrir el archivo de informe y pasar un archivo válido identificador.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Escribe el mensaje en **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Escribe el mensaje en **stdout**.|

El informe se puede enviar a uno, dos o tres destinos, o a ninguno. Para obtener más información sobre cómo especificar los modos de informe y el archivo de informe, consulte las funciones [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md). Para obtener más información sobre el uso de las macros de depuración y las funciones de creación de informes, consulte [Macros para los informes](/visualstudio/debugger/macros-for-reporting).

Si la aplicación necesita más flexibilidad que la proporcionada por **_CrtDbgReport** y **_CrtDbgReportW**, puede escribir su propia reporting función y enlazarlo a los informes de la biblioteca en tiempo de ejecución de C mecanismo mediante el uso de la [_CrtSetReportHook](crtsetreporthook.md) función.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** y **_CrtDbgReportW** son extensiones de Microsoft. Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

Consulte [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) para obtener un ejemplo de cómo cambiar la función de informes.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
