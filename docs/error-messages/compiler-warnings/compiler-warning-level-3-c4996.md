---
title: "Advertencia del compilador (nivel 3) C4996 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4996"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4996"
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
caps.latest.revision: 34
caps.handback.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4996
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El compilador encontró una declaración en desuso.  
  
 Esta advertencia o este error tiene varios significados posibles.  
  
 `C4996` se produce cuando el compilador encuentra una función o una variable que esté marcada como [en desuso](../../cpp/deprecated-cpp.md). Varias funciones, funciones miembro, funciones de plantilla y variables globales de las bibliotecas de Visual Studio están marcadas como en desuso. Estas funciones pueden tener un nombre preferido distinto, no ser seguras o tener una variante más segura, o estar obsoletas. El mensaje de error puede incluir un reemplazo sugerido para la función o variable global en desuso. Puede desactivar esta advertencia con el pragma [warning](../../preprocessor/warning.md) o la opción **\/wd4996** de la línea de comandos. También puede utilizar macros de preprocesador para desactivar determinadas clases de advertencias sobre desuso.  
  
 **El nombre POSIX de este elemento está en desuso. En su lugar, utilice el nombre conforme a ISO C y C\+\+:** new\_name**. Consulte la ayuda en línea para ver información detallada.**  
  
 Algunas funciones POSIX en CRT han cambiado de nombre para que se ajuste a las reglas C99 y C\+\+03 para los nombres de funciones globales definidos por la implementación. En la mayoría de casos, se agregó un carácter de subrayado inicial al nombre de función POSIX para crear un nombre conforme al estándar. El compilador emite una advertencia de desuso para los nombres de funciones originales y sugiere el nombre preferido. Solo los nombres originales están en desuso, no las propias funciones. Para desactivar las advertencias sobre desuso para estas funciones, defina la macro de preprocesador **\_CRT\_NONSTDC\_NO\_WARNINGS**. Puede definirla en la línea de comandos si incluye la opción  `/D_CRT_NONSTDC_NO_WARNINGS`. Para definir esta macro en Visual Studio, abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Expanda **Propiedades de configuración**, **C o C\+\+**, **Preprocesador**. En **Definiciones de preprocesador**, agregue `_CRT_NONSTDC_NO_WARNINGS`. Seleccione **Aceptar** para guardar y, luego, vuelva a generar el proyecto. Para definir esta macro solamente en archivos de origen concretos, agregue la línea `#define _CRT_NONSTDC_NO_WARNINGS` antes de cualquier línea que incluya un archivo de encabezado.  
  
 **Esta función o variable puede no ser segura. Considere la posibilidad de usar**  safe\_version **en su lugar. Para deshabilitar el desuso, utilice \_CRT\_SECURE\_NO\_WARNINGS.  Consulte la ayuda en línea para ver información detallada.**  
  
 Algunas globales y funciones de la biblioteca estándar de C\+\+ y CRT han quedado en desuso en pro de funciones nuevas más seguras. El compilador emite una advertencia de desuso para estas funciones y sugiere la función preferida. Para desactivar las advertencias sobre desuso para estas funciones en CRT, defina **\_CRT\_SECURE\_NO\_WARNINGS**. Para desactivar las advertencias sobre variables globales en desuso, defina **\_CRT\_SECURE\_NO\_WARNINGS\_GLOBALS**. Para más información sobre estas globales y funciones en desuso, consulte [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md) y [Bibliotecas seguras: Biblioteca estándar de C\+\+](../../standard-library/safe-libraries-cpp-standard-library.md).  
  
 **Llamada de función con parámetros que pueden no ser seguros: esta llamada depende del llamador para comprobar que los valores pasados son correctos. Para deshabilitar esta advertencia, utilice \-D\_SCL\_SECURE\_NO\_WARNINGS. Consulte en la documentación cómo se usan los 'iteradores comprobados' de Visual C\+\+.**  
  
 Algunas funciones de plantilla de la biblioteca estándar de C\+\+ no comprueban si los parámetros son correctos. Esta advertencia ayuda a identificar el uso de estas funciones. Para desactivar las advertencias para estas funciones, defina **\_SCL\_SECURE\_NO\_WARNINGS**. Para obtener más información, consulta [Iteradores activados](../../standard-library/checked-iterators.md).  
  
 **Se reemplazó esta función o variable por una nueva funcionalidad de sistema operativo o biblioteca. Considere la posibilidad de usar** new\_item **en su lugar. Consulte la ayuda en línea para ver información detallada.**  
  
 Algunas variables globales y funciones de la biblioteca están en desuso por estar obsoletas. Es posible que estas funciones y variables se quiten en una versión futura de la biblioteca. El compilador emite una advertencia de desuso para estos elementos y sugiere la alternativa preferida. Para desactivar las advertencias sobre desuso para estos elementos, defina **\_CRT\_OBSOLETE\_NO\_WARNINGS**. Para más información, consulte la documentación de la variable o función en desuso.  
  
 **Varios mensajes en código MFC o ATL**  
  
 La advertencia `C4996` también puede producirse si se utilizan funciones MFC o ATL que quedaron desusadas por razones de seguridad. Para suprimir estas advertencias, vea [\_AFX\_SECURE\_NO\_WARNINGS](../Topic/_AFX_SECURE_NO_WARNINGS.md) y [\_ATL\_SECURE\_NO\_WARNINGS](../Topic/_ATL_SECURE_NO_WARNINGS.md).  
  
 **Cálculo de referencias de errores en código CLR**  
  
 La advertencia `C4996` puede aparecer también cuando se utiliza la biblioteca de cálculo de referencias. En este caso, C4996 es un error y no una advertencia. Este error se producirá al utilizar [marshal\_as](../../dotnet/marshal-as.md) para convertir entre dos tipos de datos que requieren una [marshal\_context \(Clase\)](../../dotnet/marshal-context-class.md). También recibirá este error cuando la biblioteca de cálculo de referencias no admita una conversión. Para más información sobre la biblioteca de cálculo de referencias, vea [Información general del cálculo de referencias en C\+\+](../../dotnet/overview-of-marshaling-in-cpp.md).  
  
 **Ejemplos que generan C4996**  
  
 En el primer ejemplo, la advertencia `C4996` se genera para la línea en la que se declara la función y la línea en la que se utiliza la función.  
  
