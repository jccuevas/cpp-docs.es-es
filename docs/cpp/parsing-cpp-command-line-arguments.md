---
title: Analizar los argumentos de la línea de comandos de C++
ms.date: 11/04/2016
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
ms.openlocfilehash: 53873fa9340253ab5e8459eb442385641246f930
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471037"
---
# <a name="parsing-c-command-line-arguments"></a>Analizar los argumentos de la línea de comandos de C++

**Específicos de Microsoft**

El código de inicio de Microsoft C/C++ utiliza las reglas siguientes al interpretar los argumentos empleados en la línea de comandos del sistema operativo:

- Los argumentos van delimitados por espacio en blanco, que puede ser un carácter de espacio o una tabulación.

- El carácter de intercalación (^) no se reconoce como carácter de escape ni como delimitador. El analizador de la línea de comandos del sistema operativo procesa completamente este carácter antes de pasarlo a la matriz `argv` del programa.

- Una cadena entrecomillada comillas dobles ("*cadena*") se interpreta como un solo argumento, sin importar el espacio en blanco dentro de. Se puede incrustar una cadena entre comillas dentro de un argumento.

- Unas comillas precedidas por una barra diagonal inversa (\\") se interpretan como un literal de cadena de comillas (").

- Las barras diagonales inversas se interpretan literalmente, a menos que precedan inmediatamente a unas comillas.

- Si a un número par de barras diagonales inversas le sigue una comilla doble, se coloca una barra diagonal inversa en la matriz `argv` por cada par de barras diagonales inversa y se interpreta la comilla doble como un delimitador de cadenas.

- Si a un número impar de barras diagonales inversas le sigue una comilla doble, se coloca una barra diagonal inversa en la matriz `argv` por cada par de barras diagonales inversas y se interpreta la comilla doble como un carácter de escape gracias a la barra diagonal inversa restante, haciendo que se ponga una comilla doble literal (") en `argv`.

## <a name="example"></a>Ejemplo

En el programa siguiente se muestra cómo se pasan los argumentos de la línea de comandos:

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

En la tabla siguiente se muestra una entrada de ejemplo y la salida esperada para mostrar las reglas de la lista anterior.

### <a name="results-of-parsing-command-lines"></a>Resultados de analizar las líneas de comandos

|Entrada de la línea de comandos|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[main: Inicio de programa](../cpp/main-program-startup.md)