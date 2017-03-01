---
title: Las herramientas del vinculador LNK2019 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2019
dev_langs:
- C++
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.assetid: 4392be92-195c-4eb2-bd4d-49cfac3ca291
caps.latest.revision: 39
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 86b43f2688b6e1dbfb39dfec681ca9adafd2c093
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2019"></a>Error de las herramientas del vinculador LNK2019
símbolo externo sin resolver "symbol” al que se hace referencia en la función "function"  
  
 El enlazador no pudo encontrar una definición para el símbolo externo "`symbol`" que se usa en la función"`function`".  
  
 Existen diversos problemas que pueden producir este error. Este tema le ayudará a identificar la causa y encontrar una solución.  
  
 Un *símbolo* es el nombre que el compilador utiliza para una función o variable global. Un *símbolo externo* es el nombre utilizado para hacer referencia a un símbolo que se define en un archivo de origen u objeto diferente. El vinculador debe *resolver*, o busque la definición para el símbolo externo para cada función o variable global utilizado por cada archivo compilado cuando se vincula a una aplicación o DLL. Si el enlazador no puede encontrar una definición coincidente para un símbolo externo en cualquiera de los archivos vinculados, genera LNK2019.  
  
 Este error puede producirse si el archivo de biblioteca u objeto que tiene la definición de un símbolo no se incluye en la compilación. También puede producirse si el vinculador busca el nombre del símbolo no coincide con el nombre del símbolo en el archivo de biblioteca u objeto que lo define. Esto puede ocurrir si el nombre del código de llamada está mal escrito, utiliza mayúsculas, utiliza una convención de llamada diferente o especifica parámetros diferentes.  
  
 El código que usa vinculación C++ usa [decoración de nombres](../../error-messages/tool-errors/name-decoration.md), también conocida como *alteración de nombres*, para codificar información adicional sobre el tipo y la convención de llamada en el nombre del símbolo de una variable o de la función. El *nombre representativo* es el nombre que el enlazador busca para resolver los símbolos externos. Dado que la información de tipo se convierte en parte del nombre representativo del símbolo, LNK2019 puede producir si la declaración del símbolo externo que se utiliza no coincide con la declaración del símbolo donde se define. Para ayudarle a encontrar la causa del error, el mensaje de error muestra tanto el "nombre descriptivo" el nombre usado en el código fuente y el nombre representativo (entre paréntesis) para el símbolo externo sin resolver. No es necesario saber cómo traducir el nombre representativo para poder comparar con otros nombres representativos.  
  
 **Problemas comunes**  
  
 Estos son algunos de los problemas comunes que causan LNK2019:  
  
-   **El archivo objeto o biblioteca que contiene la definición del símbolo no está vinculado.** En Visual Studio, compruebe que el archivo de origen que contiene la definición se creado y vinculado como parte de su proyecto. En la línea de comandos, compruebe que se compila el archivo de origen que contiene la definición y que el archivo objeto resultante se incluye en la lista de archivos que se va a vincular.  
  
-   **La declaración del símbolo no se ha escrito el mismo que la definición del símbolo.** Compruebe la ortografía y mayúsculas y minúsculas se utiliza en la declaración y la definición, y donde se usa el símbolo o se llama.  
  
-   **Se utiliza una función pero el tipo o el número de parámetros no coinciden con la definición de función.** . La declaración de función debe coincidir con su definición. Compruebe que la llamada de función coincide con la declaración y que la declaración coincide con la definición. El código que invoca las funciones de plantilla también debe tener declaraciones de función de plantilla coincidentes que incluyan los mismos parámetros de plantilla que la definición. Para obtener un ejemplo de un error de coincidencia de declaración de plantilla, vea ejemplo LNK2019e.cpp en la sección ejemplos.  
  
-   **Una función o una variable se declara, pero no definido.** Normalmente, esto significa una declaración existe en un archivo de encabezado, pero no se implementa ninguna definición coincidente. En las funciones miembro o miembros de datos estáticos, la implementación debe incluir el selector de ámbito de clase. Para obtener un ejemplo, vea [falta el cuerpo de función o Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md).  
  
