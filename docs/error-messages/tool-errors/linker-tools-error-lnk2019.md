---
title: "Error de las herramientas del vinculador LNK2019 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_check_commonlanguageruntime_version"
  - "LNK2019"
  - "nochkclr.obj"
ms.assetid: 4392be92-195c-4eb2-bd4d-49cfac3ca291
caps.latest.revision: 39
caps.handback.revision: 37
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo externo sin resolver "symbol” al que se hace referencia en la función "function"  
  
 El enlazador no pudo encontrar una definición para el símbolo externo "`symbol`" que se usa en la función"`function`". Existen diversos problemas que pueden producir este error. Este tema le ayudará a identificar la causa y encontrar una solución.  
  
 Un *símbolo externo* es el nombre declarado que usa en el código fuente para hacer referencia a algo que está definido en otro archivo de objeto o biblioteca como, por ejemplo, una función externa o una variable global. El enlazador es el responsable de resolver todas las referencias a símbolos externos en cada archivo de objeto si están vinculadas a una aplicación o una DLL. Si el enlazador no puede encontrar una definición coincidente para un símbolo externo en cualquiera de los archivos vinculados, genera LNK2019. Este error puede producirse si el código fuente o el archivo de biblioteca que tiene la definición del símbolo no se incluye en la compilación. También puede producirse si el nombre que busca el enlazador no coincide con el nombre del símbolo en el archivo de objeto o biblioteca que lo define.  
  
 El código que usa vinculación C\+\+ usa [Decoración de nombres](../../error-messages/tool-errors/name-decoration.md), también conocida como *alteración de nombres*, para codificar información adicional sobre el tipo y la convención de llamada de un símbolo junto con su nombre. El *nombre representativo* es el nombre que el enlazador busca para resolver los símbolos externos. Si el tipo de declaración de la referencia al símbolo no coincide con el tipo de declaración de la definición del símbolo, puede que esto cause el error LNK2019, pues se convierte en parte del nombre representativo del símbolo. El mensaje de error le muestra el símbolo externo y su nombre representativo para ayudarle a encontrar la causa del error.  
  
 **Problemas comunes**  
  
 Estos son algunos de los problemas comunes que causan LNK2019:  
  
-   **La declaración del símbolo no se escribe como la definición del símbolo**. Compruebe que la ortografía sea correcta.  
  
-   **Se usa una función pero el tipo o número de parámetros no coinciden con su definición**. La declaración de función debe coincidir con su definición. El código que invoca las funciones de plantilla también debe tener declaraciones de función de plantilla coincidentes que incluyan los mismos parámetros de plantilla que la definición. Compruebe que la llamada de función coincide con la declaración y que la declaración coincide con la definición.  
  
-   **Se declara una función o una variable, pero no se define**. Normalmente, esto significa que hay una declaración en un archivo de encabezado, pero no se ha implementado ninguna definición. En las funciones miembro o miembros de datos estáticos, la implementación debe incluir el selector de ámbito de clase. Para obtener un ejemplo, consulta [Cuerpo de función o variable no encontrados](../../error-messages/tool-errors/missing-function-body-or-variable.md).  
  
-   **La convención de llamada es diferente entre la declaración de función y la definición de función**. Las convenciones de llamada \([\_\_cdecl](../../cpp/cdecl.md), [\_\_stdcall](../../cpp/stdcall.md), [\_\_fastcall](../../cpp/fastcall.md) o [\_\_vectorcall](../../cpp/vectorcall.md)\) se codifican como parte del nombre representativo. Compruebe que la convención de llamada sea la misma.  
  
-   **Un símbolo está definido en un archivo C, pero está declarado sin usar un "C" externo en un archivo C\+\+**. Los símbolos definidos en un archivo que se compila como C tienen nombres representativos diferentes a los símbolos declarados en un archivo de C\+\+, a menos que use un modificador ["C" externo](../../cpp/using-extern-to-specify-linkage.md). Compruebe que la declaración coincide con la vinculación de compilación para cada símbolo.  
  
     Del mismo modo, si define un símbolo en un archivo C\+\+ que se usará en un programa C, use `extern "C"` en la definición.  
  
-   **Se definió un símbolo como estático y, a continuación, se le hizo referencia fuera del archivo**. En C\+\+, a diferencia de C, las [constantes globales](../../error-messages/tool-errors/global-constants-in-cpp.md) tienen vinculación `static`. Para solucionar esta limitación, puede incluir las inicializaciones `const` en un encabezado de archivo e incluir dicho encabezado en los archivos .cpp. También puede hacer que la variable no sea constante y usar una referencia constante para obtener acceso.  
  
