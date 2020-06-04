---
title: Errores potenciales que pasan los objetos de CRT entre los límites de DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 10fbb128698b6422779d09a15fe3c1d25e8de5b5
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446656"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Errores potenciales que pasan los objetos de CRT entre los límites de DLL

Al pasar los objetos de tiempo de ejecución de C (CRT) como identificadores de archivos, configuraciones regionales y variables de entorno en un archivo DLL o fuera de este (llamadas de función a través del límite de DLL), puede producirse un comportamiento inesperado si el archivo DLL, así como los archivos que llamen al archivo DLL, utilizan diferentes copias de las bibliotecas de CRT.

Un problema relacionado puede aparecer cuando asigna memoria (explícitamente con `new` o `malloc`, o implícitamente con `strdup`, `strstreambuf::str`, etc.) y pasa un puntero a través de un límite de DLL para que se libere. Esto puede producir una infracción de acceso de memoria o daños en el montón si el archivo DLL y sus usuarios utilizan diferentes copias de las bibliotecas de CRT.

Otro síntoma de este problema puede ser un error en la ventana de salida durante la depuración, como:

HEAP[]: dirección no válida especificada en RtlValidateHeap(#,#)

## <a name="causes"></a>Causas

Cada copia de la biblioteca de CRT tiene un estado independiente y distinto, que su aplicación o DLL mantiene en el almacenamiento local de subprocesos. Por ello, los objetos de CRT como identificadores de archivos, variables de entorno y configuraciones regionales solo son válidos para la copia de CRT en la aplicación o el archivo DLL donde se asignan o se establecen estos objetos. Cuando el archivo DLL y su clientes de aplicación utilizan varias copias de la biblioteca de CRT, no puede pasar estos objetos de CRT a través del límite de DLL y esperar que se capturen correctamente en el otro lado. Esto es especialmente cierto para las versiones de CRT antes de Universal CRT en Visual Studio 2015 y versiones posteriores. Había una biblioteca de CRT específica para cada una de las versiones de Visual Studio compiladas con Visual Studio 2013 o anterior. Los detalles de implementación internos de CRT, como sus estructuras de datos y las convenciones de nomenclatura, eran diferentes en cada versión. La vinculación dinámica de código compilado para una versión de CRT con otra versión de DLL de CRT nunca se ha admitido, aunque ha podido funcionar eventualmente (más por suerte que por características de diseño).

Además, dado que cada copia de la biblioteca de CRT tiene su propio administrador de montón, la asignación de memoria en una biblioteca de CRT y el hecho de pasar el puntero a través de un límite de DLL que se va a liberar por una copia diferente de la biblioteca de CRT es un posible motivo por el que se pueden producir daños en el montón. Si diseña el archivo DLL para que pase objetos de CRT a través del límite o asigne memoria y espere que se va a liber fuera del archivo DLL, impedirá que los clientes de la aplicación de DLL utilicen la misma copia de la biblioteca CRT que el archivo DLL. El archivo DLL y sus clientes usan normalmente la misma copia de la biblioteca CRT solo si ambos están vinculados en tiempo de carga a la misma versión del archivo DLL de CRT. Dado que la versión de DLL de la biblioteca Universal CRT utilizada por Visual Studio 2015 y posterior en Windows 10 es ahora un componente de Windows implementado de forma centralizada, ucrtbase.dll, es la misma para las aplicaciones compiladas con Visual Studio 2015 y versiones posteriores. Sin embargo, incluso cuando el código de CRT es idéntico, no se puede entregar memoria asignada en un montón a un componente que utilice un montón diferente.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En este ejemplo se pasa un identificador de archivo a través de un límite de DLL.

El archivo DLL y .exe se compilan con /MD, de modo que comparten una única copia de CRT.

Si recompila con /MT para que utilicen copias independientes de CRT, la ejecución del archivo test1Main.exe resultante produce una infracción de acceso.

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

Este ejemplo pasa variables de entorno a través de un límite de DLL.

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

Si el archivo DLL y el archivo .exe se compilan con /MD para utilizar solo una copia de CRT, el programa se ejecuta correctamente y genera el siguiente resultado:

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)
