---
title: C++finalización del programa
description: Describe las formas de exit programa C++de un lenguaje.
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: f83c9d5da5b0a1127603a97fd7946e9cca43a7a5
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123960"
---
# <a name="c-program-termination"></a>C++finalización del programa

En C++, puede exit un programa de las siguientes maneras:

- Llame a la función [exit](exit-function.md) .
- Llame a la función [abort](abort-function.md) .
- Ejecute una instrucción [return](return-statement-cpp.md) a partir de `main`.

## <a name="opno-locexit-function"></a>Función exit

La función [exit](../c-runtime-library/reference/exit-exit-exit.md) , declarada en \<> stdlib. h, finaliza C++ un programa. El valor proporcionado como argumento para `exit` se devuelve al sistema operativo como código de return del programa o código exit. Por Convención, un código return de cero significa que el programa se ha completado correctamente. Puede usar las constantes EXIT_FAILURE y EXIT_SUCCESS, también definidas en \<> stdlib. h, para indicar si el programa se ha realizado correctamente o no.

La emisión de una instrucción **return** desde la función `main` es equivalente a llamar a la función `exit` con el valor return como su argumento.

## <a name="opno-locabort-function"></a>Función abort

La función [abort](../c-runtime-library/reference/abort.md) , también declarada en el archivo de inclusión estándar \<stdlib. h >, C++ finaliza un programa. La diferencia entre `exit` y `abort` es que `exit` permite que C++ tenga lugar el procesamiento de finalización en tiempo de ejecución (se llamará a los destructores de objeto globales), mientras que `abort` finaliza el programa inmediatamente. La función `abort` omite el proceso de destrucción normal de los objetos estáticos globales inicializados. También omite cualquier procesamiento especial que se haya especificado mediante la función [atexit](../c-runtime-library/reference/atexit.md) .

## <a name="opno-locatexit-function"></a>Función atexit

Utilice la función [atexit](../c-runtime-library/reference/atexit.md) para especificar las acciones que se ejecutan antes de la finalización del programa. Ninguno de los objetos estáticos globales inicializados antes de la llamada a **atexit** se destruyen antes de la ejecución de la función de procesamiento de exit.

## <a name="opno-locreturn-statement-in-opno-locmain"></a>return instrucción en main

La emisión de una instrucción [return](return-statement-cpp.md) a partir de `main` es funcionalmente equivalente a llamar a la función `exit`. Considere el ejemplo siguiente:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Las instrucciones `exit` y **return** del ejemplo anterior son funcionalmente idénticas. Sin embargo C++ , requiere que las funciones que tienen tipos de return distintos de **void** return un valor. La instrucción **return** permite return un valor de `main`.

## <a name="destruction-of-static-objects"></a>Destrucción de objetos estáticos

Cuando se llama a `exit` o se ejecuta una instrucción de **return** desde `main`, los objetos estáticos se destruyen en el orden inverso a la inicialización (después de la llamada a `atexit` si existe). En el ejemplo siguiente se muestra cómo funcionan esa inicialización y limpieza.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, los objetos estáticos `sd1` y `sd2` se crean e inicializan antes de la entrada a `main`. Después de que este programa termine de usar la instrucción **return** , se destruye primero `sd2` y, después, se `sd1`. El destructor para la clase de `ShowData` cierra los archivos asociados a estos objetos estáticos.

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

Otra forma de escribir este código es declarar los objetos `ShowData` con ámbito de bloque, lo que permite destruirlos cuando salen del ámbito:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Vea también

[main función y argumentos de la línea de comandos](main-function-command-line-args.md)