-   **No se define un miembro estático de una clase**. Un miembro de clase estática debe tener una definición única. En caso contrario, infringe la regla de definición. Un miembro de clase estática que no se pueda definir mediante inserción deberá definirse en un archivo de origen usando su nombre completo. Si no se define en absoluto, el enlazador genera LNK2019.  
  
-   **Una dependencia de compilación solo se define como una dependencia de proyecto en la solución**. En versiones anteriores de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)], este nivel de dependencia era suficiente. Sin embargo, a partir de Visual Studio 2010, [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] requiere una [referencia de proyecto a proyecto](../Topic/Managing%20references%20in%20a%20project.md). Si el proyecto no tiene una referencia de proyecto a proyecto, puede que reciba este error del enlazador. Agregue una referencia de proyecto a proyecto para corregir este problema.  
  
-   **Cree una aplicación de consola mediante la configuración para una aplicación Windows**. Si el mensaje de error es similar a**unresolved external symbol WinMain referenced in function** `function_name`, vincule con **\/SUBSYSTEM:CONSOLE** en lugar de **\/SUBSYSTEM:WINDOWS**. Para obtener más información acerca de esta configuración y para obtener instrucciones sobre cómo establecer esta propiedad en Visual Studio, consulte [\/SUBSYSTEM \(Especificar subsistema\)](../../build/reference/subsystem-specify-subsystem.md).  
  
-   **Use opciones de compilador diferentes para la inserción de funciones en archivos de origen diferentes**. El uso de funciones insertadas definidas en los archivos .cpp y la mezcla de opciones de compilador de inserción de funciones en archivos de origen diferentes puede causar LNK2019. Para obtener más información, consulta [Problemas en la inclusión de funciones en línea](../../error-messages/tool-errors/function-inlining-problems.md).  
  
-   **Use variables automáticas fuera de su ámbito**. Las variables automáticas \(de ámbito de función\) solo pueden usarse dentro del ámbito de esa función. Estas variables no se pueden declarar `extern` y usar en otros archivos de origen. Para obtener un ejemplo, consulta [Variables automáticas \(ámbito de función\)](../../error-messages/tool-errors/automatic-function-scope-variables.md).  
  
-   **Llame a funciones intrínsecas o pasa tipos de argumentos a funciones intrínsecas que no son compatibles con la arquitectura de destino**. Por ejemplo, si usa una función intrínseca AVX2 pero no especifica la opción del compilador [\/ARCH:AVX2](../../build/reference/arch-x86.md), el compilador supone que la función intrínseca es una función externa. En lugar de generar una instrucción insertada, el compilador genera una llamada a un símbolo externo con el mismo nombre que la función intrínseca. Cuando el enlazador intenta buscar la definición de esta función ausente, genera LNK2019. Compruebe que solo usa funciones intrínsecas y tipos compatibles con la arquitectura de destino.  
  
