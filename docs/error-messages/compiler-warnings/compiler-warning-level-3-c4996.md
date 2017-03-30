---
title: Compilador (nivel 3) de la advertencia C4996 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: b790beb88de009e1c7161f3c9af6b3e21c22fd8e
ms.openlocfilehash: aa9586bd0abed0b1fa1d24c777eea8c82c5cedc0
ms.lasthandoff: 03/29/2017

---
# <a name="compiler-warning-level-3-c4996"></a>Compilador (nivel 3) de la advertencia C4996
El compilador encontró una declaración en desuso.  
  
 Esta advertencia o este error tiene varios significados posibles.  
  
 `C4996`se produce cuando el compilador encuentra una función o variable que esté marcada como [en desuso](../../cpp/deprecated-cpp.md). Varias funciones, funciones miembro, funciones de plantilla y variables globales de las bibliotecas de Visual Studio están marcadas como en desuso. Estas funciones pueden tener un nombre preferido distinto, no ser seguras o tener una variante más segura, o estar en desuso. El mensaje de error puede incluir un reemplazo sugerido para la función o variable global en desuso. Puede desactivar esta advertencia con el [advertencia](../../preprocessor/warning.md) pragma o **/wd4996** opción de línea de comandos. También puede utilizar macros de preprocesador para desactivar determinadas clases de advertencias sobre desuso. 

