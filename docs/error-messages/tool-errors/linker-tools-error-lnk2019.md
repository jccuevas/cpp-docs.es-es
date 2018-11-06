---
title: Error de las herramientas del vinculador LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: af40a48e36d316842ec9a744ad95d6c3b3af3731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555602"
---
# <a name="linker-tools-error-lnk2019"></a>Error de las herramientas del vinculador LNK2019

símbolo externo sin resolver '*símbolo*'hace referencia en la función'*función*'

El código compilado para *función* hace una referencia o una llamada a *símbolos*, pero este símbolo no está definido en cualquiera de las bibliotecas o archivos de objeto especificados al vinculador.

Este mensaje de error va seguido de un error irrecuperable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Debe corregir todos los LNK2001 y LNK2019 errores para corregir el error LNK1120.

## <a name="possible-causes"></a>Causas posibles

Hay muchas maneras de obtener este error, pero todas ellas implican una referencia a una función o variable que el vinculador no *resolver*, o busque una definición. El compilador puede identificar cuándo un símbolo no es *declarado*, pero no cuando no es *definido*, porque la definición puede estar en un archivo de origen diferente o biblioteca. Si se hace referencia a un símbolo, pero nunca se ha definido, el vinculador genera un error de símbolo externo sin resolver.

Estos son algunos de los problemas comunes que causan LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>El archivo objeto o biblioteca que contiene la definición del símbolo no está vinculado

En Visual Studio, compruebe que el archivo de origen que contiene la definición está compilado y vinculado como parte del proyecto. En la línea de comandos, compruebe que se compila el archivo de origen que contiene la definición y que el archivo objeto resultante se incluye en la lista de archivos que se va a vincular.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>La declaración del símbolo no se escribe igual que la definición del símbolo

Compruebe la ortografía y mayúsculas y minúsculas se usa en la declaración y la definición, y siempre que el símbolo es usar o llamar.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Se utiliza una función pero el tipo o el número de parámetros no coincide con la definición de función

. La declaración de función debe coincidir con su definición. Compruebe que la llamada de función coincide con la declaración y que la declaración coincide con la definición. El código que invoca las funciones de plantilla también debe tener declaraciones de función de plantilla coincidentes que incluyan los mismos parámetros de plantilla que la definición. Para obtener un ejemplo de un error de coincidencia de declaración de plantilla, vea el ejemplo LNK2019e.cpp en la sección ejemplos.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Una función o variable está declarada pero no definida

Esto suele significar una declaración existe en un archivo de encabezado, pero no se implementa la definición correspondiente. En las funciones miembro o miembros de datos estáticos, la implementación debe incluir el selector de ámbito de clase. Para obtener un ejemplo, consulta [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>La convención de llamada es diferente entre la declaración de función y la definición de función

. Las convenciones de llamada ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)o [__vectorcall](../../cpp/vectorcall.md)) se codifican como parte del nombre representativo. Compruebe que la convención de llamada sea la misma.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Un símbolo está definido en un archivo de C, pero declarado sin usar extern "C" en un archivo de C++

. Los símbolos definidos en un archivo que se compila como C tienen nombres representativos diferentes a los símbolos declarados en un archivo de C++, a menos que use un modificador ["C" externo](../../cpp/using-extern-to-specify-linkage.md) . Compruebe que la declaración coincide con la vinculación de compilación para cada símbolo. Del mismo modo, si define un símbolo en un archivo C++ que se usará en un programa C, use `extern "C"` en la definición.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Un símbolo está definido como estático y, a continuación, se le hizo referencia fuera del archivo

. En C++, a diferencia de C, las [constantes globales](../../error-messages/tool-errors/global-constants-in-cpp.md) tienen vinculación `static` . Para solucionar esta limitación, puede incluir las inicializaciones `const` en un encabezado de archivo e incluir dicho encabezado en los archivos .cpp. También puede hacer que la variable no sea constante y usar una referencia constante para obtener acceso.

### <a name="a-static-member-of-a-class-is-not-defined"></a>No se define un miembro estático de una clase

. Un miembro de clase estática debe tener una definición única. En caso contrario, infringe la regla de definición. Un miembro de clase estática que no se pueda definir mediante inserción deberá definirse en un archivo de origen usando su nombre completo. Si no se define en absoluto, el enlazador genera LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Una dependencia de compilación solo se define como una dependencia de proyecto en la solución

En versiones anteriores de Visual Studio, este nivel de dependencia era suficiente. Sin embargo, a partir de Visual Studio 2010, Visual Studio requiere un [referencia de proyecto a proyecto](/visualstudio/ide/managing-references-in-a-project). Si el proyecto no tiene una referencia de proyecto a proyecto, puede que reciba este error del enlazador. Agregue una referencia de proyecto a proyecto para corregir este problema.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Compilar una aplicación de consola mediante la configuración para una aplicación de Windows

