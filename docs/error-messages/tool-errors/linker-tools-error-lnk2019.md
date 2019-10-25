---
title: Error de las herramientas del vinculador LNK2019
ms.date: 10/22/2019
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: 948a27e2d80c81afcf41efadd83e56709c98a304
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811111"
---
# <a name="linker-tools-error-lnk2019"></a>Error de las herramientas del vinculador LNK2019

> símbolo externo sin resolver '*Symbol*' al que se hace referencia en la función '*function*'

El código compilado de la *función* hace referencia o llama a *Symbol*, pero el enlazador no puede encontrar la definición de símbolos en ninguna de las bibliotecas o archivos objeto que se van a vincular.

Este mensaje de error va seguido de un error irrecuperable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Para corregir el error LNK1120, primero debe corregir todos los errores LNK2001 y LNK2019.

## <a name="possible-causes"></a>Causas posibles

Hay muchas maneras de obtener este error. Todos ellos incluyen una referencia a una función o variable que el enlazador no pudo *resolver*, o buscar una definición para. El compilador puede identificar si no se ha *declarado*un símbolo, pero no puede saber si el símbolo no está *definido*. Esto se debe a que la definición puede estar en un archivo o biblioteca de origen diferente. Si se hace referencia a un símbolo pero nunca se define, el vinculador genera un error de símbolo externo sin resolver.

Estos son algunos de los problemas comunes que causan LNK2019:

### <a name="the-source-file-that-contains-the-definition-of-the-symbol-isnt-compiled"></a>El archivo de código fuente que contiene la definición del símbolo no está compilado

En Visual Studio, asegúrese de que el archivo de código fuente que define el símbolo se compila como parte del proyecto. Compruebe el directorio de salida de compilación intermedia para buscar un archivo. obj coincidente. Si no se compila el archivo de código fuente, haga clic con el botón derecho en el archivo en Explorador de soluciones y elija **propiedades** para comprobar las propiedades del archivo. Las **propiedades de configuración** > página **General** deben mostrar un **tipo de elemento** de **C/C++ Compiler**. En la línea de comandos, asegúrese de que el archivo de código fuente que contiene la definición está compilado.

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-isnt-linked"></a>El archivo objeto o biblioteca que contiene la definición del símbolo no está vinculado

En Visual Studio, asegúrese de que el archivo objeto o la biblioteca que contiene la definición de símbolo se vinculan como parte del proyecto. En la línea de comandos, asegúrese de que la lista de archivos que se van a vincular incluye el archivo objeto o la biblioteca.

### <a name="the-declaration-of-the-symbol-isnt-spelled-the-same-as-the-definition-of-the-symbol"></a>La declaración del símbolo no se escribe de la misma forma que la definición del símbolo

Compruebe que usa las mayúsculas y minúsculas correctas en la declaración y en la definición, y donde se usa o se llama al símbolo.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-dont-match-the-function-definition"></a>Se utiliza una función pero el tipo o el número de parámetros no coinciden con la definición de función

. La declaración de función debe coincidir con su definición. Asegúrese de que la llamada de función coincide con la declaración y que la declaración coincide con la definición. El código que invoca las funciones de plantilla también debe tener declaraciones de función de plantilla coincidentes que incluyan los mismos parámetros de plantilla que la definición. Para obtener un ejemplo de una incoherencia en la declaración de una plantilla, vea ejemplo LNK2019e. cpp en la sección ejemplos.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Se declara una función o una variable, pero no se define

LNK2019 puede producirse cuando una declaración existe en un archivo de encabezado, pero no se implementa ninguna definición coincidente. En las funciones miembro o miembros de datos estáticos, la implementación debe incluir el selector de ámbito de clase. Para obtener un ejemplo, consulta [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>La Convención de llamada es diferente entre la declaración de función y la definición de función

. Las convenciones de llamada ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)o [__vectorcall](../../cpp/vectorcall.md)) se codifican como parte del nombre representativo. Asegúrese de que la Convención de llamada es la misma.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Un símbolo se define en un archivo C, pero se declara sin usar extern "C" en C++ un archivo.

