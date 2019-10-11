---
title: Error de las herramientas del vinculador LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: 3c4e5578c7b0f496feb4d40933af624f462a31d2
ms.sourcegitcommit: 680a155cc44a38f88bb2b1c5a1ef6dcb7141c011
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252627"
---
# <a name="linker-tools-error-lnk2019"></a>Error de las herramientas del vinculador LNK2019

símbolo externo sin resolver '*Symbol*' al que se hace referencia en la función '*function*'

El código compilado de la *función* hace referencia o llama a *Symbol*, pero ese símbolo no está definido en ninguna de las bibliotecas o archivos de objeto especificados para el vinculador.

Este mensaje de error va seguido de un error irrecuperable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Debe corregir todos los errores LNK2001 y LNK2019 para corregir el error LNK1120.

## <a name="possible-causes"></a>Causas posibles

Hay muchas maneras de obtener este error, pero todos ellos implican una referencia a una función o variable que el vinculador no puede *resolver*o buscar una definición para. El compilador puede identificar si no se ha *declarado*un símbolo, pero no cuando no está *definido*, porque la definición puede estar en un archivo o biblioteca de origen diferente. Si se hace referencia a un símbolo pero nunca se define, el vinculador genera un error de símbolo externo sin resolver.

Estos son algunos de los problemas comunes que causan LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>El archivo objeto o biblioteca que contiene la definición del símbolo no está vinculado

En Visual Studio, compruebe que el archivo de código fuente que contiene la definición se ha compilado y vinculado como parte del proyecto. En la línea de comandos, compruebe que el archivo de código fuente que contiene la definición está compilado y que el archivo objeto resultante se incluye en la lista de archivos que se van a vincular.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>La declaración del símbolo no se escribe de la misma forma que la definición del símbolo

Compruebe que la ortografía y el uso de mayúsculas y minúsculas se han corregido correctamente en la declaración y en la definición, y en cualquier lugar donde se use o se llame al símbolo.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Se usa una función pero el tipo o el número de parámetros no coinciden con la definición de función

. La declaración de función debe coincidir con su definición. Compruebe que la llamada de función coincide con la declaración y que la declaración coincide con la definición. El código que invoca las funciones de plantilla también debe tener declaraciones de función de plantilla coincidentes que incluyan los mismos parámetros de plantilla que la definición. Para obtener un ejemplo de una incoherencia en la declaración de una plantilla, vea ejemplo LNK2019e. cpp en la sección ejemplos.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Se declara una función o una variable, pero no se define

Normalmente, esto significa que una declaración existe en un archivo de encabezado, pero no se implementa ninguna definición coincidente. En las funciones miembro o miembros de datos estáticos, la implementación debe incluir el selector de ámbito de clase. Para obtener un ejemplo, consulta [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>La Convención de llamada es diferente entre la declaración de función y la definición de función

. Las convenciones de llamada ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)o [__vectorcall](../../cpp/vectorcall.md)) se codifican como parte del nombre representativo. Compruebe que la convención de llamada sea la misma.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Un símbolo se define en un archivo C, pero se declara sin usar extern "C" en C++ un archivo.

. Los símbolos definidos en un archivo que se compila como C tienen nombres representativos diferentes a los símbolos declarados en un archivo de C++, a menos que use un modificador ["C" externo](../../cpp/using-extern-to-specify-linkage.md) . Compruebe que la declaración coincide con la vinculación de compilación para cada símbolo. Del mismo modo, si define un símbolo en un archivo C++ que se usará en un programa C, use `extern "C"` en la definición.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Un símbolo se define como estático y, posteriormente, se hace referencia a él fuera del archivo

. En C++, a diferencia de C, las [constantes globales](../../error-messages/tool-errors/global-constants-in-cpp.md) tienen vinculación `static` . Para solucionar esta limitación, puede incluir las inicializaciones `const` en un encabezado de archivo e incluir dicho encabezado en los archivos .cpp. También puede hacer que la variable no sea constante y usar una referencia constante para obtener acceso.

### <a name="a-static-member-of-a-class-is-not-defined"></a>No se ha definido un miembro estático de una clase

. Un miembro de clase estática debe tener una definición única. En caso contrario, infringe la regla de definición. Un miembro de clase estática que no se pueda definir mediante inserción deberá definirse en un archivo de origen usando su nombre completo. Si no se define en absoluto, el enlazador genera LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Una dependencia de compilación solo se define como una dependencia de proyecto en la solución

En versiones anteriores de Visual Studio, este nivel de dependencia era suficiente. Sin embargo, a partir de Visual Studio 2010, Visual Studio requiere una [referencia de proyecto a proyecto](/visualstudio/ide/managing-references-in-a-project). Si el proyecto no tiene una referencia de proyecto a proyecto, puede que reciba este error del enlazador. Agregue una referencia de proyecto a proyecto para corregir este problema.

### <a name="an-entry-point-is-not-defined"></a>No se ha definido un punto de entrada

