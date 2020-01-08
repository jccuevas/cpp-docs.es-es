---
title: C++finalización del programa
ms.date: 12/10/2019
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
ms.openlocfilehash: a0e86cacd951327d39296a183be5ee4fbc36fd15
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301345"
---
# <a name="c-program-termination"></a>C++finalización del programa

En C++, puede salir de un programa de las siguientes maneras:

- Llame a la función [Exit](exit-function.md) .
- Llame a la función [Abort](abort-function.md) .
- Ejecute una instrucción [Return](return-statement-cpp.md) desde `main`.

## <a name="exit-function"></a>exit (Función)

La función [Exit](../c-runtime-library/reference/exit-exit-exit.md) , declarada en \<> stdlib. h, finaliza C++ un programa. El valor proporcionado como argumento para `exit` se devuelve al sistema operativo como el código de retorno o el código de salida del programa. Por convención, un código de retorno de cero significa que el programa se completó correctamente. Puede usar las constantes EXIT_FAILURE y EXIT_SUCCESS, también definidas en \<> stdlib. h, para indicar si el programa se ha realizado correctamente o no.

La emisión de una instrucción **Return** a partir de la función `main` es equivalente a llamar a la función `exit` con el valor devuelto como su argumento.

## <a name="abort-function"></a>abort (función)

La función [Abort](../c-runtime-library/reference/abort.md) , también declarada en el archivo de inclusión estándar \<stdlib. h >, C++ finaliza un programa. La diferencia entre `exit` y `abort` es que `exit` permite que C++ tenga lugar el procesamiento de finalización en tiempo de ejecución (se llamará a los destructores de objeto globales), mientras que `abort` finaliza el programa inmediatamente. La función `abort` omite el proceso de destrucción normal de los objetos estáticos globales inicializados. También omite cualquier procesamiento especial que se especificó mediante la función [AtExit](../c-runtime-library/reference/atexit.md) .

## <a name="atexit-function"></a>atexit (función)

Utilice la función [AtExit](../c-runtime-library/reference/atexit.md) para especificar las acciones que se ejecutan antes de la finalización del programa. Ninguno de los objetos estáticos globales inicializados antes de la llamada a **AtExit** se destruye antes de la ejecución de la función de procesamiento de salida.

## <a name="return-statement-in-main"></a>instrucción return en Main

La emisión de una instrucción [Return](return-statement-cpp.md) desde `main` es funcionalmente equivalente a llamar a la función `exit`. Considere el ejemplo siguiente:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Las instrucciones `exit` y **Return** del ejemplo anterior son funcionalmente idénticas. Sin embargo C++ , requiere que las funciones que tienen tipos de valor devuelto distintos de **void** devuelvan un valor. La instrucción **Return** le permite devolver un valor de `main`.

## <a name="destruction-of-static-objects"></a>Destrucción de objetos estáticos

Cuando se llama a `exit` o se ejecuta una instrucción **Return** de `main`, los objetos estáticos se destruyen en el orden inverso a la inicialización (después de la llamada a `atexit` si existe). En el ejemplo siguiente se muestra cómo funcionan esa inicialización y limpieza.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, los objetos estáticos `sd1` y `sd2` se crean e inicializan antes de la entrada a `main`. Una vez que este programa finaliza con la instrucción **Return** , primero se destruye `sd2` y, a continuación, se `sd1`. El destructor para la clase de `ShowData` cierra los archivos asociados a estos objetos estáticos.

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

[main: Inicio de programa](main-program-startup.md)