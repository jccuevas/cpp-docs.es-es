---
title: Compilador (nivel 3) de la advertencia C4996 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4996
dev_langs:
- C++
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
caps.latest.revision: 34
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 9a0c25772fadec86a893b8c7c4af09072eb0476f
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-warning-level-3-c4996"></a>Compilador (nivel 3) de la advertencia C4996
El compilador encontró una declaración en desuso.  
  
Esta advertencia o error tiene varios significados posibles, dependiendo del contexto.  
  
Advertencia C4996 se produce cuando el compilador encuentra una función o variable que esté marcada como [en desuso](../../cpp/deprecated-cpp.md) mediante el uso de un `__declspec(deprecated)` modificador. También se emite esta advertencia cuando se intenta acceder a una función, miembro de clase o definición de tipo que tiene C ++ 14 `[[deprecated]]` atributo. Para obtener más información, consulte [atributos estándar de C++](../../cpp/attributes2.md). Se puede usar este atributo usted mismo en las bibliotecas para advertir a los clientes sobre definiciones de tipos, miembros o funciones en desuso.  
  
Varias funciones, funciones miembro, funciones de plantilla y variables globales de las bibliotecas de Visual Studio están marcadas como en desuso. Estas funciones pueden tener un nombre preferido distinto, no ser seguras o tener una variante más segura, o estar obsoletas. Muchos mensajes de error incluyen un reemplazo sugerido para la función en desuso o una variable global.  
  
Para corregir este problema, se recomienda suele que cambiar el código para usar las funciones de más seguras o actualizadas sugeridas y variables globales en su lugar. Si tiene que utilizar las funciones existentes o las variables por motivos de portabilidad, puede desactivar la advertencia.  
  
Puede desactivar las advertencias para una línea de código específica mediante el [advertencia](../../preprocessor/warning.md) pragma `#pragma warning(suppress : 4996)`. Que puede apagarlo dentro de un archivo mediante el uso de la directiva de advertencia pragma `#pragma warning(disable : 4996)`. Puede desactivarlo globalmente en las compilaciones de línea de comandos mediante el uso de la **/wd4996** opción de línea de comandos. Para desactivar la advertencia para un proyecto en el IDE de Visual Studio, abra el **páginas de propiedades** cuadro de diálogo, seleccione la **propiedades de configuración**, **C/C++**, **avanzadas** página y edite la **deshabilitar advertencias específicas** propiedad que se va a agregar `4996`.  También puede usar macros de preprocesador para desactivar determinadas clases específicas de las advertencias sobre desuso utilizadas en las bibliotecas. A continuación se describen estas macros.  
  
Estas son algunas de las fuentes de biblioteca de la advertencia C4996.  
  
## <a name="posix-function-names"></a>Nombres de función POSIX  
  
**El nombre POSIX de este elemento está en desuso. En su lugar, utilice el nombre de compatible con ISO C y C++:** *new_name*. **Consulte la Ayuda en línea para obtener más información.**  
  
Microsoft ha cambiado el nombre de algunas funciones POSIX en CRT para respetar C99 y C ++ 03 las reglas para nombres de funciones globales definidos por la implementación. Solo los nombres POSIX originales están en desuso, no las propias funciones. En la mayoría de casos, se agregó un carácter de subrayado inicial al nombre de función POSIX para crear un nombre conforme al estándar. El compilador emite una advertencia para el nombre de la función original y sugiere el nombre preferido.  
  
Para corregir este problema, se recomienda suele que cambiar el código para usar los nombres de función sugeridas en su lugar. Sin embargo, los nombres actualizados son específicos de Microsoft. Si necesita usar los nombres de función existente por motivos de portabilidad, puede desactivar estas advertencias. Las funciones POSIX siguen estando disponibles en la biblioteca en sus nombres originales.  
  
Para desactivar las advertencias sobre desuso para estas funciones, defina la macro de preprocesador **_CRT_NONSTDC_NO_WARNINGS**. Puede definirla en la línea de comandos si incluye la opción `/D_CRT_NONSTDC_NO_WARNINGS`. Para definir esta macro en Visual Studio, abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Expanda **Propiedades de configuración**, **C o C++**, **Preprocesador**. En **Definiciones de preprocesador**, agregue `_CRT_NONSTDC_NO_WARNINGS`. Seleccione **Aceptar** para guardar y, luego, vuelva a generar el proyecto. Para definir esta macro solamente en archivos de origen concretos, agregue la línea `#define _CRT_NONSTDC_NO_WARNINGS` antes de cualquier línea que incluya un archivo de encabezado.  
  
