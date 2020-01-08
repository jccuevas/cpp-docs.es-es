---
title: función Main y argumentos de la línea deC++comandos ()
description: La función main es el punto de entrada de C++ un programa.
ms.date: 12/10/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
ms.openlocfilehash: 95e774700c63dc815f6d814bfda84a38a38d4e6e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302413"
---
# <a name="main-function-and-command-line-arguments"></a>función Main y argumentos de la línea de comandos

Todos C++ los programas deben tener una función `main`. Si intenta compilar un C++ proyecto *. exe* sin una función Main, el compilador producirá un error. (Las bibliotecas de vínculos dinámicos y las bibliotecas estáticas no tienen una función `main`). La función `main` es donde comienza la ejecución del código fuente, pero antes de que un programa entre en la función `main`, todos los miembros de clase estáticos sin inicializadores explícitos se establecen en cero. En Microsoft C++, los objetos estáticos globales también se inicializan antes de la entrada para `main`. Se aplican varias restricciones a la función `main` que no se aplican C++ a otras funciones. La función `main`:

- No se puede sobrecargar (vea [sobrecarga de funciones](function-overloading.md)).
- No se puede declarar como **inline**.
- No se puede declarar como **static**.
- No se puede tomar su dirección.
- No se puede llamar.

La sintaxis de declaración de `main` es la siguiente:

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Específicos de Microsoft**

Si los archivos de código fuente utilizan caracteres anchos de Unicode, puede utilizar `wmain`, que es la versión con caracteres anchos de `main`. La sintaxis de declaración de `wmain` es la siguiente:

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

También puede usar `_tmain`, que se define en TCHAR. h. `_tmain` se resuelve en `main` a menos que se defina _UNICODE. En ese caso, `_tmain` se resuelve en `wmain`.

Si no se especifica ningún valor devuelto, el compilador proporciona un valor devuelto de cero. Como alternativa, las funciones `main` y `wmain` se pueden declarar como si devolvieran **void** (ningún valor devuelto). Si declara `main` o `wmain` como si devolviera **void**, no puede devolver un código de salida al proceso primario o al sistema operativo mediante una instrucción [Return](../cpp/return-statement-in-program-termination-cpp.md) . Para devolver un código de salida cuando `main` o `wmain` se declara como **void**, debe usar la función [Exit](../cpp/exit-function.md) .

**FIN de Específicos de Microsoft**

## <a name="command-line-arguments"></a>Argumentos de línea de comandos

Los argumentos de `main` o `wmain` permiten un análisis práctico de la línea de comandos y, opcionalmente, el acceso a las variables de entorno. El lenguaje define los tipos `argc` y `argv`. Los nombres `argc`, `argv`y `envp` son tradicionales, pero puede asignarles el nombre que desee.

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

Las definiciones de los argumentos son las siguientes:

*argc*<br/>
Entero que contiene el recuento de argumentos que siguen en *argv*. El parámetro *argc* siempre es mayor o igual que 1.

*argv*<br/>
Una matriz de cadenas terminadas en null que representan los argumentos de la línea de comandos especificados por el usuario del programa. Por Convención, `argv[0]` es el comando con el que se invoca el programa, `argv[1]` es el primer argumento de la línea de comandos, etc., hasta `argv[argc]`, que es siempre NULL. Vea [personalizar el procesamiento de línea de comandos](../cpp/customizing-cpp-command-line-processing.md) para obtener información sobre cómo suprimir el procesamiento de línea de comandos.

El primer argumento de la línea de comandos siempre es `argv[1]` y el último es `argv[argc - 1]`.

> [!NOTE]
> Por Convención, `argv[0]` es el comando con el que se invoca el programa. Sin embargo, es posible generar un proceso mediante [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) y, si usa el primer y el segundo argumento (*lpApplicationName* y *lpCommandLine*), es posible que `argv[0]` no sea el nombre del archivo ejecutable; Use [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) para recuperar el nombre del archivo ejecutable y su ruta de acceso completa.

**Específicos de Microsoft**