El código de aplicación debe definir un punto de entrada adecuado: `main` o `wmain` para las aplicaciones de consola, @no__t 2 o `wWinMain` para las aplicaciones de Windows. Para obtener más información, vea [main: El programa startup @ no__t-0 o [WinMain función](/windows/win32/api/winbase/nf-winbase-winmain). Para usar un punto de entrada personalizado, especifique la opción del enlazador [/entry (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md) . 

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Compilar una aplicación de consola mediante la configuración de una aplicación para Windows

Si el mensaje de error es similar al **símbolo externo sin resolver al que se hace referencia en la función** *function_name*, VINCULE mediante **/Subsystem: Console** en lugar de a **/Subsystem: Windows**. Para obtener más información acerca de esta configuración y para obtener instrucciones sobre cómo establecer esta propiedad en Visual Studio, consulte [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Intenta vincular bibliotecas de 64 bits a código de 32 bits o a bibliotecas de 32 bits a código de 64 bits.

Las bibliotecas y los archivos de objeto vinculados al código se deben compilar para la misma arquitectura que el código. Compruebe que las bibliotecas a las que hace referencia el proyecto se compilan para la misma arquitectura que el proyecto. Asegúrese de que la opción de ruta de acceso de los directorios de la biblioteca de [/LIBPATH](../../build/reference/libpath-additional-libpath.md) o **adicional** utilizada por el enlazador apunta a las bibliotecas compiladas para la arquitectura correcta.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Puede usar diferentes opciones del compilador para la inserción de funciones en archivos de código fuente diferentes

. El uso de funciones insertadas definidas en los archivos .cpp y la mezcla de opciones de compilador de inserción de funciones en archivos de origen diferentes puede causar LNK2019. Para obtener más información, consulta [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Se usan variables automáticas fuera de su ámbito

. Las variables automáticas (de ámbito de función) solo pueden usarse dentro del ámbito de esa función. Estas variables no se pueden declarar `extern` y usar en otros archivos de origen. Para obtener un ejemplo, consulta [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Se llama a las funciones intrínsecas o se pasan tipos de argumentos a funciones intrínsecas que no se admiten en la arquitectura de destino.

. Por ejemplo, si usa una función intrínseca AVX2 pero no especifica la opción del compilador [/ARCH:AVX2](../../build/reference/arch-x86.md) , el compilador supone que la función intrínseca es una función externa. En lugar de generar una instrucción insertada, el compilador genera una llamada a un símbolo externo con el mismo nombre que la función intrínseca. Cuando el enlazador intenta buscar la definición de esta función ausente, genera LNK2019. Compruebe que solo usa funciones intrínsecas y tipos compatibles con la arquitectura de destino.

### <a name="you-mix-code-that-uses-native-wchar_t-with-code-that-doesnt"></a>Se mezcla código que usa WCHAR @ no__t-0T nativo con código que no

C++el trabajo de conformidad de lenguaje que se realizó en Visual Studio 2005 realizó `wchar_t` de forma predeterminada. Debe usar la opción del compilador [/Zc: wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para generar código compatible con los archivos de biblioteca y objeto compilados con versiones anteriores de Visual Studio. Si no se han compilado todos los archivos con la misma configuración **/Zc: WCHAR @ no__t-1T** , es posible que las referencias de tipo no se resuelvan en tipos compatibles. Compruebe que los tipos `wchar_t` de todos los archivos de objeto o biblioteca sean compatibles, ya sea actualizando los tipos que se usan o mediante el uso de una configuración **/Zc:wchar_t** coherente cuando compile.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de la biblioteca de terceros y Vcpkg

Si ve este error al intentar configurar una biblioteca de terceros como parte de la compilación, considere la posibilidad de usar [Vcpkg](../../vcpkg.md), el administrador de paquetes C++ visuales, para instalar y compilar la biblioteca. Vcpkg admite una lista grande y creciente [de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports), y establece todas las propiedades de configuración y las dependencias necesarias para compilaciones correctas como parte del proyecto. Para obtener más información, consulte la entrada de [blog visual C++ ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) relacionada.

## <a name="diagnosis-tools"></a>Herramientas de diagnóstico

Saber por qué el enlazador no puede encontrar una definición de símbolo en concreto puede ser difícil. A menudo, el problema es que no incluyó el código que contiene la definición en la compilación, o bien que las opciones de compilación crearon nombres representativos para símbolos externos. Hay varias herramientas y opciones que pueden ayudarle a diagnosticar un error LNK2019.

- La opción del enlazador [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) puede ayudarle a determinar los archivos a los que el enlazador hace referencia. Esto puede ayudarle a comprobar si el archivo que contiene la definición del símbolo está incluido en la compilación.

- Las opciones [/Exports](../../build/reference/dash-exports.md) y [/Symbols](../../build/reference/symbols.md) de la utilidad **dumpbin** pueden ayudarle a detectar qué símbolos se definen en los archivos. dll y de objeto o biblioteca. Compruebe que los nombres representativos exportados coinciden con los nombres representativos que busca en enlazador.

- La utilidad **UNDNAME** puede mostrarle el símbolo externo no representativo equivalente para un nombre representativo.

## <a name="examples"></a>Ejemplos

Aquí hay varios ejemplos de código que causa un error LNK2019 junto con información acerca de cómo corregirlo.

### <a name="a-symbol-is-declared-but-not-defined"></a>Se declaró un símbolo pero no se definió

En este ejemplo, se declara una variable externa, pero no se define:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
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

### <a name="inconsistent-wchar_t-type-definitions"></a>Definiciones de tipo wchar_t incoherentes

En este ejemplo se crea un archivo DLL que tiene una exportación que usa `WCHAR`, que se resuelve en `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

En el ejemplo siguiente se usa el archivo DLL en el ejemplo anterior y se genera LNK2019 porque los tipos Short * y WCHAR @ no__t-0 no son iguales.

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

