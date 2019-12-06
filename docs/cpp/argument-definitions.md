---
title: Definiciones de argumentos
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
ms.openlocfilehash: aebd4800ad8d653d532708784ef0a5333211d46b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857663"
---
# <a name="argument-definitions"></a>Definiciones de argumentos

Los argumentos del prototipo

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

proporcionan una manera cómoda de analizar los argumentos en la línea de comandos y, opcionalmente, acceder a las variables de entorno. Las definiciones de los argumentos son las siguientes:

*argc*<br/>
Entero que contiene el recuento de argumentos que siguen en *argv*. El parámetro *argc* siempre es mayor o igual que 1.

*argv*<br/>
Una matriz de cadenas terminadas en null que representan los argumentos de la línea de comandos especificados por el usuario del programa. Por Convención, `argv[0]` es el comando con el que se invoca el programa, `argv[1]` es el primer argumento de la línea de comandos, etc., hasta `argv[argc]`, que es siempre NULL. Vea [personalizar el procesamiento de línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento de línea de comandos.

El primer argumento de la línea de comandos siempre es `argv[1]` y el último es `argv[argc - 1]`.

> [!NOTE]
> Por Convención, `argv[0]` es el comando con el que se invoca el programa.  Sin embargo, es posible generar un proceso mediante [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) y, si usa el primer y el segundo argumento (*lpApplicationName* y *lpCommandLine*), es posible que `argv[0]` no sea el nombre del archivo ejecutable; Use [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) para recuperar el nombre del archivo ejecutable y su ruta de acceso completa.

**Específicos de Microsoft**

*envp*<br/>
La matriz *envp* , que es una extensión común en muchos sistemas UNIX, se utiliza en Microsoft C++. Es una matriz de cadenas que representan las variables establecidas en el entorno de usuario. Esta matriz termina con una entrada NULL. Se puede declarar como una matriz de punteros a **Char** (`char *envp[]`) o como un puntero a los punteros a **Char** (`char **envp`). Si el programa usa `wmain` en lugar de `main`, utilice el tipo de datos **wchar_t** en lugar de **Char**. El bloque de entorno que se pasa a `main` y `wmain` es una copia "inmovilizada" del entorno actual. Si posteriormente cambia el entorno mediante una llamada a `putenv` o `_wputenv`, el entorno actual (devuelto por `getenv` o `_wgetenv` y la variable `_environ` o `_wenviron`) cambiará, pero el bloque señalado por envp no cambiará. Consulte [personalizar el procesamiento](../cpp/customizing-cpp-command-line-processing.md) de la línea de comandos para obtener información sobre cómo suprimir el procesamiento del entorno. Este argumento es compatible con ANSI en C, pero no en C++.

**FIN de Específicos de Microsoft**

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar los argumentos *argc*, *argv*y *envp* para `main`:

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)