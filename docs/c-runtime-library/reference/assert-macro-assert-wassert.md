---
title: assert (Macro), _assert, _wassert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1d2bef607e80e2e972915bd8a8b0517b7c6e5eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200672"
---
# <a name="assert-macro-assert-wassert"></a>assert (macro), _assert, _wassert

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

*expresión* una expresión escalar (incluidas las expresiones de puntero) que se evalúa como distinto de cero a (**true**) o 0 (**false**).

*mensaje* el mensaje para mostrar.

*nombre de archivo* el nombre del origen de archivo de la aserción no se pudo en.

*línea* el número de línea en el archivo de origen de la aserción con errores.

## <a name="remarks"></a>Comentarios

El **assert** macro se usa normalmente para identificar errores lógicos durante el desarrollo del programa. Úsela para detener la ejecución del programa cuando se produzcan condiciones inesperadas implementando el *expresión* argumento se evalúe como **false** solo cuando el programa está funcionando incorrectamente. Se pueden desactivar las comprobaciones de aserción en tiempo de compilación definiendo la macro **NDEBUG**. Puede desactivar la **assert** macro sin modificar los archivos de origen mediante un **/DNDEBUG** opción de línea de comandos. Puede desactivar la **assert** macro en el código fuente mediante el uso de un `#define NDEBUG` la directiva antes de \<assert.h > se incluye.

El **assert** un mensaje de diagnóstico cuando se imprime macro *expresión* se evalúa como **false** (0) y llama a [anular](abort.md) para finalizar el programa ejecución. Se realiza ninguna acción si *expresión* es **true** (distinto de cero). El mensaje de diagnóstico incluye la expresión del error, el nombre del archivo de origen y el número de línea en el que se produjo el error de la aserción.

El mensaje de diagnóstico se imprime en caracteres anchos. Por lo tanto, funcionará como se espera incluso si hay caracteres Unicode en la expresión.

El destino del mensaje de diagnóstico depende del tipo de aplicación que llamó a la rutina. Las aplicaciones de consola siempre reciben el mensaje a través **stderr**. En una aplicación basada en Windows, **assert** llama a la Windows [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) función para crear un cuadro de mensaje para mostrar el mensaje junto con un **Aceptar** botón. Cuando el usuario hace clic en **Aceptar**, el programa se anula inmediatamente.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución, **assert** crea un cuadro de mensaje con tres botones: **anular**, **vuelva a intentar**y **Omitir**. Si el usuario hace clic en **Anular**, el programa se anula inmediatamente. Si el usuario hace clic en **Reintentar**, se llama el depurador y el usuario puede depurar el programa si está habilitada la depuración just-in-time (JIT). Si el usuario hace clic **omitir**, **assert** continúa con su ejecución normal: creando el cuadro de mensaje con el **Aceptar** botón. Observe que si se hace clic en **Ignorar** cuando existe una condición de error, se puede producir un comportamiento indefinido.

Para más información sobre la depuración, vea [Técnicas de depuración de CRT](/visualstudio/debugger/crt-debugging-techniques).

El **_assert** y **_wassert** funciones son funciones de CRT internas. Ayudan a minimizar el código necesario en sus archivos de objeto para admitir aserciones. No se recomienda llamar a estas funciones directamente.

El **assert** macro está habilitada en las versiones de lanzamiento y depuración de las bibliotecas de tiempo de ejecución de C cuando **NDEBUG** no está definido. Cuando **NDEBUG** está definido, la macro está disponible, pero no evalúa su argumento y no tiene ningún efecto. Cuando se habilita, el **assert** llamadas a macros **_wassert** para su implementación. Otras macros de aserción, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) y [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), también están disponibles, pero solo evalúan las expresiones que se les pasan cuando se ha definido la macro [_DEBUG](../../c-runtime-library/debug.md) y cuando están en código vinculado con la versión de depuración de las bibliotecas en tiempo de ejecución de C.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**Assert**, **_wassert**|\<assert.h>|

La firma de la **_assert** función no está disponible en un archivo de encabezado. La firma de la **_wassert** función solo está disponible cuando el **NDEBUG** no está definida la macro.

## <a name="example"></a>Ejemplo

En este programa, el **analyze_string** función usa el **assert** macro para probar varias condiciones relacionadas con la cadena y longitud. Si se produce un error en cualquiera de las condiciones, el programa imprime un mensaje que indica la causa del error.

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
