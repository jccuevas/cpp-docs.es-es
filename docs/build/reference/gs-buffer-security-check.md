---
title: /GS (Comprobación de seguridad del búfer)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 10afa874092eb563903ba5f49c6add136afc869c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820239"
---
# <a name="gs-buffer-security-check"></a>/GS (Comprobación de seguridad del búfer)

Detecta algunas saturaciones de búfer que sobrescriben la dirección de devolución de una función, la dirección del controlador de excepciones o ciertos tipos de parámetros. Producir una saturación del búfer es una técnica utilizada por los piratas informáticos para aprovechar que el código no impone restricciones del tamaño de búfer.

## <a name="syntax"></a>Sintaxis

```
/GS[-]
```

## <a name="remarks"></a>Comentarios

**/GS** está activada de forma predeterminada. Si espera que su aplicación no tenga ningún riesgo de seguridad, utilice **/GS-**. Para obtener más información sobre cómo suprimir la detección de saturación del búfer, vea [safebuffers](../../cpp/safebuffers.md).

## <a name="security-checks"></a>Comprobaciones de seguridad

A las funciones que el compilador reconoce como propensas a problemas de saturación del búfer, les asigna espacio en la pila antes de la dirección de devolución. En la entrada de función, se carga el espacio asignado con un *cookie de seguridad* que se calcula una vez al cargar el módulo. A la salida de la función, y durante el desenredo del marco en los sistemas operativos de 64 bits, se llama a una función del asistente para asegurarse de que el valor de la cookie sigue siendo el mismo. Un valor diferente indica que se puede haber producido una sobrescritura de la pila. Si se detecta un valor diferente, se finaliza el proceso.

## <a name="gs-buffers"></a>Búferes GS

Se realiza una comprobación de seguridad de saturación del búfer en un *búfer GS*. Un búfer GS puede ser uno de los siguientes:

- Una matriz que tiene más de 4 bytes, más de dos elementos y un tipo de elemento que no es un tipo de puntero.

- Una estructura de datos cuyo tamaño es superior a 8 bytes y no contiene punteros.

- Un búfer asignado mediante el uso de la [_alloca](../../c-runtime-library/reference/alloca.md) función.

- Cualquier clase o estructura que contiene un búfer GS.

Por ejemplo, las siguientes instrucciones declaran los búferes GS.

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

Sin embargo, las siguientes instrucciones no declaran búferes GS. Las primeras dos declaraciones contienen elementos de tipo de puntero. Las instrucciones tercera y cuarta declaran matrices cuyo tamaño es demasiado pequeño. La quinta instrucción declara una estructura cuyo tamaño en una plataforma x86 no es superior a 8 bytes.

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>Inicializar la cookie de seguridad

El **/GS** opción del compilador requiere que se inicialice la cookie de seguridad antes de ejecuta cualquier función que usa la cookie. La cookie de seguridad debe inicializarse inmediatamente en la entrada a un archivo EXE o DLL. Esto se hace automáticamente si utiliza los puntos de entrada predeterminada VCRuntime: mainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup, o _DllMainCRTStartup. Si usa un punto de entrada alternativo, debe inicializar manualmente la cookie de seguridad mediante una llamada a [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md).

## <a name="what-is-protected"></a>Lo que está protegido

El **/GS** opción del compilador protege los siguientes elementos:

- La dirección de devolución de una llamada de función.

- La dirección de un controlador de excepciones para una función.

- Parámetros de función vulnerables.

En todas las plataformas, **/GS** intenta detectar saturaciones de búfer en la dirección de retorno. Las saturaciones de búfer se aprovechan con mayor facilidad en plataformas como x86 y x64, que usan convenciones de llamada para almacenar la dirección de devolución de una llamada a función en la pila.

En x86, si una función usa un controlador de excepciones, el compilador inserta una cookie de seguridad para proteger la dirección del controlador de excepciones. La cookie se comprueba durante el desenredo del marco.

**/GS** protege *parámetros vulnerables* que se pasan a una función. Un parámetro vulnerable es un puntero, una referencia de C++, una estructura de C (del tipo POD de C++) que contiene un puntero o un búfer GS.

Un parámetro vulnerable se asigna antes que la cookie y las variables locales. Una saturación del búfer puede sobrescribir estos parámetros. El código de la función que usa estos parámetros puede provocar un ataque antes de que se devuelva la función y se realice la comprobación de seguridad. Para reducir este riesgo, el compilador realiza una copia de los parámetros vulnerables durante el prólogo de la función y los coloca bajo el área de almacenamiento de cualquier búfer.

El compilador no realiza copias de los parámetros vulnerables en las siguientes situaciones:

- Funciones que no contienen un búfer GS.

- Optimizaciones ([opciones /O](o-options-optimize-code.md)) no están habilitadas.

- Funciones que tienen una lista de argumentos de variable (...).

- Las funciones marcadas con [naked](../../cpp/naked-cpp.md).

- Funciones que contienen código de ensamblado insertado en la primera instrucción.

- Un parámetro solo se utiliza de manera que sea poco probable que se pueda usar de forma malintencionada en caso de una saturación del búfer.

## <a name="what-is-not-protected"></a>Lo que no está protegido

El **/GS** opción del compilador no protege contra todos los ataques de seguridad de saturación del búfer. Por ejemplo, si tiene un búfer y vtable en un objeto, la saturación de un búfer podría dañar vtable.

Incluso si usa **/GS**, siempre intenta escribir código seguro que no tenga ninguna saturación de búfer.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para establecer esta opción del compilador en Visual Studio

1. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**.

   Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. En el **páginas de propiedades** cuadro de diálogo, haga clic en el **C o C++** carpeta.

1. Haga clic en el **generación de código** página de propiedades.

1. Modificar el **Buffer Security Check** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.

## <a name="example"></a>Ejemplo

En este ejemplo se satura un búfer. Esto produce un error de la aplicación en tiempo de ejecución.

```C
// compile with: /c /W1
#include <cstring>
#include <stdlib.h>
#pragma warning(disable : 4996)   // for strcpy use

// Vulnerable function
void vulnerable(const char *str) {
   char buffer[10];
   strcpy(buffer, str); // overrun buffer !!!

   // use a secure CRT function to help prevent buffer overruns
   // truncate string to fit a 10 byte buffer
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);
}

int main() {
   // declare buffer that is bigger than expected
   char large_buffer[] = "This string is longer than 10 characters!!";
   vulnerable(large_buffer);
}
```

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