Si el mensaje de error es similar a **símbolo externo sin resolver WinMain hace referencia en la función** *function_name*, vincule con **/SUBSYSTEM: Console** en lugar de **/SUBSYSTEM: Windows**. Para obtener más información acerca de esta configuración y para obtener instrucciones sobre cómo establecer esta propiedad en Visual Studio, consulte [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Se intenta vincular bibliotecas de 64 bits a código de 32 bits, o bibliotecas de 32 bits para código de 64 bits

Bibliotecas y archivos objeto vinculados en el código deben compilarse para la misma arquitectura que el código. Compruebe que las bibliotecas de las referencias del proyecto se compilan para la misma arquitectura que el proyecto. Asegúrese de que el [/libpath](../../build/reference/libpath-additional-libpath.md) o **directorios de bibliotecas adicionales** opción de ruta de acceso utilizada por los puntos del vinculador a bibliotecas compiladas con la arquitectura correcta.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Usar opciones de compilador diferentes para la inclusión de funciones en archivos de origen diferentes

. El uso de funciones insertadas definidas en los archivos .cpp y la mezcla de opciones de compilador de inserción de funciones en archivos de origen diferentes puede causar LNK2019. Para obtener más información, consulta [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Use variables automáticas fuera de su ámbito

. Las variables automáticas (de ámbito de función) solo pueden usarse dentro del ámbito de esa función. Estas variables no se pueden declarar `extern` y usar en otros archivos de origen. Para obtener un ejemplo, consulta [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Llame a funciones intrínsecas o pasa tipos de argumentos a funciones intrínsecas que no son compatibles con la arquitectura de destino

. Por ejemplo, si usa una función intrínseca AVX2 pero no especifica la opción del compilador [/ARCH:AVX2](../../build/reference/arch-x86.md) , el compilador supone que la función intrínseca es una función externa. En lugar de generar una instrucción insertada, el compilador genera una llamada a un símbolo externo con el mismo nombre que la función intrínseca. Cuando el enlazador intenta buscar la definición de esta función ausente, genera LNK2019. Compruebe que solo usa funciones intrínsecas y tipos compatibles con la arquitectura de destino.

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>Mezcle código que usa wchar nativo\_t con código que no

. El trabajo de conformidad de lenguaje C++ que se realizó en Visual C++ 2005 convirtió `wchar_t` en un tipo nativo de forma predeterminada. Debe usar la opción del compilador [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para generar código compatible con los archivos de objeto o biblioteca compilados con versiones anteriores de Visual C++. Si no todos los archivos se han compilado con la misma **/Zc:wchar\_t** configuración, el tipo no pueden resolver las referencias a tipos compatibles. Compruebe que los tipos `wchar_t` de todos los archivos de objeto o biblioteca sean compatibles, ya sea actualizando los tipos que se usan o mediante el uso de una configuración **/Zc:wchar_t** coherente cuando compile.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de la biblioteca de terceros y de Vcpkg

Si ve este error cuando intenta configurar una biblioteca de terceros como parte de la compilación, considere el uso de [Vcpkg](../../vcpkg.md), el Administrador de paquetes de Visual C++, para instalar y compile la biblioteca. Vcpkg admite un enorme y creciente [lista de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports)y establece todas las propiedades de configuración y las dependencias necesarias para compilaciones correctas como parte del proyecto. Para obtener más información, consulte relacionado [Blog de Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) registrar.

## <a name="diagnosis-tools"></a>Herramientas de diagnóstico

Saber por qué el enlazador no puede encontrar una definición de símbolo en concreto puede ser difícil. A menudo el problema es que no se ha incluido el código que contiene la definición de la compilación o han creado diferentes opciones de compilación nombres representativos para símbolos externos. Hay varias herramientas y opciones que pueden ayudarle a diagnosticar un error LNK2019.

- La opción del enlazador [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) puede ayudarle a determinar los archivos a los que el enlazador hace referencia. Esto puede ayudarle a comprobar si el archivo que contiene la definición del símbolo está incluido en la compilación.

- El [/EXPORTA](../../build/reference/dash-exports.md) y [/símbolos](../../build/reference/symbols.md) opciones de la **DUMPBIN** utilidad puede ayudarle a descubrir qué símbolos están definidos en los archivos .dll y biblioteca u objeto. Compruebe que los nombres representativos exportados coinciden con los nombres representativos que busca en enlazador.

- El **UNDNAME** utilidad puede mostrarle el símbolo externo no representativo equivalente para un nombre representativo.

## <a name="examples"></a>Ejemplos

Aquí hay varios ejemplos de código que causa un error LNK2019 junto con información acerca de cómo corregirlo.

### <a name="a-symbol-is-declared-but-not-defined"></a>Se declaró un símbolo pero no se definió

En este ejemplo, una variable externa se declara, pero no definida:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Este es otro ejemplo donde se declaran una variable y función como `extern` , pero se proporciona ninguna definición:

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

A menos que `i` y `g` se definen en uno de los archivos incluidos en la compilación, el enlazador genera LNK2019. Puede corregir los errores mediante la inclusión del archivo de código fuente que contiene las definiciones como parte de la compilación. Como alternativa, puede pasar archivos .obj o .lib que contienen las definiciones para el vinculador.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>Se declara un miembro de datos estáticos pero no se define

LNK2019 también puede producirse cuando se declara un miembro de datos estático pero no se define. La muestra siguiente genera LNK2019 y muestra cómo corregirlo.

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-do-not-match-definition"></a>Los parámetros de declaración no coinciden con la definición

El código que invoca las funciones de plantilla debe tener declaraciones de función de plantilla coincidentes. Las declaraciones deben incluir los mismos parámetros de plantilla que la definición. La muestra siguiente genera LNK2019 en un operador definido por el usuario y muestra cómo corregirlo.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration does not match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-wchart-type-definitions"></a>Definiciones de tipo wchar_t incoherentes

Este ejemplo crea un archivo DLL que tiene una exportación que usa `WCHAR`, que se resuelve en `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

El ejemplo siguiente utiliza el archivo DLL en el ejemplo anterior y genera LNK2019 porque los tipos unsigned short * y WCHAR\* no son iguales.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Para corregir este error, cambie `unsigned short` a `wchar_t` o `WCHAR`, o compile LNK2019g.cpp con **/Zc:wchar_t-**.

## <a name="additional-resources"></a>Recursos adicionales

Para obtener más información sobre las posibles causas y soluciones para el error LNK2001, consulte la pregunta desbordamiento de pila [¿qué es un error de símbolo externo sin definir referencia/unresolved y cómo lo corrijo?](http://stackoverflow.com/q/12573816/2002113).