-   **Mezcle código que usa wchar\_t nativo con código que no lo usa**. El trabajo de conformidad de lenguaje C\+\+ que se realizó en Visual C\+\+ 2005 convirtió `wchar_t` en un tipo nativo de forma predeterminada. Debe usar la opción del compilador [\/Zc:wchar\_t\-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para generar código compatible con los archivos de objeto o biblioteca compilados con versiones anteriores de Visual C\+\+. Si no se compilaron todos los archivos con la misma configuración **\/Zc:wchar\_t**, puede que los tipos de referencia no se resuelvan en tipos compatibles. Compruebe que los tipos `wchar_t` de todos los archivos de objeto o biblioteca sean compatibles, ya sea actualizando los tipos que se usan o mediante el uso de una configuración **\/Zc:wchar\_t** coherente cuando compile.  
  
 Para obtener más información sobre las posibles causas y soluciones para LNK2019, consulte la pregunta Desbordamiento de la pila en [What is an undefined reference\/unresolved external symbol error and how do I fix it? \(¿Qué es un símbolo externo sin resolver o una referencia no definida y cómo se resuelven?\)](http://stackoverflow.com/q/12573816/2002113).  
  
 **Herramientas de diagnóstico**  
  
 Saber por qué el enlazador no puede encontrar una definición de símbolo en concreto puede ser difícil. A menudo, el problema es que no incluyó el código en la compilación o bien que las opciones de compilación crearon nombres representativos para símbolos externos. Hay varias herramientas y opciones que pueden ayudarle a diagnosticar un error LNK2019.  
  
-   La opción del enlazador [\/VERBOSE](../../build/reference/verbose-print-progress-messages.md) puede ayudarle a determinar los archivos a los que el enlazador hace referencia. Esto puede ayudarle a comprobar si el archivo que contiene la definición del símbolo está incluido en la compilación.  
  
-   Las opciones [\/EXPORTS](../../build/reference/dash-exports.md) y [\/SYMBOLS](../../build/reference/symbols.md) de la utilidad DUMPBIN pueden ayudarle a descubrir qué símbolos están definidos en los archivos .dll y en los archivos de objeto o biblioteca. Compruebe que los nombres representativos exportados coinciden con los nombres representativos que busca en enlazador.  
  
-   La utilidad UNDNAME puede mostrarle el símbolo externo no representativo equivalente para un nombre representativo.  
  
 **Ejemplos**  
  
 Aquí hay varios ejemplos de código que causa un error LNK2019 junto con información acerca de cómo corregirlo.  
  
 **Se declaró un símbolo pero no se definió**  
  
 La muestra siguiente genera LNK2019 porque se declaró un símbolo externo pero no se definió:  
  
```cpp  
// LNK2019.cpp // Compile by using: cl /EHsc LNK2019.cpp // LNK2019 expected extern char B[100];   // B is not available to the linker int main() { B[0] = ' ';   // LNK2019 }  
```  
  
 A continuación se muestra otro ejemplo:  
  
```cpp  
// LNK2019c.cpp // Compile by using: cl /EHsc LNK2019c.cpp // LNK2019 expected extern int i; extern void g(); void f() { i++; g(); } int main() {}  
```  
  
 Si `i` y `g` no están definidas en uno de los archivos de la compilación, el enlazador genera LNK2019. Puede corregir los errores mediante la inclusión del archivo de código fuente que contiene las definiciones como parte de la compilación. Como alternativa, puede pasar a los archivos .obj o .lib del enlazador que contienen las definiciones.  
  
 **Se declara un miembro de datos estáticos pero no se define**  
  
 LNK2019 también puede producirse cuando se declara un miembro de datos estático pero no se define. La muestra siguiente genera LNK2019 y muestra cómo corregirlo.  
  
```cpp  
// LNK2019b.cpp // Compile by using: cl /EHsc LNK2019b.cpp // LNK2019 expected struct C { static int s; }; // Uncomment the following line to fix the error. // int C::s; int main() { C c; C::s = 1; }  
```  
  
 **Los parámetros de declaración no coinciden con la definición**  
  
 El código que invoca las funciones de plantilla debe tener declaraciones de función de plantilla coincidentes. Las declaraciones deben incluir los mismos parámetros de plantilla que la definición. La muestra siguiente genera LNK2019 en un operador definido por el usuario y muestra cómo corregirlo.  
  
```cpp  
// LNK2019e.cpp // compile by using: cl /EHsc LNK2019e.cpp // LNK2019 expected #include <iostream> using namespace std; template<class T> class Test { // The operator<< declaration does not match the definition below: friend ostream& operator<<(ostream&, Test&); // To fix, replace the line above with the following: // template<typename T> friend ostream& operator<<(ostream&, Test<T>&); }; template<typename T> ostream& operator<<(ostream& os, Test<T>& tt) { return os; } int main() { Test<int> t; cout << "Test: " << t << endl;   // LNK2019 unresolved external }  
```  
  
 **Definiciones de tipo wchar\_t incoherentes**  
  
 La muestra siguiente crea una DLL que tiene una exportación que usa `WCHAR`, que resuelve en `wchar_t`.  
  
```cpp  
// LNK2019g.cpp // compile with: cl /EHsc /LD LNK2019g.cpp #include "windows.h" // WCHAR resolves to wchar_t __declspec(dllexport) void func(WCHAR*) {}  
```  
  
 La muestra siguiente usa la DLL de la muestra anterior y genera LNK2019 porque los tipos short \* y WCHAR \* sin asignar no son iguales.  
  
```cpp  
// LNK2019h.cpp // compile by using: cl /EHsc LNK2019h LNK2019g.lib // LNK2019 expected __declspec(dllimport) void func(unsigned short*); int main() { func(0); }  
```  
  
 Para resolver este error, cambie `unsigned short` a `wchar_t` o `WCHAR` o bien compile LNK2019g.cpp con **\/Zc:wchar\_t\-**.