-   **La convención de llamada es diferente entre la declaración de función y la definición de función.** Convenciones de llamada ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md), o [__vectorcall](../../cpp/vectorcall.md)) se codifican como parte del nombre representativo. Compruebe que la convención de llamada sea la misma.  
  
-   **Un símbolo está definido en un archivo de C, pero declarado sin usar extern "C" en un archivo de C++.** Símbolos definidos en un archivo que se compila como C tienen nombres representativos diferentes a los símbolos declarados en un archivo de C++ a menos que utilice un [extern "C"](../../cpp/using-extern-to-specify-linkage.md) modificador. Compruebe que la declaración coincide con la vinculación de compilación para cada símbolo.  
  
     Del mismo modo, si define un símbolo en un archivo C++ que se usará en un programa C, use `extern "C"` en la definición.  
  
-   **Un símbolo está definido como estático y, a continuación, se le hizo referencia fuera del archivo.** En C++, a diferencia de C, [constantes globales](../../error-messages/tool-errors/global-constants-in-cpp.md) tienen `static` vinculación. Para solucionar esta limitación, puede incluir las inicializaciones `const` en un encabezado de archivo e incluir dicho encabezado en los archivos .cpp. También puede hacer que la variable no sea constante y usar una referencia constante para obtener acceso.  
  
-   **No se define un miembro estático de una clase.** . Un miembro de clase estática debe tener una definición única. En caso contrario, infringe la regla de definición. Un miembro de clase estática que no se pueda definir mediante inserción deberá definirse en un archivo de origen usando su nombre completo. Si no se define en absoluto, el enlazador genera LNK2019.  
  
-   **Una dependencia de compilación solo se define como una dependencia de proyecto en la solución.** En versiones anteriores de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)], este nivel de dependencia era suficiente. Sin embargo, a partir de Visual Studio 2010, [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] requiere un [referencia de proyecto a proyecto](/visualstudio/ide/managing-references-in-a-project). Si el proyecto no tiene una referencia de proyecto a proyecto, puede que reciba este error del enlazador. Agregue una referencia de proyecto a proyecto para corregir este problema.  
  
-   **Cree una aplicación de consola mediante la configuración para una aplicación Windows**. Si el mensaje de error es similar a **unresolved external symbol WinMain referenced in function**`function_name`, vincule con **/SUBSYSTEM:CONSOLE** en lugar de **/SUBSYSTEM:WINDOWS**. Para obtener más información acerca de esta configuración y para obtener instrucciones sobre cómo establecer esta propiedad en Visual Studio, consulte [/SUBSYSTEM (Especificar subsistema)](../../build/reference/subsystem-specify-subsystem.md).  
  
-   **Usar opciones de compilador diferentes para la inclusión de funciones en archivos de código fuente diferente.** . El uso de funciones insertadas definidas en los archivos .cpp y la mezcla de opciones de compilador de inserción de funciones en archivos de origen diferentes puede causar LNK2019. Para obtener más información, consulte [problemas en la inclusión función](../../error-messages/tool-errors/function-inlining-problems.md).  
  
-   **Utilice variables automáticas fuera de su ámbito.** . Las variables automáticas (de ámbito de función) solo pueden usarse dentro del ámbito de esa función. Estas variables no se pueden declarar `extern` y usar en otros archivos de origen. Para obtener un ejemplo, vea [las de Variables automáticas (ámbito de función)](../../error-messages/tool-errors/automatic-function-scope-variables.md).  
  
-   **Llamar a funciones intrínsecas o pasa tipos de argumentos a funciones intrínsecas que no son compatibles con la arquitectura de destino.** Por ejemplo, si usa una función intrínseca AVX2 pero no se especifica la [/ARCH:AVX2](../../build/reference/arch-x86.md) opción del compilador, el compilador supone que la función intrínseca es una función externa. En lugar de generar una instrucción insertada, el compilador genera una llamada a un símbolo externo con el mismo nombre que la función intrínseca. Cuando el enlazador intenta buscar la definición de esta función ausente, genera LNK2019. Compruebe que solo usa funciones intrínsecas y tipos compatibles con la arquitectura de destino.  
  