. Los símbolos definidos en un archivo que se compila como C tienen nombres representativos diferentes a los símbolos declarados en un archivo de C++, a menos que use un modificador ["C" externo](../../cpp/using-extern-to-specify-linkage.md) . Asegúrese de que la declaración coincide con la vinculación de compilación para cada símbolo. Del mismo modo, si define un símbolo en un archivo C++ que se usará en un programa C, use `extern "C"` en la definición.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Un símbolo se define como estático y, posteriormente, se hace referencia a él fuera del archivo

. En C++, a diferencia de C, las [constantes globales](../../error-messages/tool-errors/global-constants-in-cpp.md) tienen vinculación `static` . Para solucionar esta limitación, puede incluir las inicializaciones `const` en un encabezado de archivo e incluir dicho encabezado en los archivos .cpp. También puede hacer que la variable no sea constante y usar una referencia constante para obtener acceso.

### <a name="a-static-member-of-a-class-isnt-defined"></a>No se ha definido un miembro estático de una clase

. Un miembro de clase estática debe tener una definición única. En caso contrario, infringe la regla de definición. Un miembro de clase estática que no se pueda definir en línea debe definirse en un archivo de código fuente utilizando su nombre completo. Si no se define en absoluto, el enlazador genera LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Una dependencia de compilación solo se define como una dependencia de proyecto en la solución

En versiones anteriores de Visual Studio, este nivel de dependencia era suficiente. Sin embargo, a partir de Visual Studio 2010, Visual Studio requiere una [referencia de proyecto a proyecto](/visualstudio/ide/managing-references-in-a-project). Si el proyecto no tiene una referencia de proyecto a proyecto, es posible que reciba este error del enlazador. Agregue una referencia de proyecto a proyecto para corregir este problema.

### <a name="an-entry-point-isnt-defined"></a>No se ha definido un punto de entrada