## <a name="unsafe-crt-library-functions"></a>Funciones de biblioteca de CRT no seguras  
  
 **Esta función o variable puede ser no seguro. Considere el uso de***safe_version* **en su lugar.   Para deshabilitar el desuso, utilice _CRT_SECURE_NO_WARNINGS.  Consulte la ayuda en línea para obtener información detallada.**  
  
 Microsoft desusado algunas funciones de biblioteca estándar de C++ y CRT y las variables globales en favor de versiones más seguras. En la mayoría de los casos, las funciones en desuso permiten desactivada acceso de lectura o escritura a los búferes, lo que puede provocar problemas de seguridad grave. El compilador emite una advertencia de desuso para estas funciones y sugiere la función preferida.  
  
 Para corregir este problema, se recomienda usar la función o variable *safe_version* en su lugar. Si ha comprobado que no es posible una sobrescritura de búfer o overread que se produzca en el código y no puede cambiar el código por motivos de portabilidad, puede desactivar la advertencia.  
   
 Para desactivar las advertencias sobre desuso para estas funciones en CRT, defina **_CRT_SECURE_NO_WARNINGS**. Para desactivar las advertencias sobre variables globales en desuso, defina **_CRT_SECURE_NO_WARNINGS_GLOBALS**. Para obtener más información sobre estas globales y funciones en desuso, consulte [características de seguridad en CRT](../../c-runtime-library/security-features-in-the-crt.md) y [bibliotecas seguras: biblioteca estándar de C++](../../standard-library/safe-libraries-cpp-standard-library.md).  
  
## <a name="unsafe-standard-library-functions"></a>Funciones no seguras de biblioteca estándar  
  
 **' std::** *function_name* **::\_Unchecked\_iteradores::\_Deprecate' llamada a std::** *nombre_función* **con parámetros que pueden ser seguros: esta llamada se basa en el llamador para comprobar que los valores pasados son correctos. Para deshabilitar esta advertencia, utilice -D_SCL_SECURE_NO_WARNINGS. Consulte la documentación sobre cómo usar iteradores comprobados' de Visual C++.**  
  
Esta advertencia aparece en las compilaciones de depuración porque algunas funciones de plantilla de la biblioteca estándar de C++ no comprueba los parámetros son correctos. En la mayoría de los casos, esto es porque no hay suficiente información disponible para la función que se va a comprobar los límites del contenedor o porque los iteradores se pueden usar de forma incorrecta con la función. Esta advertencia ayuda a identificar estos usos de la función, ya que pueden ser una fuente de vulnerabilidades de seguridad en el programa. Para obtener más información, consulta [Checked Iterators](../../standard-library/checked-iterators.md).  
  
Por ejemplo, esta advertencia aparece en el modo de depuración si se pasa un puntero de elemento a `std::copy` en lugar de una matriz sin formato. Para corregir este problema, use una matriz declarada correctamente, por lo que la biblioteca puede comprobar las extensiones de matriz y realice la comprobación de límites.  
  
```cpp  
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>
 
void example(char const * const src) { 
    char dest[1234]; 
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996 
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements 
} 
```  
  
Varios algoritmos de la biblioteca estándar se han actualizado para tener versiones de "intervalo dual" en C ++ 14. Si utiliza las versiones de doble intervalo, el segundo intervalo proporciona la comprobación de límites necesarios:  
  
```cpp  
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>
 
bool example(
    char const * const left, 
    const size_t leftSize, 
    char const * const right, 
    const size_t rightSize) 
{ 
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead: 
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK 
    return result;
}
```  
  
Este ejemplo muestra varias maneras más la biblioteca estándar de puede utilizarse para comprobar el uso de iterador y al uso desactivada puede ser peligroso:  
  
```cpp  
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>  
#include <array>  
#include <iostream>  
#include <iterator>  
#include <numeric>  
#include <string>  
#include <vector>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    vector<int> v(16);  
    iota(v.begin(), v.end(), 0);  
    print("v: ", v);  
  
    // OK: vector::iterator is checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    vector<int> v2(16);  
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });  
    print("v2: ", v2);  
  
    // OK: back_insert_iterator is marked as checked in debug mode  
    // (i.e. an overrun is impossible)  
    vector<int> v3;  
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });  
    print("v3: ", v3);  
  
    // OK: array::iterator is checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    array<int, 16> a4;  
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });  
    print("a4: ", a4);  
  
    // OK: Raw arrays are checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    // NOTE: This applies only when raw arrays are 
    // given to C++ Standard Library algorithms!  
    int a5[16];  
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });  
    print("a5: ", a5);  
  
    // WARNING C4996: Pointers cannot be checked in debug mode  
    // (i.e. an overrun triggers undefined behavior)  
    int a6[16];  
    int * p6 = a6;  
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });  
    print("a6: ", a6);  
  
    // OK: stdext::checked_array_iterator is checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    int a7[16];  
    int * p7 = a7;  
    transform(v.begin(), v.end(), 
        stdext::make_checked_array_iterator(p7, 16), 
        [](int n) { return n * 7; });  
    print("a7: ", a7);  
  
    // WARNING SILENCED: stdext::unchecked_array_iterator 
    // is marked as checked in debug mode, but it performs no checking, 
    // so an overrun triggers undefined behavior  
    int a8[16];  
    int * p8 = a8;  
    transform( v.begin(), v.end(), 
        stdext::make_unchecked_array_iterator(p8), 
        [](int n) { return n * 8; });  
    print("a8: ", a8);  
}  
```  
  
