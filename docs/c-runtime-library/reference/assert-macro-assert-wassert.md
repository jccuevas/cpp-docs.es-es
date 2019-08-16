---
title: assert (macro), _assert, _wassert
ms.date: 11/04/2016
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
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: a2cc780fbc93aa66bd7fd613c3e155cda27eb7f9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500337"
---
# <a name="assert-macro-_assert-_wassert"></a>assert (macro), _assert, _wassert

Evalúa una expresión y, cuando el resultado es **false**, imprime un mensaje de diagnóstico y anula el programa.

## <a name="syntax"></a>Sintaxis

```C
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

### <a name="parameters"></a>Parámetros

*expression*<br/>
Una expresión escalar (incluidas las expresiones de puntero) que se evalúa como un valor distinto de cero (**true**) o 0 (**false**).

*message*<br/>
Mensaje que se va a mostrar.

*filename*<br/>
Nombre del archivo de origen en el que la aserción generó error.

*line*<br/>
Número de línea del archivo de origen de la aserción con error.

## <a name="remarks"></a>Comentarios

La macro Assert se usa normalmente para identificar errores lógicos durante el desarrollo del programa. Úselo para detener la ejecución del programa cuando se producen condiciones inesperadas implementando el argumento de *expresión* para evaluar como **false** solo cuando el programa está funcionando incorrectamente. Las comprobaciones de aserción pueden desactivarse en tiempo de compilación definiendo la macro **NDEBUG**. Puede desactivar la macro **Assert** sin modificar los archivos de origen mediante una opción de línea de comandos **/DNDEBUG** . Puede desactivar la macro Assert en el código fuente mediante una `#define NDEBUG` Directiva antes \<de que se incluya Assert. h >.

La macro Assert imprime un mensaje de diagnóstico cuando *Expression* se evalúa como **false** (0) y llama a [Abort](abort.md) para finalizar la ejecución del programa. No se realiza ninguna acción si la *expresión* es **true** (distinto de cero). El mensaje de diagnóstico incluye la expresión del error, el nombre del archivo de origen y el número de línea en el que se produjo el error de la aserción.

El mensaje de diagnóstico se imprime en caracteres anchos. Por lo tanto, funcionará como se espera incluso si hay caracteres Unicode en la expresión.

El destino del mensaje de diagnóstico depende del tipo de aplicación que llamó a la rutina. Las aplicaciones de consola siempre reciben el mensaje a través de **stderr**. En una aplicación basada en Windows, **Assert** llama a la función [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) de Windows para crear un cuadro de mensaje que muestre el mensaje junto con un botón **Aceptar** . Cuando el usuario hace clic en **Aceptar**, el programa se anula inmediatamente.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución, Assert crea un cuadro de mensaje con tres botones: **Anular**, **Reintentar**y **omitir**. Si el usuario hace clic en **Anular**, el programa se anula inmediatamente. Si el usuario hace clic en **Reintentar**, se llama el depurador y el usuario puede depurar el programa si está habilitada la depuración just-in-time (JIT). Si el usuario hace clicen omitir, Assert continúa con su ejecución normal: creando el cuadro de mensaje con el botón **Aceptar** . Observe que si se hace clic en **Ignorar** cuando existe una condición de error, se puede producir un comportamiento indefinido.

Para más información sobre la depuración, vea [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

Las funciones _ Assert y **wassert** son funciones de CRT internas. Ayudan a minimizar el código necesario en sus archivos de objeto para admitir aserciones. No se recomienda llamar a estas funciones directamente.

La macro Assert está habilitada en las versiones de lanzamiento y depuración de las bibliotecas en tiempo de ejecución de C cuando no se define **NDEBUG** . Cuando se define **NDEBUG** , la macro está disponible pero no evalúa su argumento y no tiene ningún efecto. Cuando está habilitada, la macro Assert llama a **wassert** para su implementación. Otras macros de aserción, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) y [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), también están disponibles, pero sólo evalúan las expresiones que se les pasan cuando la macro [_DEBUG](../../c-runtime-library/debug.md) se ha definido y cuando se encuentran en código vinculado con la versión de depuración de las bibliotecas en tiempo de ejecución de C.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**assert**, **_wassert**|\<assert.h>|

La firma de la función _ Assert no está disponible en un archivo de encabezado. La firma de la función **wassert** solo está disponible cuando no se define la macro **NDEBUG** .

## <a name="example"></a>Ejemplo

En este programa, la función **analyze_string** usa la macro Assert para probar varias condiciones relacionadas con la cadena y la longitud. Si se produce un error en cualquiera de las condiciones, el programa imprime un mensaje que indica la causa del error.

```C
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

[Control de errores](../../c-runtime-library/error-handling-crt.md)<br/>
[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