## Ejemplo  
 El siguiente ejemplo genera C4996.  
  
```cpp  
// C4996.cpp // compile with: /W3 // C4996 warning expected #include <stdio.h> // #pragma warning(disable : 4996) void func1(void) { printf_s("\nIn func1"); } __declspec(deprecated) void func1(int) { printf_s("\nIn func2"); } int main() { func1(); func1(1); }  
```  
  
## Ejemplo  
 La advertencia C4996 también puede producirse si no se utiliza un iterador comprobado al realizar la compilación con un valor de `_ITERATOR_DEBUG_LEVEL` definido \(establecido en 1 de forma predeterminada para las compilaciones de modo de depuración\).  Vea [Iteradores activados](../../standard-library/checked-iterators.md) para obtener más información.  
  
 En el siguiente ejemplo de código de STL se genera la advertencia C4996.  
  
```cpp  
// C4996_b.cpp // compile with: /EHsc /W3 /c #define _ITERATOR_DEBUG_LEVEL 1 #include <algorithm> #include <iterator> using namespace std; using namespace stdext; int main() { int a[] = { 1, 2, 3 }; int b[] = { 10, 11, 12 }; copy(a, a + 3, b + 1);   // C4996 // try the following line instead //   copy(a, a + 3, b); copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK }  
  
```  
  
## Ejemplo  
 En el siguiente ejemplo de código de STL se genera C4996 como una advertencia: Los comentarios están alineados.  
  
```cpp  
#include <algorithm> #include <array> #include <iostream> #include <iterator> #include <numeric> #include <string> #include <vector> using namespace std; template <typename C> void print(const string& s, const C& c) { cout << s; for (const auto& e : c) { cout << e << " "; } cout << endl; } int main() { vector<int> v(16); iota(v.begin(), v.end(), 0); print("v: ", v); // OK: vector::iterator is checked in debug mode // (i.e. an overrun will trigger a debug assertion) vector<int> v2(16); transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; }); print("v2: ", v2); // OK: back_insert_iterator is marked as checked in debug mode // (i.e. an overrun is impossible) vector<int> v3; transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; }); print("v3: ", v3); // OK: array::iterator is checked in debug mode // (i.e. an overrun will trigger a debug assertion) array<int, 16> a4; transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; }); print("a4: ", a4); // OK: Raw arrays are checked in debug mode // (i.e. an overrun will trigger a debug assertion) // NOTE: This applies only when raw arrays are given to STL algorithms! int a5[16]; transform(v.begin(), v.end(), a5, [](int n) { return n * 5; }); print("a5: ", a5); // WARNING C4996: Pointers cannot be checked in debug mode // (i.e. an overrun will trigger undefined behavior) int a6[16]; int * p6 = a6; transform(v.begin(), v.end(), p6, [](int n) { return n * 6; }); print("a6: ", a6); // OK: stdext::checked_array_iterator is checked in debug mode // (i.e. an overrun will trigger a debug assertion) int a7[16]; int * p7 = a7; transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; }); print("a7: ", a7); // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode // (i.e. it performs no checking, so an overrun will trigger undefined behavior) int a8[16]; int * p8 = a8; transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; }); print("a8: ", a8); }  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente se genera la advertencia C4996 porque la biblioteca de cálculo de referencias exige un contexto para convertir un objeto `System::String` en `const char *`.  
  
```cpp  
// C4996_Marshal.cpp // compile with: /clr // C4996 expected #include <stdlib.h> #include <string.h> #include <msclr\marshal.h> using namespace System; using namespace msclr::interop; int main() { String^ message = gcnew String("Test String to Marshal"); const char* result; result = marshal_as<const char*>( message ); return 0; }  
```