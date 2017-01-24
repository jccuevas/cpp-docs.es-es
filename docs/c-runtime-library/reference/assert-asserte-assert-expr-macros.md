---
title: "_ASSERT, _ASSERTE, _ASSERT_EXPR (macros) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ASSERTE"
  - "ASSERTE"
  - "_ASSERT"
  - "_ASSERT_EXPR"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "depurar [CRT], usar macros"
  - "_ASSERTE (macro)"
  - "macros, depurar con"
  - "macros de informes de depuración"
  - "_ASSERT (macro)"
  - "_ASSERT_EXPR (macro)"
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ASSERT, _ASSERTE, _ASSERT_EXPR (macros)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Evalúa una expresión y genera un informe de depuración cuando el resultado es `False` \(solo la versión de depuración\).  
  
## Sintaxis  
  
```  
_ASSERT_EXPR(  
   booleanExpression,  
   message  
);  
_ASSERT(   
   booleanExpression   
);  
_ASSERTE(   
   booleanExpression   
);  
  
```  
  
#### Parámetros  
 `booleanExpression`  
 Una expresión escalar \(incluidas las expresiones de puntero\) que se evalúa en un valor que no es cero \(true\) o 0 \(false\).  
  
 `message`  
 Una cadena de caracteres anchos para mostrarla como parte del informe.  
  
## Comentarios  
 Las `_ASSERT_EXPR`, `_ASSERT` y `_ASSERTE` ofrecen una aplicación con un mecanismo simple y limpio para comprobar suposiciones durante el proceso de depuración. Son muy flexibles porque no tienen que incluirse en instrucciones `#ifdef` para evitar que se llamen en una compilación comercial de una aplicación. Esta flexibilidad se logra mediante la macro [\_DEBUG](../../c-runtime-library/debug.md).`_ASSERT_EXPR`, `_ASSERT` y `_ASSERTE` solo están disponibles cuando `_DEBUG` se define en tiempo de compilación. Cuando no se define `_DEBUG`, las llamadas a estas macros se quitan durante el preprocesamiento.  
  
 `_ASSERT_EXPR`, `_ASSERT` y `_ASSERTE` evalúan su argumento `booleanExpression` y cuando el resultado es `false` \(0\), imprimen un mensaje de diagnóstico y llaman a [\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) para generar un informe de depuración. La macro `_ASSERT` imprime un mensaje de diagnóstico simple, `_ASSERTE` incluye una representación de cadena de la expresión del error en el mensaje y `_ASSERT_EXPR` incluye la cadena `message` en el mensaje de diagnóstico. Estas macros no hacen nada cuando `booleanExpression` se evalúa como un valor diferente a cero.  
  
 `_ASSERT_EXPR`, `_ASSERT` y `_ASSERTE` invocan `_CrtDbgReportW`, lo que hace que toda la salida esté en caracteres anchos.`_ASSERTE` imprime correctamente los caracteres Unicode en `booleanExpression` y `_ASSERT_EXPR` imprime caracteres Unicode en `message`.  
  
 Dado que la macro `_ASSERTE` especifica la expresión del error y que `_ASSERT_EXPR` permite especificar un mensaje en el informe generado, permiten que los usuarios identifiquen el problema sin hacer referencia al código fuente. Sin embargo, existe una desventaja en el sentido de que se incluye cada `message` que se imprime por `_ASSERT_EXPR` y cada expresión evaluada por `_ASSERTE` en el archivo de salida \(versión de depuración\) de la aplicación como una constante de cadena. Por tanto, si se realiza un gran número de llamadas a `_ASSERT_EXPR` o `_ASSERTE`, estas expresiones pueden aumentar considerablemente el tamaño del archivo de salida.  
  
 A menos que se especifique lo contrario con las funciones [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) y [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md), aparecen mensajes en un cuadro de diálogo emergente equivalente a establecer lo siguiente:  
  
```c  
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);  
```  
  
 `_CrtDbgReportW` genera el informe de depuración y determina los destinos en función de los modos de informe actuales y el archivo definidos para el tipo de informe `_CRT_ASSERT`. De manera predeterminada, los errores de aserción y los demás errores se dirigen a una ventana de mensajes de depuración. Las funciones [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) y [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) se usan para definir los destinos de cada tipo de informe.  
  
 Cuando el destino es una ventana de mensaje de depuración y el usuario hace clic en el botón **Reintentar**, `_CrtDbgReportW` devuelve 1, lo que hace que las macros `_ASSERT_EXPR`, `_ASSERT` y `_ASSERTE` inicien el depurador siempre que está habilitada la depuración just\-in\-time \(JIT\).  
  
 Para más información sobre el proceso de creación de informes, vea la función [\_CrtDbgReport, \_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md). Para más información sobre cómo resolver errores de aserción y usar estas macros como mecanismo de control de errores de depuración, vea [Uso de macros para comprobación e informes](../Topic/Macros%20for%20Reporting.md).  
  
 Además de las macros `_ASSERT`, la macro [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md) se puede usar para comprobar la lógica del programa. Esta macro está disponible en las versiones de lanzamiento y depuración de las bibliotecas. Las macros de depuración [\_RPT, \_RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) también están disponibles para generar un informe de depuración, pero no evalúan una expresión. Las macros `_RPT` generan un informe sencillo. Las macros `_RPTF` incluyen el número de línea y el archivo de origen donde se llamó a la macro de informe en el informe generado. Las versiones de caracteres anchos de estas macros están disponibles \(`_RPTWn`, `_RPTFWn`\). Las versiones de caracteres anchos son idénticas a las versiones de caracteres estrechos, salvo que se usan cadenas de caracteres anchos para todos los parámetros de cadena y la salida.  
  
 Aunque `_ASSERT_EXPR`, `_ASSERT` y `_ASSERTE` son macros y están disponibles mediante la inclusión de \< crtdbg.h \>, la aplicación debe vincularse a una versión de depuración de la biblioteca de tiempo de ejecución de C cuando se define `_DEBUG`, ya que estas macros llaman a otras funciones en tiempo de ejecución.  
  
## Requisitos  
  
|Macro|Encabezado necesario|  
|-----------|--------------------------|  
|`_ASSERT_EXPR`, `_ASSERT`, `_ASSERTE`|\<crtdbg.h\>|  
  
## Ejemplo  
 En este programa, se realizan llamadas a las macros `_ASSERT` y `_ASSERTE` para probar la condición `string1 == string2`. Si se produce un error en la condición, estas macros imprimen un mensaje de diagnóstico. También se aplican el grupo de macros `_RPTn` y `_RPTFn` en este programa como alternativa a la función `printf`.  
  
```  
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
Use las macros de aserción para evaluar la expresión p1 == p2. crt_ASSERT_macro.c(54) : Will _ASSERT find 'I am p1' == 'I am p2' ? crt_ASSERT_macro.c(55): error de aserción. ¿crt_assert_macro.c(58): _ASSERTE encontrará 'Estoy p1' == 'Estoy p2'? crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2 'I am p1' != 'I am p2'  
```  
  
## Equivalente en .NET Framework  
 [System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)  
  
## Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [assert \(macro\), \_assert, \_wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [\_RPT, \_RPTF, \_RPTW, \_RPTFW \(Macros\)](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)