Si ha comprobado que el código no puede tener un búfer saturación error en las funciones de biblioteca estándar que desencadenan esta advertencia, puede desactivar esta advertencia. Para desactivar las advertencias para estas funciones, defina **_SCL_SECURE_NO_WARNINGS**.   
  
## <a name="example-checked-iterators-enabled"></a>Ejemplo: Iteradores comprobados habilitados  
  
Advertencia C4996 también puede producirse si no utiliza un iterador comprobado al compilar con `_ITERATOR_DEBUG_LEVEL` definido como 1 o 2. Se establece en 2 de forma predeterminada para las compilaciones de modo de depuración y en 0 para las compilaciones comerciales. Vea [Checked Iterators](../../standard-library/checked-iterators.md) para obtener más información.  
  
```cpp  
// C4996_checked.cpp  
// compile with: /EHsc /W4 /MDd C4996_checked.cpp  
#define _ITERATOR_DEBUG_LEVEL 2  
  
#include <algorithm>  
#include <iterator>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
    int a[] = { 1, 2, 3 };  
    int b[] = { 10, 11, 12 };  
    copy(a, a + 3, b + 1);   // C4996  
    // try the following line instead:  
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK  
}  
```  
  
## <a name="unsafe-mfc-or-atl-code"></a>Código no seguro MFC o ATL  
  
Advertencia C4996 también puede producirse si se utilizan funciones MFC o ATL que quedaron en desuso por razones de seguridad.  
  
Para corregir este problema, se recomienda que cambiar el código para usar las funciones actualizadas en su lugar.  
  
Para obtener información sobre cómo suprimir estas advertencias, vea [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings) y [_ATL_SECURE_NO_WARNINGS](http://msdn.microsoft.com/Library/587d29d8-a75a-44a3-bec8-f724087e5e73).  
  
## <a name="obsolete-crt-functions-and-variables"></a>Las variables y funciones de CRT obsoletas  
  
**Esta función o variable ha sido reemplazada por una funcionalidad más reciente de biblioteca o el sistema operativo. Considere el uso de** *new_item* **en su lugar. Consulte la ayuda en línea para obtener información detallada.**  
  
Algunas variables globales y funciones de la biblioteca están en desuso por estar obsoletas. Es posible que estas funciones y variables se quiten en una versión futura de la biblioteca. El compilador emite una advertencia de desuso para estos elementos y sugiere la alternativa preferida.  
  
Para corregir este problema, se recomienda que cambiar el código para usar la sugerencia de función o variable.  
  
Para desactivar las advertencias sobre desuso para estos elementos, defina **_CRT_OBSOLETE_NO_WARNINGS**. Para más información, consulte la documentación de la variable o función en desuso.  
  
## <a name="example-marshalling-errors-in-clr-code"></a>Ejemplo: Cálculo de referencias de errores en el código CLR  
  
Advertencia C4996 también puede producirse cuando se utiliza la biblioteca de cálculo de referencias de CLR. En este caso, C4996 es un error y no una advertencia. Este error se produce cuando se usa [serializar_as](../../dotnet/marshal-as.md) para convertir entre dos tipos de datos que requieren un [marshal_context (clase)](../../dotnet/marshal-context-class.md). También puede recibir este error cuando la biblioteca de serialización no admita una conversión. Para más información sobre la biblioteca de cálculo de referencias, vea [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md).  
  
Este ejemplo genera la advertencia C4996 porque la biblioteca de cálculo de referencias exige un contexto para convertir un `System::String` a una `const char *`.  
  
```cpp  
// C4996_Marshal.cpp  
// compile with: /clr   
// C4996 expected  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = marshal_as<const char*>( message );  
   return 0;  
}  
```
  
## <a name="example-user-defined-deprecated-function"></a>Ejemplo: Función en desuso definido por el usuario  
  
Puede usar el atributo desusado en su propio código para advertir a los llamadores cuando ya no se recomienda el uso de determinadas funciones. En este ejemplo, se genera C4996 para la línea en la que se declara la función en desuso y la línea en el que se utiliza la función.  
  
```cpp  
// C4996.cpp  
// compile with: /W3  
// C4996 warning expected  
#include <stdio.h>  
  
// #pragma warning(disable : 4996)  
void func1(void) {  
   printf_s("\nIn func1");  
}  
  
__declspec(deprecated) void func1(int) {  
   printf_s("\nIn func2");  
}  
  
int main() {  
   func1();  
   func1(1);    // C4996  
}  
```  
  

