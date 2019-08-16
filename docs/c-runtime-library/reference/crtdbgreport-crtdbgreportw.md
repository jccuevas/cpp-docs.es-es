---
title: _CrtDbgReport, _CrtDbgReportW
ms.date: 11/04/2016
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
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: b5579a8996950c5f3e923f67ed2a5e667bb566fa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499999"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

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
Tipo de informe: **_CRT_WARN**, **_CRT_ERROR**y **_CRT_ASSERT**.

*filename*<br/>
Puntero al nombre del archivo de código fuente donde se produjo la aserción o el informe o **null**.

*linenumber*<br/>
Número de línea del archivo de código fuente donde se produjo la aserción o el informe o **null**.

*moduleName*<br/>
Puntero al nombre del módulo (.exe o .dll) donde se produjo la aserción o el informe.

*format*<br/>
Puntero a la cadena de control de formato utilizada para crear el mensaje de usuario.

*argument*<br/>
Argumentos de sustitución opcionales utilizados por el *formato*.

## <a name="return-value"></a>Valor devuelto

En todos los destinos de informe, _ **crtdbgreport** y **_CrtDbgReportW** devuelven-1 si se produce un error y 0 si no se encuentran errores. En cambio, cuando el destino del informe es una ventana de mensajes de depuración y el usuario hace clic en el botón **Reintentar**, estas funciones devuelven 1. Si el usuario hace clic en el botón **Anular** de la ventana de mensajes de depuración, estas funciones se anulan inmediatamente y no devuelven ningún valor.

Las macros de depuración [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) llaman a _ **crtdbgreport** para generar los informes de depuración. Las versiones con caracteres anchos de estas macros, así como _ [Assert,](assert-asserte-assert-expr-macros.md)_ asserte, [_RPTW](rpt-rptf-rptw-rptfw-macros.md) y [rptfw (](rpt-rptf-rptw-rptfw-macros.md), usan **_CrtDbgReportW** para generar los informes de depuración. Cuando _ **crtdbgreport** o **_CrtDbgReportW** devuelven 1, estas macros inician el depurador, siempre que esté habilitada la depuración Just-in-Time (JIT).

## <a name="remarks"></a>Comentarios

_ **Crtdbgreport** y **_CrtDbgReportW** pueden enviar el informe de depuración a tres destinos distintos: un archivo de informe de depuración, un monitor de depuración (el depurador de Visual Studio) o una ventana de mensaje de depuración. Se usan dos funciones de configuración, [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md), para especificar los destinos de cada tipo de informe. Estas funciones permiten controlar por separado los destinos de los informes de cada tipo de informe. Por ejemplo, es posible especificar que un *reportType* de **_CRT_WARN** se envíe solo al monitor de depuración, mientras que un *reportType* de **_CRT_ASSERT** se envía a una ventana de mensajes de depuración y a un archivo de informe definido por el usuario.

**_CrtDbgReportW** es la versión con caracteres anchos de _ **crtdbgreport**. Todos sus parámetros de salida y de cadena son cadenas de caracteres anchos; por lo demás, es idéntica a la versión de caracteres de un solo byte.

_ **Crtdbgreport** y **_CrtDbgReportW** crean el mensaje de usuario para el informe de depuración sustituyendo los argumentos del *argumento*[**n**] en la cadena de *formato* , con las mismas reglas definidas por **printf** o  **wprintf** (funciones). A continuación, estas funciones generan el informe de depuración y determinan el destino o los destinos, en función de los modos de informe actuales y del archivo definido para *reportType*. Cuando el informe se envía a una ventana de mensajes de depuración, el *nombre de archivo*, **lineNumber**y *ModuleName* se incluyen en la información que se muestra en la ventana.

En la tabla siguiente se enumeran las opciones disponibles para el modo de informe o los modos y el archivo, así como el comportamiento resultante de _ **crtdbgreport** y **_CrtDbgReportW**. Estas opciones se definen como marcas de bits en \<crtdbg.h>.

|Modo de informe|Archivo de informe|_ **Crtdbgreport**, comportamiento de **_CrtDbgReportW**|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|No aplicable|Escribe el mensaje mediante la API [OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw) de Windows.|
|**_CRTDBG_MODE_WNDW**|No aplicable|Llama a la API [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) de Windows para crear el cuadro de mensaje en el que se mostrará el mensaje junto con los botones **Anular**, **Reintentar** y **Omitir**. Si un usuario hace clicen anular, _ **Crtdbgreport** o _ **crtdbgreport** se anula inmediatamente. Si un usuario hace clic en **Reintentar**, devuelve 1. Si un usuario hace clicen omitir, la ejecución continúa y _ **crtdbgreport** y **_CrtDbgReportW** devuelven 0. Observe que si se hace clic en **Omitir** cuando existe una condición de error, se suele producir un "comportamiento indefinido".|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Escribe el mensaje en el **identificador**proporcionado por el usuario, usando la API [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) de Windows y no comprueba la validez del identificador de archivo. la aplicación es responsable de abrir el archivo de informe y de pasar un identificador de archivo válido.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Escribe el mensaje en **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Escribe el mensaje en **stdout**.|

El informe se puede enviar a uno, dos o tres destinos, o a ninguno. Para obtener más información sobre cómo especificar los modos de informe y el archivo de informe, consulte las funciones [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md). Para obtener más información sobre el uso de las macros de depuración y las funciones de creación de informes, consulte [Macros para los informes](/visualstudio/debugger/macros-for-reporting).

Si la aplicación necesita más flexibilidad que la que proporciona _ **crtdbgreport** y **_CrtDbgReportW**, puede escribir su propia función de creación de informes y enlazarla al mecanismo de informes de la biblioteca en tiempo de ejecución de C mediante [_CrtSetReportHook](crtsetreporthook.md) funcionalidad.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

_ **Crtdbgreport** y **_CrtDbgReportW** son extensiones de Microsoft. Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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