El código de aplicación debe definir un punto de entrada adecuado: `main` o `wmain` para las aplicaciones de consola y `WinMain` o `wWinMain` para aplicaciones Windows. Para obtener más información, consulte [Main: Program startup](../../cpp/main-program-startup.md) o la [función WinMain](/windows/win32/api/winbase/nf-winbase-winmain). Para usar un punto de entrada personalizado, especifique la opción del enlazador [/entry (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md) .

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Compilar una aplicación de consola mediante la configuración de una aplicación para Windows

Si el mensaje de error es similar al **símbolo externo sin resolver al que se hace referencia en la función** *function_name*, VINCULE mediante **/Subsystem: Console** en lugar de a **/Subsystem: Windows**. Para obtener más información acerca de esta configuración y para obtener instrucciones sobre cómo establecer esta propiedad en Visual Studio, consulte [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Intenta vincular bibliotecas de 64 bits a código de 32 bits o a bibliotecas de 32 bits a código de 64 bits.

Las bibliotecas y los archivos de objeto vinculados al código se deben compilar para la misma arquitectura que el código. Asegúrese de que las bibliotecas a las que hace referencia el proyecto se compilan para la misma arquitectura que el proyecto. Asegúrese de que la propiedad [/LIBPATH](../../build/reference/libpath-additional-libpath.md) o **directorios de biblioteca adicionales** apunta a las bibliotecas compiladas para la arquitectura correcta.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Puede usar diferentes opciones del compilador para la inserción de funciones en archivos de código fuente diferentes

. El uso de funciones insertadas definidas en los archivos .cpp y la mezcla de opciones de compilador de inserción de funciones en archivos de origen diferentes puede causar LNK2019. Para obtener más información, consulta [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Se usan variables automáticas fuera de su ámbito

. Las variables automáticas (de ámbito de función) solo pueden usarse dentro del ámbito de esa función. Estas variables no se pueden declarar `extern` y usar en otros archivos de origen. Para obtener un ejemplo, consulta [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>Puede llamar a funciones intrínsecas o pasar tipos de argumentos a funciones intrínsecas que no se admiten en la arquitectura de destino.

Por ejemplo, si usa un intrínseco AVX2, pero no especifica la opción del compilador [/Arch: AVX2](../../build/reference/arch-x86.md) , el compilador supone que el intrínseco es una función externa. En lugar de generar una instrucción insertada, el compilador genera una llamada a un símbolo externo con el mismo nombre que la función intrínseca. Cuando el enlazador intenta buscar la definición de esta función ausente, genera LNK2019. Asegúrese de usar solo los intrínsecos y los tipos compatibles con la arquitectura de destino.

### <a name="you-mix-code-that-uses-native-wchar_t-with-code-that-doesnt"></a>Se mezcla código que usa wchar_t nativo con código que no

C++el trabajo de conformidad de lenguaje que se realizó en Visual Studio 2005 hacía que **wchar_t** fuera un tipo nativo de forma predeterminada. Si no se compilaron todos los archivos con la misma configuración **/Zc:wchar_t** , puede que los tipos de referencia no se resuelvan en tipos compatibles. Asegúrese de que los tipos **wchar_t** de todos los archivos de biblioteca y objeto son compatibles. Actualice desde una definición de tipo **wchar_t** o use la configuración de **/Zc: wchar_t** coherente al compilar.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de la biblioteca de terceros y Vcpkg

Si ve este error al intentar configurar una biblioteca de terceros como parte de la compilación, considere la posibilidad de usar [Vcpkg](../../vcpkg.md), el administrador de paquetes C++ visuales, para instalar y compilar la biblioteca. Vcpkg admite una lista grande y creciente [de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports). Establece todas las propiedades de configuración y las dependencias necesarias para las compilaciones correctas como parte del proyecto. Para obtener más información, consulte la entrada de [blog visual C++ ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) relacionada.

## <a name="diagnosis-tools"></a>Herramientas de diagnóstico

A veces es difícil saber por qué el enlazador no puede encontrar una definición de símbolo determinada. A menudo, el problema es que no incluyó el código que contiene la definición en la compilación. O bien, las opciones de compilación han creado nombres representativos para símbolos externos. Hay varias herramientas y opciones que pueden ayudarle a diagnosticar errores LNK2019.

- La opción del enlazador [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) puede ayudarle a determinar los archivos a los que el enlazador hace referencia. Esta opción puede ayudarle a comprobar si el archivo que contiene la definición del símbolo está incluido en la compilación.

- Las opciones [/Exports](../../build/reference/dash-exports.md) y [/Symbols](../../build/reference/symbols.md) de la utilidad **dumpbin** pueden ayudarle a detectar qué símbolos se definen en los archivos. dll y de objeto o biblioteca. Asegúrese de que los nombres representativos exportados coinciden con los nombres representativos que busca el enlazador.

- La utilidad **UNDNAME** puede mostrarle el símbolo externo no representativo equivalente para un nombre representativo.

## <a name="examples"></a>Ejemplos

Aquí hay varios ejemplos de código que causa un error LNK2019 junto con información acerca de cómo corregirlo.

### <a name="a-symbol-is-declared-but-not-defined"></a>Se declaró un símbolo pero no se definió

En este ejemplo, se declara una variable externa, pero no se define:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B isn't available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Este es otro ejemplo en el que una variable y una función se declaran como `extern` pero no se proporciona ninguna definición:

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

A menos que `i` y `g` se hayan definido en uno de los archivos incluidos en la compilación, el enlazador genera LNK2019. Puede corregir los errores mediante la inclusión del archivo de código fuente que contiene las definiciones como parte de la compilación. Como alternativa, puede pasar archivos. obj o. lib que contengan las definiciones al enlazador.

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

### <a name="declaration-parameters-dont-match-the-definition"></a>Los parámetros de declaración no coinciden con la definición

El código que invoca las funciones de plantilla debe tener declaraciones de función de plantilla coincidentes. Las declaraciones deben incluir los mismos parámetros de plantilla que la definición. La muestra siguiente genera LNK2019 en un operador definido por el usuario y muestra cómo corregirlo.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration doesn't match the definition below:
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

### <a name="inconsistent-wchar_t-type-definitions"></a>Definiciones de tipo wchar_t incoherentes

En este ejemplo se crea un archivo DLL que tiene una exportación que usa `WCHAR`, que se resuelve en `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

En el ejemplo siguiente se usa el archivo DLL en el ejemplo anterior y se genera el error LNK2019 porque los tipos Short * y WCHAR sin signo\* no son iguales.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Para corregir este error, cambie `unsigned short` a `wchar_t` o `WCHAR`, o bien compile LNK2019g. cpp mediante **/Zc: wchar_t-** .

## <a name="additional-resources"></a>Recursos adicionales

Para obtener más información sobre las posibles causas y soluciones de LNK2001, vea la Stack Overflow pregunta [¿Qué es un error de referencia no definida/símbolo externo sin resolver y cómo corregirlo?](https://stackoverflow.com/q/12573816/2002113).