También se emite esta advertencia cuando se intenta acceder a una función, miembro de clase o definición de tipo que tiene C ++ 14 `[[deprecated]]` atributo. Para obtener más información, consulte [atributos estándar de C++](../../cpp/attributes2.md). 
  
 **El nombre POSIX de este elemento está en desuso. En su lugar, utilice el nombre de compatible con ISO C y C++:** new_name**. Consulte la ayuda en línea para obtener información detallada.**  
  
 Algunas funciones POSIX en CRT han cambiado de nombre para que se ajuste a las reglas C99 y C++03 para los nombres de funciones globales definidos por la implementación. En la mayoría de casos, se agregó un carácter de subrayado inicial al nombre de función POSIX para crear un nombre conforme al estándar. El compilador emite una advertencia de desuso para los nombres de funciones originales y sugiere el nombre preferido. Solo los nombres originales están en desuso, no las propias funciones. Para desactivar las advertencias sobre desuso para estas funciones, defina la macro de preprocesador **_CRT_NONSTDC_NO_WARNINGS**. Puede definirla en la línea de comandos si incluye la opción `/D_CRT_NONSTDC_NO_WARNINGS`. Para definir esta macro en Visual Studio, abra el diálogo **Páginas de propiedades** del proyecto. Expanda **Propiedades de configuración**, **C o C++**, **Preprocesador**. En **Definiciones de preprocesador**, agregue `_CRT_NONSTDC_NO_WARNINGS`. Seleccione **Aceptar** para guardar y, luego, vuelva a generar el proyecto. Para definir esta macro solamente en archivos de origen concretos, agregue la línea `#define _CRT_NONSTDC_NO_WARNINGS` antes de cualquier línea que incluya un archivo de encabezado.  
  
 **Esta función o variable puede ser no seguro. Considere el uso de** safe_version **en su lugar. Para deshabilitar el desuso, utilice _CRT_SECURE_NO_WARNINGS.  Consulte la ayuda en línea para obtener información detallada.**  
  
 Algunas variables globales y funciones de biblioteca estándar de C++ y CRT han quedado obsoletas en favor de funciones nuevas más seguras. El compilador emite una advertencia de desuso para estas funciones y sugiere la función preferida. Para desactivar las advertencias sobre desuso para estas funciones en CRT, defina **_CRT_SECURE_NO_WARNINGS**. Para desactivar las advertencias sobre variables globales en desuso, defina **_CRT_SECURE_NO_WARNINGS_GLOBALS**. Para obtener más información sobre estas globales y funciones en desuso, consulte [características de seguridad en CRT](../../c-runtime-library/security-features-in-the-crt.md) y [bibliotecas seguras: biblioteca estándar de C++](../../standard-library/safe-libraries-cpp-standard-library.md).  
  
 **Llamada de función con parámetros que pueden ser seguros: esta llamada se basa en el llamador para comprobar que los valores pasados son correctos. Para deshabilitar esta advertencia, utilice -D_SCL_SECURE_NO_WARNINGS. Consulte la documentación sobre cómo usar iteradores comprobados' de Visual C++.**  
  
 Algunas funciones de plantilla de la biblioteca estándar de C++ no comprueban si los parámetros son correctos. Esta advertencia ayuda a identificar el uso de estas funciones. Para desactivar las advertencias para estas funciones, defina **_SCL_SECURE_NO_WARNINGS**. Para obtener más información, vea [Iteradores comprobados](../../standard-library/checked-iterators.md).  
  
 **Esta función o variable ha sido reemplazada por una funcionalidad más reciente de biblioteca o el sistema operativo. Considere el uso de** new_item **en su lugar. Consulte la ayuda en línea para obtener información detallada.**  
  
 Algunas variables globales y funciones de la biblioteca están en desuso por estar obsoletas. Esa posible que estas funciones y variables se quiten en una versión futura de la biblioteca. El compilador emite una advertencia de desuso para estos elementos y sugiere la alternativa preferida. Para desactivar las advertencias sobre desuso para estos elementos, defina **_CRT_OBSOLETE_NO_WARNINGS**. Para más información, consulte la documentación de la variable o función en desuso.  
  
 **Varios mensajes en código MFC o ATL**  
  
 La advertencia `C4996` también puede producirse si se utilizan funciones MFC o ATL que quedaron desusadas por razones de seguridad. Para suprimir estas advertencias, vea [_AFX_SECURE_NO_WARNINGS](http://msdn.microsoft.com/Library/97dcfd41-1e56-41d5-bf7e-d240b950134b) y [_ATL_SECURE_NO_WARNINGS](http://msdn.microsoft.com/Library/587d29d8-a75a-44a3-bec8-f724087e5e73).  
  
 **Serialización de errores en el código CLR**  
  
 La advertencia `C4996` puede aparecer también cuando se utiliza la biblioteca de cálculo de referencias. En este caso, C4996 es un error y no una advertencia. Este error se producirá cuando se usa [serializar_as](../../dotnet/marshal-as.md) para convertir entre dos tipos de datos que requieren un [marshal_context (clase)](../../dotnet/marshal-context-class.md). También recibirá este error cuando la biblioteca de cálculo de referencias no admita una conversión. Para obtener más información acerca de la biblioteca de serialización, vea [información general de serialización en C++](../../dotnet/overview-of-marshaling-in-cpp.md).  
  
 **Ejemplos que generan C4996**  
  
 En el primer ejemplo, la advertencia `C4996` se genera para la línea en la que se declara la función y la línea en la que se utiliza la función.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo genera C4996.  
  
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
   func1(1);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 La advertencia C4996 también puede producirse si no se utiliza un iterador comprobado al realizar la compilación con un valor de `_ITERATOR_DEBUG_LEVEL` definido (establecido en 1 de forma predeterminada para las compilaciones de modo de depuración).  Vea [Iteradores comprobados](../../standard-library/checked-iterators.md) para obtener más información.  
  
 El ejemplo de código de biblioteca estándar de C++ siguiente genera la advertencia C4996.  
  
```cpp  
// C4996_b.cpp  
// compile with: /EHsc /W3 /c  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <algorithm>  
#include <iterator>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
    int a[] = { 1, 2, 3 };  
    int b[] = { 10, 11, 12 };  
    copy(a, a + 3, b + 1);   // C4996  
    // try the following line instead  
    //   copy(a, a + 3, b);  
    copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK  
}  
  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código de biblioteca estándar de C++ siguiente genera la advertencia C4996 como una advertencia. Los comentarios están alineados.  
  
```cpp  
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
    // (i.e. an overrun will trigger a debug assertion)  
    vector<int> v2(16);  
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });  
    print("v2: ", v2);  
  
    // OK: back_insert_iterator is marked as checked in debug mode  
    // (i.e. an overrun is impossible)  
    vector<int> v3;  
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });  
    print("v3: ", v3);  
  
    // OK: array::iterator is checked in debug mode  
    // (i.e. an overrun will trigger a debug assertion)  
    array<int, 16> a4;  
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });  
    print("a4: ", a4);  
  
    // OK: Raw arrays are checked in debug mode  
    // (i.e. an overrun will trigger a debug assertion)  
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!  
    int a5[16];  
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });  
    print("a5: ", a5);  
  
    // WARNING C4996: Pointers cannot be checked in debug mode  
    // (i.e. an overrun will trigger undefined behavior)  
    int a6[16];  
    int * p6 = a6;  
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });  
    print("a6: ", a6);  
  
    // OK: stdext::checked_array_iterator is checked in debug mode  
    // (i.e. an overrun will trigger a debug assertion)  
    int a7[16];  
    int * p7 = a7;  
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });  
    print("a7: ", a7);  
  
    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode  
    // (i.e. it performs no checking, so an overrun will trigger undefined behavior)  
    int a8[16];  
    int * p8 = a8;  
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });  
    print("a8: ", a8);  
}  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera la advertencia C4996 porque la biblioteca de cálculo de referencias exige un contexto para convertir un objeto `System::String` en `const char *`.  
  
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