*envp*<br/>
La matriz *envp* , que es una extensión común en muchos sistemas UNIX, se utiliza en Microsoft C++. Es una matriz de cadenas que representan las variables establecidas en el entorno de usuario. Esta matriz termina con una entrada NULL. Se puede declarar como una matriz de punteros a **Char** (`char *envp[]`) o como un puntero a los punteros a **Char** (`char **envp`). Si el programa usa `wmain` en lugar de `main`, utilice el tipo de datos **wchar_t** en lugar de **Char**. El bloque de entorno que se pasa a `main` y `wmain` es una copia "inmovilizada" del entorno actual. Si posteriormente cambia el entorno mediante una llamada a `putenv` o `_wputenv`, el entorno actual (devuelto por `getenv` o `_wgetenv` y la variable `_environ` o `_wenviron`) cambiará, pero el bloque señalado por envp no cambiará. Consulte [personalizar el procesamiento](../cpp/customizing-cpp-command-line-processing.md) de la línea de comandos para obtener información sobre cómo suprimir el procesamiento del entorno. Este argumento es compatible con ANSI en C, pero no en C++.

**FIN de Específicos de Microsoft**

### <a name="example"></a>Ejemplo

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

## <a name="parsing-c-command-line-arguments"></a>Analizar C++ argumentos de la línea de comandos

**Específicos de Microsoft**

El código de inicio de Microsoft C/C++ utiliza las reglas siguientes al interpretar los argumentos empleados en la línea de comandos del sistema operativo:

- Los argumentos van delimitados por espacio en blanco, que puede ser un carácter de espacio o una tabulación.

- El carácter de intercalación (^) no se reconoce como carácter de escape ni como delimitador. El analizador de la línea de comandos del sistema operativo procesa completamente este carácter antes de pasarlo a la matriz `argv` del programa.

- Una cadena delimitada por comillas dobles ("*cadena*") se interpreta como un solo argumento, independientemente del espacio en blanco incluido en. Se puede incrustar una cadena entre comillas dentro de un argumento.

- Unas comillas precedidas por una barra diagonal inversa (\\") se interpretan como un literal de cadena de comillas (").

- Las barras diagonales inversas se interpretan literalmente, a menos que precedan inmediatamente a unas comillas.

- Si a un número par de barras diagonales inversas le sigue una comilla doble, se coloca una barra diagonal inversa en la matriz `argv` por cada par de barras diagonales inversa y se interpreta la comilla doble como un delimitador de cadenas.

- Si a un número impar de barras diagonales inversas le sigue una comilla doble, se coloca una barra diagonal inversa en la matriz `argv` por cada par de barras diagonales inversas y se interpreta la comilla doble como un carácter de escape gracias a la barra diagonal inversa restante, haciendo que se ponga una comilla doble literal (") en `argv`.

### <a name="example"></a>Ejemplo

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

### <a name="results-of-parsing-command-lines"></a>Resultados del análisis de líneas de comandos

|Entrada de la línea de comandos|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**FIN de Específicos de Microsoft**

## <a name="wildcard-expansion"></a>Expansión de caracteres comodín

**Específicos de Microsoft**

Puede utilizar caracteres comodín (signo de interrogación (?) y asterisco (*)) para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.

Los argumentos de línea de comandos se controlan mediante una rutina llamada `_setargv` (o `_wsetargv` en el entorno de caracteres anchos), que, de forma predeterminada, no expande los caracteres comodín en cadenas independientes en la matriz de cadenas de `argv`. Para obtener más información sobre cómo habilitar la expansión de caracteres comodín, consulte [expandir argumentos comodín](../c-language/expanding-wildcard-arguments.md).

**FIN de Específicos de Microsoft**

## <a name="customizing-c-command-line-processing"></a>Personalizar el procesamiento de línea de comandos de C++

**Específicos de Microsoft**

Si el programa no acepta argumentos de línea de comandos, puede guardar una pequeña cantidad de espacio suprimiendo el uso de la rutina de biblioteca que realiza el procesamiento de la línea de comandos. Esta rutina se denomina `_setargv` y se describe en [expansión de caracteres comodín](../cpp/wildcard-expansion.md). Para suprimir su uso, defina una rutina que no hace nada en el archivo que contiene la función `main` y asígnele el nombre `_setargv`. A continuación, la definición de `_setargv`satisface la llamada a `_setargv` y no se carga la versión de la biblioteca.

Del mismo modo, si nunca tiene acceso a la tabla de entorno mediante el argumento `envp`, puede proporcionar su propia rutina vacía para usar en lugar de `_setenvp`, la rutina de procesamiento de entorno. Al igual que con la función `_setargv`, `_setenvp` se debe declarar como **extern "C"** .

El programa puede realizar llamadas a la familia de rutinas `spawn` o `exec` en la biblioteca en tiempo de ejecución de C. Si es así, no debe suprimir la rutina de procesamiento de entorno, puesto que esta rutina se utiliza para pasar un entorno del proceso primario al proceso secundario.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)