-   **Mezcle código que usa wchar_t nativo con código que no.** . El trabajo de conformidad de lenguaje C++ que se realizó en Visual C++ 2005 convirtió `wchar_t` en un tipo nativo de forma predeterminada. Debe utilizar el [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) opción del compilador para generar código compatible con archivos de biblioteca y objeto compilados con versiones anteriores de Visual C++. Si no se compilaron todos los archivos con la misma configuración **/Zc:wchar_t** , puede que los tipos de referencia no se resuelvan en tipos compatibles. Compruebe que los tipos `wchar_t` de todos los archivos de objeto o biblioteca sean compatibles, ya sea actualizando los tipos que se usan o mediante el uso de una configuración **/Zc:wchar_t** coherente cuando compile.  
  
 Para obtener más información sobre las posibles causas y soluciones para LNK2019, consulte la pregunta Desbordamiento de la pila en [What is an undefined reference/unresolved external symbol error and how do I fix it? (¿Qué es un símbolo externo sin resolver o una referencia no definida y cómo se resuelven?)](http://stackoverflow.com/q/12573816/2002113).  
  
 **Herramientas de diagnóstico**  
  
 Saber por qué el enlazador no puede encontrar una definición de símbolo en concreto puede ser difícil. A menudo, el problema es que no incluyó el código en la compilación o bien que las opciones de compilación crearon nombres representativos para símbolos externos. Hay varias herramientas y opciones que pueden ayudarle a diagnosticar un error LNK2019.  
  
-   El [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) opción del vinculador puede ayudarle a determinar los archivos que el enlazador hace referencia. Esto puede ayudarle a comprobar si el archivo que contiene la definición del símbolo está incluido en la compilación.  
  
-   El [/EXPORTS](../../build/reference/dash-exports.md) y [/símbolos](../../build/reference/symbols.md) opciones de la utilidad DUMPBIN pueden ayudarle a descubrir qué símbolos están definidos en los archivos .dll y el objeto o biblioteca. Compruebe que los nombres representativos exportados coinciden con los nombres representativos que busca en enlazador.  
  
-   La utilidad UNDNAME puede mostrarle el símbolo externo no representativo equivalente para un nombre representativo.  
  
 **Ejemplos**  
  
 Aquí hay varios ejemplos de código que causa un error LNK2019 junto con información acerca de cómo corregirlo.  
  
 **Un símbolo está declarado pero no definido**  
  
 La muestra siguiente genera LNK2019 porque se declaró un símbolo externo pero no se definió:  
  
```cpp  
// LNK2019.cpp  
// Compile by using: cl /EHsc LNK2019.cpp  
// LNK2019 expected  
extern char B[100];   // B is not available to the linker  
int main() {  
   B[0] = ' ';   // LNK2019  
}  
```  
  
 A continuación se muestra otro ejemplo:  
  
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
  
 Si `i` y `g` no están definidas en uno de los archivos de la compilación, el enlazador genera LNK2019. Puede corregir los errores mediante la inclusión del archivo de código fuente que contiene las definiciones como parte de la compilación. Como alternativa, puede pasar a los archivos .obj o .lib del enlazador que contienen las definiciones.  
  
 **Un miembro de datos estático se declara, pero no definido**  
  
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
  
 **Parámetros de declaración no coinciden con la definición**  
  
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
  
 **Definiciones de tipo wchar_t incoherentes**  
  
 La muestra siguiente crea una DLL que tiene una exportación que usa `WCHAR`, que resuelve en `wchar_t`.  
  
```cpp  
// LNK2019g.cpp  
// compile with: cl /EHsc /LD LNK2019g.cpp  
#include "windows.h"  
// WCHAR resolves to wchar_t  
__declspec(dllexport) void func(WCHAR*) {}  
```  
  
 En el ejemplo siguiente utiliza el archivo DLL en el ejemplo anterior y genera LNK2019 porque los tipos unsigned short * y WCHAR\* no son iguales.  
  
```cpp  
// LNK2019h.cpp  
// compile by using: cl /EHsc LNK2019h LNK2019g.lib  
// LNK2019 expected  
__declspec(dllimport) void func(unsigned short*);  
  
int main() {  
   func(0);  
}  
```  
  
 Para resolver este error, cambie `unsigned short` a `wchar_t` o `WCHAR`, o compile LNK2019g.cpp con **/Zc:wchar_t-**.
