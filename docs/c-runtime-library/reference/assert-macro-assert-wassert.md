---
title: assert (Macro), _assert, _wassert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- assert
- _assert
- _wassert
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 97bdb002953c07aba3bf7951a6f94a058c977f9d
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="assert-macro-assert-wassert"></a>assert (macro), _assert, _wassert
Evalúa una expresión y, cuando el resultado es `false`, imprime un mensaje de diagnóstico y anula el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
assert(   
   expression   
);  
void _assert(  
   char const* message,  
   char const* filename,  
   unsigned line  
);  
void _wassert(  
   wchar_t const* message,  
   wchar_t const* filename,  
   unsigned line  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `expression`  
 Una expresión escalar (incluidas las expresiones de puntero) que se evalúa en un valor que no es cero (`true`) o 0 (`false`).  
  
 `message`  
 Mensaje que se va a mostrar.  
  
 `filename`  
 Nombre del archivo de origen en el que la aserción generó error.  
  
 `line`  
 Número de línea del archivo de origen de la aserción con error.  
  
## <a name="remarks"></a>Comentarios  
 La macro `assert` se usa normalmente para identificar errores lógicos durante el desarrollo del programa. Úsela para detener la ejecución del programa cuando se produzcan condiciones inesperadas implementando el argumento `expression` para evaluar en `false` solo cuando el programa está funcionando incorrectamente. Se pueden desactivar las comprobaciones de aserción en tiempo de compilación definiendo la macro `NDEBUG`. Puede desactivar la macro `assert` sin modificar sus archivos de origen mediante una opción de la línea de comandos **/DNDEBUG** . Puede desactivar la macro `assert` del código fuente mediante una directiva `#define NDEBUG` antes de incluir \<assert.h>.  
  
 La macro `assert` imprime un mensaje de diagnóstico cuando `expression` se evalúa en `false` (0) y llama a [abort](../../c-runtime-library/reference/abort.md) para finalizar la ejecución del programa. No se realiza ninguna acción si `expression` es `true` (distinto de cero). El mensaje de diagnóstico incluye la expresión del error, el nombre del archivo de origen y el número de línea en el que se produjo el error de la aserción.  
  
 El mensaje de diagnóstico se imprime en caracteres anchos. Por lo tanto, funcionará como se espera incluso si hay caracteres Unicode en la expresión.  
  
 El destino del mensaje de diagnóstico depende del tipo de aplicación que llamó a la rutina. Las aplicaciones de consola siempre reciben el mensaje a través de `stderr`. En una aplicación basada en Windows, `assert` llama a la función [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) de Windows para crear un cuadro de mensaje que muestre el mensaje junto con un botón **Aceptar** . Cuando el usuario hace clic en **Aceptar**, el programa se anula inmediatamente.  
  
 Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución, `assert` crea un cuadro de mensaje con tres botones: **Anular**, **Reintentar**e **Ignorar**. Si el usuario hace clic en **Anular**, el programa se anula inmediatamente. Si el usuario hace clic en **Reintentar**, se llama el depurador y el usuario puede depurar el programa si está habilitada la depuración just-in-time (JIT). Si el usuario hace clic en **Ignorar**, `assert` continúa con su ejecución normal: creando el cuadro de mensaje con el botón **Aceptar** . Observe que si se hace clic en **Ignorar** cuando existe una condición de error, se puede producir un comportamiento indefinido.  
  
 Para más información sobre la depuración, vea [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
 Las funciones `_assert` y `_wassert` son funciones de CRT internas. Ayudan a minimizar el código necesario en sus archivos de objeto para admitir aserciones. No se recomienda llamar a estas funciones directamente.  
  
 La macro `assert` está habilitada tanto en la versión de lanzamiento como en la versión de depuración de las bibliotecas en tiempo de ejecución de C cuando `NDEBUG` no está definido. Cuando se define `NDEBUG` , la macro está disponible pero no evalúa su argumento y no tiene ningún efecto. Cuando se habilita, la macro `assert` llama a `_wassert` para su implementación. Otras macros de aserción, [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) y [_ASSERT_EXPR](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), también están disponibles, pero solo evalúan las expresiones que se les pasan cuando se ha definido la macro [_DEBUG](../../c-runtime-library/debug.md) y cuando están en código vinculado con la versión de depuración de las bibliotecas en tiempo de ejecución de C.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`assert`, `_wassert`|\<assert.h>|  
  
 La firma de la función `_assert` no está disponible en un archivo de encabezado. La firma de la función `_wassert` solo está disponible cuando la macro `NDEBUG` no está definida.  
  
## <a name="example"></a>Ejemplo  
 En este programa, la función `analyze_string` usa la macro `assert` para probar varias condiciones relacionadas con la cadena y la longitud. Si se produce un error en cualquiera de las condiciones, el programa imprime un mensaje que indica la causa del error.  
  
```  
// crt_assert.c  
// compile by using: cl /W4 crt_assert.c  
#include <stdio.h>  
#include <assert.h>  
#include <string.h>  
  
void analyze_string( char *string );   // Prototype  
  
int main( void )  
{  
   char  test1[] = "abc", *test2 = NULL, test3[] = "";  
  
   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );  
   analyze_string( test1 );  
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );  
   analyze_string( test2 );  
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );  
   analyze_string( test3 );  
}  
  
// Tests a string to see if it is NULL,   
// empty, or longer than 0 characters.  
void analyze_string( char * string )  
{  
   assert( string != NULL );        // Cannot be NULL  
   assert( *string != '\0' );       // Cannot be empty  
   assert( strlen( string ) > 2 );  // Length must exceed 2  
}  
```  
  
 El programa genera esta salida:  
  
```Output  
Analyzing string 'abc'  
Analyzing string '(null)'  
Assertion failed: string != NULL, file crt_assert.c, line 25  
```  
  
 Tras el error de aserción, según la versión del sistema operativo y la biblioteca en tiempo de ejecución, puede ver un cuadro de mensaje que contiene algo similar a lo siguiente:  
  
```Output  
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.  
```  
  
 Si hay un depurador instalado, elija el botón **Depurar** para iniciar el depurador o **Cerrar programa** , para salir.  
  
## <a name="see-also"></a>Vea también  
 [Control de errores](../../c-runtime-library/error-handling-crt.md)   
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [raise](../../c-runtime-library/reference/raise.md)   
 [signal](../../c-runtime-library/reference/signal.md)   
 [_ASSERT, _ASSERTE, _ASSERT_EXPR (Macros)](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [_DEBUG](../../c-runtime-library/debug.md)
