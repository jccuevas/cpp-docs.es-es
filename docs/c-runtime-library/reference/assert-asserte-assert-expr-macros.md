---
title: _ASSERT, _ASSERTE, _ASSERT_EXPR (macros)
ms.date: 11/04/2016
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
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: d2d83c3afa8e22c1f75480fe2afefa8bf68be858
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740025"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)

Evalúa una expresión y genera un informe de depuración cuando el resultado es **false** (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Una expresión escalar (incluidas las expresiones de puntero) que se evalúa en un valor que no es cero (true) o 0 (false).

*message*<br/>
Una cadena de caracteres anchos para mostrarla como parte del informe.

## <a name="remarks"></a>Comentarios

Las macros **_ASSERT_EXPR**, _ **Assert** y _ **Assert** proporcionan una aplicación con un mecanismo limpio y simple para comprobar suposiciones durante el proceso de depuración. Son muy flexibles porque no tienen que incluirse en instrucciones `#ifdef` para evitar que se llamen en una compilación comercial de una aplicación. Esta flexibilidad se logra mediante la macro [_DEBUG](../../c-runtime-library/debug.md) . **_ASSERT_EXPR**, _ **Assert** y _ **Assert** solo están disponibles cuando se define **_ Debug** en tiempo de compilación. Cuando no se define **_ Debug** , las llamadas a estas macros se quitan durante el preprocesamiento.

**_ASSERT_EXPR**, **_ Assert** y _ **asserte** evalúan su argumento *booleanExpression* y cuando el resultado es **false** (0), imprimen un mensaje de diagnóstico y llaman a [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) para generar un informe de depuración. La macro _ **Assert** imprime un mensaje de diagnóstico simple, _ **asserte** incluye una representación de cadena de la expresión con error en el mensaje y **_ASSERT_EXPR** incluye la cadena de *mensaje* en el mensaje de diagnóstico. Estas macros no hacen nada cuando *booleanExpression* se evalúa como un valor distinto de cero.

**_ASSERT_EXPR**, _ **Assert** y _ **Assert** Invoke **_CrtDbgReportW**, lo que hace que toda la salida esté en caracteres anchos. _ **Assert** imprime correctamente los caracteres Unicode en *booleanExpression* y **_ASSERT_EXPR** imprime los caracteres Unicode en el *mensaje*.

Dado que la macro _ **Asserte** especifica la expresión con error y **_ASSERT_EXPR** le permite especificar un mensaje en el informe generado, permiten a los usuarios identificar el problema sin hacer referencia al código fuente de la aplicación. Sin embargo, existe una desventaja en que todos los *mensajes* impresos por **_ASSERT_EXPR** y cada expresión evaluada por _ **Assert** se incluyen en el archivo de salida (versión de depuración) de la aplicación como una constante de cadena. Por lo tanto, si se realiza un gran número de llamadas a **_ASSERT_EXPR** o _ **asserte**, estas expresiones pueden aumentar considerablemente el tamaño del archivo de salida.

A menos que se especifique lo contrario con las funciones [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md) , aparecen mensajes en un cuadro de diálogo emergente equivalente a establecer lo siguiente:

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** genera el informe de depuración y determina su destino o destinos, basándose en el modo de informe actual o en los modos y el archivo definidos para el tipo de informe **_CRT_ASSERT** . De manera predeterminada, los errores de aserción y los demás errores se dirigen a una ventana de mensajes de depuración. Las funciones [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md) se usan para definir los destinos de cada tipo de informe.

Cuando el destino es una ventana de mensaje de depuración y el usuario hace clic en el botón **Reintentar** , **_CrtDbgReportW** devuelve 1, lo que hace que las macros **_ASSERT_EXPR**, _ **Assert** y _ **Assert** inicien el depurador siempre que la depuración Just-in-Time (JIT) está habilitada.

Para más información sobre el proceso de creación de informes, vea la función [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) . Para más información sobre cómo resolver errores de aserción y usar estas macros como mecanismo de control de errores de depuración, vea [Uso de macros para comprobación e informes](/visualstudio/debugger/macros-for-reporting).

Además de las macros _ **Assert** , la macro [Assert](assert-macro-assert-wassert.md) se puede usar para comprobar la lógica del programa. Esta macro está disponible en las versiones de lanzamiento y depuración de las bibliotecas. Las macros de depuración [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) también están disponibles para generar un informe de depuración, pero no evalúan una expresión. Las macros **_RPT** generan un informe sencillo. Las macros **_RPTF** incluyen el archivo de código fuente y el número de línea donde se llamó a la macro de informe en el informe generado. Hay disponibles versiones de caracteres anchos de estas macros ( **_RPTW**, **rptfw (** ). Las versiones de caracteres anchos son idénticas a las versiones de caracteres estrechos, salvo que se usan cadenas de caracteres anchos para todos los parámetros de cadena y la salida.

Aunque **_ASSERT_EXPR**, _ **Assert** y _ **Assert** son macros y \<están disponibles al incluir CRTDBG. h >, la aplicación debe vincularse con una versión de depuración de la biblioteca en tiempo de ejecución de C cuando se define **_ Debug** porque Estas macros llaman a otras funciones en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-----------|---------------------|
|**_ASSERT_EXPR**, _ **ASSERT**, _ **ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>Ejemplo

En este programa, se realizan llamadas a las macros _ **Assert** y _ **asserte** para probar la condición `string1 == string2`. Si se produce un error en la condición, estas macros imprimen un mensaje de diagnóstico. El grupo de macros **_RPT** y **_RPTF** también se ha ejecutado en este programa, como alternativa a la función **printf** .

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
