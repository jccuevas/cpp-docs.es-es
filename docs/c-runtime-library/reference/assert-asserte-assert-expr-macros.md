---
title: _ASSERT, _ASSERTE, _ASSERT_EXPR (Macros) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa84e5c032cefa49ef3a9d21d3bbfc2073d02e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399743"
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)

Evaluar una expresión y generar un informe de depuración cuando el resultado es **False** (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Parámetros

*booleanExpression* una expresión escalar (incluidas las expresiones de puntero) que se evalúa como distinto de cero (true) o 0 (false).

*mensaje* una cadena de caracteres ancho para mostrar como parte del informe.

## <a name="remarks"></a>Comentarios

El **_ASSERT_EXPR**, **_ASSERT** y **_ASSERTE** ofrecen una aplicación con un mecanismo simple y limpio para comprobar suposiciones durante el proceso de depuración. Son muy flexibles porque no tienen que incluirse en instrucciones `#ifdef` para evitar que se llamen en una compilación comercial de una aplicación. Esta flexibilidad se logra mediante la macro [_DEBUG](../../c-runtime-library/debug.md) . **_ASSERT_EXPR**, **_ASSERT** y **_ASSERTE** solo están disponibles cuando **_DEBUG** se define en tiempo de compilación. Cuando **_DEBUG** no es está definido, las llamadas a estas macros se quitan durante el preprocesamiento.

**_ASSERT_EXPR**, **_ASSERT** y **_ASSERTE** evaluar sus *booleanExpression* argumento y cuando el resultado es **false**(0), imprimen un mensaje de diagnóstico y llaman a [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) para generar un informe de depuración. El **_ASSERT** macro imprime un mensaje de diagnóstico simple, **_ASSERTE** incluye una representación de cadena de la expresión del error en el mensaje, y **_ASSERT_EXPR** incluye el *mensaje* cadena en el mensaje de diagnóstico. Estas macros no hacen nada cuando *booleanExpression* se evalúa como distinto de cero.

**_ASSERT_EXPR**, **_ASSERT** y **_ASSERTE** invocar **_CrtDbgReportW**, lo que hace que toda la salida en caracteres anchos. **_ASSERTE** imprime correctamente los caracteres Unicode en *booleanExpression* y **_ASSERT_EXPR** imprime caracteres Unicode en *mensaje*.

Dado que la **_ASSERTE** macro especifica la expresión del error y **_ASSERT_EXPR** permite especificar un mensaje en el informe generado, permiten que los usuarios identificar el problema sin hacer referencia a la código fuente de la aplicación. Sin embargo, existe una desventaja de que cada *mensaje* impresos por **_ASSERT_EXPR** y cada expresión evaluada por **_ASSERTE** se incluye en la salida (versión de depuración) archivo de la aplicación como una constante de cadena. Por lo tanto, si un gran número de llamadas se realizan en **_ASSERT_EXPR** o **_ASSERTE**, estas expresiones pueden aumentar considerablemente el tamaño de su archivo de salida.

A menos que se especifique lo contrario con las funciones [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md), aparecen mensajes en un cuadro de diálogo emergente equivalente a establecer lo siguiente:

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** genera el informe de depuración y determina su destino o destinos, en función de los modos de modo de informe actual y los archivos definidos para la **_CRT_ASSERT** tipo de informe. De manera predeterminada, los errores de aserción y los demás errores se dirigen a una ventana de mensajes de depuración. Las funciones [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md) se usan para definir los destinos de cada tipo de informe.

Cuando el destino es una ventana de mensaje de depuración y el usuario hace clic en el **vuelva a intentar** botón, **_CrtDbgReportW** devuelve 1, haciendo que el **_ASSERT_EXPR**, **_ ASSERT** y **_ASSERTE** macros para iniciar el depurador siempre que está habilitada la depuración just-in-time (JIT).

Para obtener más información sobre el proceso de creación de informes, consulte la función [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) . Para más información sobre cómo resolver errores de aserción y usar estas macros como mecanismo de control de errores de depuración, vea [Uso de macros para comprobación e informes](/visualstudio/debugger/macros-for-reporting).

Además el **_ASSERT** macros, el [assert](assert-macro-assert-wassert.md) macro puede utilizarse para comprobar la lógica del programa. Esta macro está disponible en las versiones de lanzamiento y depuración de las bibliotecas. Las macros de depuración [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) también están disponibles para generar un informe de depuración, pero no evalúan una expresión. El **_RPT** macros de generan un informe sencillo. El **_RPTF** macros incluyen el número de archivo y la línea de código fuente donde se llamó a la macro de informe en el informe generado. Versiones de caracteres anchos de estas macros están disponibles (**_RPTW**, **_RPTFW**). Las versiones de caracteres anchos son idénticas a las versiones de caracteres estrechos, salvo que se usan cadenas de caracteres anchos para todos los parámetros de cadena y la salida.

Aunque **_ASSERT_EXPR**, **_ASSERT** y **_ASSERTE** son macros y están disponibles mediante la inclusión de \<crtdbg.h >, la aplicación debe vincularse a una depuración versión de la biblioteca de tiempo de ejecución de C cuando **_DEBUG** está definida porque estas macros llaman a otras funciones de tiempo de ejecución.

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT**, **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>Ejemplo

En este programa, se realizan llamadas a la **_ASSERT** y **_ASSERTE** macros para probar la condición `string1 == string2`. Si se produce un error en la condición, estas macros imprimen un mensaje de diagnóstico. El **_RPT** y **_RPTF** grupo de macros también se aplican en este programa, como una alternativa a la **printf** función.

```C
// crt_ASSERT_macro.c
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug
//
// This program uses the _ASSERT and _ASSERTE debugging macros.
//

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main()
{
   char *p1, *p2;

   // The Reporting Mode and File must be specified
   // before generating a debug report via an assert
   // or report macro.
   // This program sends all report types to STDOUT.
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);

   // Allocate and assign the pointer variables.
   p1 = (char *)malloc(10);
   strcpy_s(p1, 10, "I am p1");
   p2 = (char *)malloc(10);
   strcpy_s(p2, 10, "I am p2");

   // Use the report macros as a debugging
   // warning mechanism, similar to printf.
   // Use the assert macros to check if the
   // p1 and p2 variables are equivalent.
   // If the expression fails, _ASSERTE will
   // include a string representation of the
   // failed expression in the report.
   // _ASSERT does not include the
   // expression in the generated report.
   _RPT0(_CRT_WARN,
       "Use the assert macros to evaluate the expression p1 == p2.\n");
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);
   _ASSERT(p1 == p2);

   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",
          p1, p2);
   _ASSERTE(p1 == p2);

   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);

   free(p2);
   free(p1);

   return 0;
}
```

```Output
Use the assert macros to evaluate the expression p1 == p2.
crt_ASSERT_macro.c(54) :
Will _ASSERT find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(55) : Assertion failed!
crt_ASSERT_macro.c(58) :

Will _ASSERTE find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2
'I am p1' != 'I am p2'
```

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[assert (macro), _assert, _wassert](assert-macro-assert-wassert.md)<br/>
[_RPT, _RPTF, _RPTW, _RPTFW (Macros)](rpt-rptf-rptw-rptfw-macros.md)<br/>
