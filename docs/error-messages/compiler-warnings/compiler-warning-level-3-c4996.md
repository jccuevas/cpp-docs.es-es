---
title: ADVERTENCIA del compilador (nivel 3) C4996
description: Explica por qué se produce C4996 de advertencia del compilador y describe qué hacer con él.
ms.date: 11/25/2019
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 98662dc0b5439c1f8857e4f2ad259793a4d03e41
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865232"
---
# <a name="compiler-warning-level-3-c4996"></a>ADVERTENCIA del compilador (nivel 3) C4996

El código usa una función, un miembro de clase, una variable o una definición de tipo que está marcada como *desusada*. Los símbolos están desusados mediante un modificador [__declspec (en desuso)](../../cpp/deprecated-cpp.md) o el\[de c++ 14 [\[\]\]en desuso](../../cpp/attributes.md) . El mensaje de advertencia C4996 real se especifica mediante el modificador `deprecated` o el atributo de la declaración.

> [!IMPORTANT]
> Esta advertencia siempre es un mensaje deliberado del autor del archivo de encabezado que declara el símbolo. No utilice el símbolo en desuso sin conocer las consecuencias.

## <a name="remarks"></a>Observaciones

Muchas funciones, funciones miembro, funciones de plantilla y variables globales de las bibliotecas de Visual Studio están *desusadas*. Algunos, como POSIX y las funciones específicas de Microsoft, están desusados porque ahora tienen un nombre preferido diferente. Algunas funciones de la biblioteca en tiempo de ejecución de C están desusadas porque no son seguras y tienen una variante más segura. Otras están desusadas porque están obsoletas. Los mensajes de degradación suelen incluir un reemplazo sugerido para la función o variable global en desuso.

## <a name="turn-off-the-warning"></a>Desactivar la advertencia

Para corregir un problema de C4996, normalmente se recomienda cambiar el código. En su lugar, use las funciones sugeridas y las variables globales. Si necesita usar las funciones o variables existentes por motivos de portabilidad, puede desactivar la advertencia.

Para desactivar la advertencia para una línea de código concreta, use la pragma [warning](../../preprocessor/warning.md) `#pragma warning(suppress : 4996)`.

Para desactivar la advertencia en un archivo, use la pragma warning `#pragma warning(disable : 4996)`.

Para desactivar la advertencia globalmente en compilaciones de línea de comandos, use la opción de línea de comandos [/wd4996](../../build/reference/compiler-option-warning-level.md) .

Para desactivar la advertencia para un proyecto completo en el IDE de Visual Studio:

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto. Para obtener información sobre cómo usar el cuadro de diálogo páginas de propiedades, vea [páginas de propiedades](../../build/reference/property-pages-visual-cpp.md).

1. Seleccione las **propiedades de configuración** > página **avanzadas** de **CC++ /**  > .

1. Edite la propiedad **deshabilitar advertencias específicas** para agregar `4996`. Elija **Aceptar** para aplicar los cambios.

También puede usar macros de preprocesador para desactivar determinadas clases específicas de advertencias de desuso usadas en las bibliotecas. Estas macros se describen a continuación.

Para definir una macro de preprocesador en Visual Studio:

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto. Para obtener información sobre cómo usar el cuadro de diálogo páginas de propiedades, vea [páginas de propiedades](../../build/reference/property-pages-visual-cpp.md).

1. Expanda **propiedades de configuración >C++ preprocesador de C/>** .

1. En la propiedad **definiciones de preprocesador** , agregue el nombre de la macro. Seleccione **Aceptar** para guardar y, luego, vuelva a generar el proyecto.

Para definir una macro solo en archivos de código fuente específicos, agregue una línea como `#define EXAMPLE_MACRO_NAME` antes de cualquier línea que incluya un archivo de encabezado.

Estos son algunos de los orígenes comunes de errores y advertencias de C4996:

## <a name="posix-function-names"></a>Nombres de funciones POSIX

**El nombre POSIX de este elemento está en desuso. En su lugar, use ISO C y C++ el nombre compatible:** *New-Name*. **Consulte la ayuda en línea para obtener más información.**

Microsoft ha cambiado el nombre de algunas funciones de biblioteca POSIX y específicas de Microsoft en CRT para cumplir las restricciones de C99 y C++ 03 en los nombres reservados y globales definidos por la implementación. *Solo los nombres están en desuso, no las propias funciones*. En la mayoría de los casos, se agregó un carácter de subrayado inicial al nombre de la función para crear un nombre conforme. El compilador emite una advertencia de desuso para el nombre de función original y sugiere el nombre preferido.

Para corregir este problema, normalmente se recomienda cambiar el código para usar los nombres de función sugeridos en su lugar. Sin embargo, los nombres actualizados son específicos de Microsoft. Si necesita usar los nombres de función existentes por motivos de portabilidad, puede desactivar estas advertencias. Las funciones siguen estando disponibles en la biblioteca bajo sus nombres originales.

Para desactivar las advertencias sobre desuso para estas funciones, defina la macro de preprocesador **\_CRT\_NONSTDC\_no\_advertencias**. Puede definir esta macro en la línea de comandos incluyendo la opción `/D_CRT_NONSTDC_NO_WARNINGS`.

## <a name="unsafe-crt-library-functions"></a>Funciones de la biblioteca CRT no segura

**Esta función o variable puede no ser segura. Considere la posibilidad de usar** *Safe-version* **en su lugar. Para deshabilitar el desuso, utilice \_CRT\_protección\_NO\_advertencias.  Consulte la ayuda en línea para obtener más información.**

Microsoft ha dejado de usar algunas C++ funciones de la biblioteca CRT y estándar, así como las versiones más seguras. La mayoría de las funciones en desuso permiten el acceso de lectura o escritura no comprobada a los búferes. Su uso incorrecto puede dar lugar a graves problemas de seguridad. El compilador emite una advertencia de desuso para estas funciones y sugiere la función preferida.

Para corregir este problema, se recomienda usar la función o la variable *Safe-version* en su lugar. A veces no se puede, por motivos de portabilidad o de compatibilidad con versiones anteriores. Compruebe detenidamente que no es posible que se produzca una sobrescritura de búfer o una sobrelectura en el código. Después, puede desactivar la advertencia.

Para desactivar las advertencias sobre desuso para estas funciones en CRT, defina **\_crt\_protección\_no\_advertencias**.

Para desactivar las advertencias sobre variables globales en desuso, defina **\_CRT\_seguro\_no\_advertencias\_globales**.

Para obtener más información sobre estas funciones desusadas y las variables globales, vea [características de seguridad en CRT](../../c-runtime-library/security-features-in-the-crt.md) y [bibliotecas seguras: C++ biblioteca estándar](../../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="unsafe-standard-library-functions"></a>Funciones de la biblioteca estándar no segura

__' STD::__ *function_name* __::\_unchecked\_iteradores::\_deprecated ' Call to STD::__ *function_name* **con parámetros que pueden no ser seguros: esta llamada depende del llamador para comprobar que los valores pasados son correctos. Para deshabilitar esta advertencia, use-D\_SCL\_protección\_NO\_advertencias. Consulte la documentación sobre cómo usar los C++ iteradores comprobados de Visual**

Esta advertencia aparece en las compilaciones C++ de depuración porque ciertas funciones de plantilla de la biblioteca estándar no comprueban los parámetros para comprobar su exactitud. A menudo, esto se debe a que no hay suficiente información disponible para que la función Compruebe los límites del contenedor. O bien, dado que los iteradores se pueden usar incorrectamente con la función. Esta advertencia le ayuda a identificar estas funciones, ya que pueden ser una fuente de vulnerabilidades de seguridad serias en el programa. Para obtener más información, vea [iteradores comprobados](../../standard-library/checked-iterators.md).

Por ejemplo, esta advertencia aparece en modo de depuración si se pasa un puntero de elemento a `std::copy`, en lugar de una matriz sin formato. Para corregir este problema, use una matriz declarada correctamente, de modo que la biblioteca pueda comprobar las extensiones de la matriz y realizar la comprobación de los límites.

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

Varios algoritmos de la biblioteca estándar se actualizaron para tener versiones de "intervalo dual" en C++ 14. Si usa las versiones de intervalo dual, el segundo intervalo proporciona la comprobación de límites necesaria:

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

En este ejemplo se muestran varias formas más de usar la biblioteca estándar para comprobar el uso de iteradores y, cuando el uso no comprobado puede ser peligroso:

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

Si ha comprobado que el código no puede tener un error de saturación del búfer, puede desactivar esta advertencia. Para desactivar las advertencias para estas funciones, defina **\_SCL\_seguro\_no\_advertencias**.

## <a name="checked-iterators-enabled"></a>Iteradores comprobados habilitados

C4996 también se puede producir si no se usa un iterador comprobado cuando `_ITERATOR_DEBUG_LEVEL` se define como 1 o 2. Está establecido en 2 de forma predeterminada para las compilaciones en modo de depuración y en 0 para las compilaciones comerciales. Para obtener más información, vea [iteradores comprobados](../../standard-library/checked-iterators.md).

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

## <a name="unsafe-mfc-or-atl-code"></a>Código MFC o ATL no seguro

C4996 puede producirse si se utilizan funciones MFC o ATL desusadas por razones de seguridad.

Para corregir este problema, se recomienda encarecidamente cambiar el código para usar las funciones actualizadas en su lugar.

Para obtener información sobre cómo suprimir estas advertencias, vea [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

## <a name="obsolete-crt-functions-and-variables"></a>Variables y funciones de CRT obsoletas

**Esta función o variable se ha sustituido por una nueva funcionalidad de la biblioteca o del sistema operativo. Considere la posibilidad de usar** *new_item* **en su lugar. Consulte la ayuda en línea para obtener más información.**

Algunas variables globales y funciones de la biblioteca están en desuso por estar obsoletas. Es posible que estas funciones y variables se quiten en una versión futura de la biblioteca. El compilador emite una advertencia de desuso para estos elementos y sugiere la alternativa preferida.

Para corregir este problema, se recomienda cambiar el código para usar la función o variable sugeridas.

Para desactivar las advertencias sobre desuso para estos elementos, defina **\_CRT\_obsoleto\_no\_advertencias**. Para más información, consulte la documentación de la variable o función en desuso.

## <a name="marshaling-errors-in-clr-code"></a>Serialización de errores en código CLR

C4996 también se puede producir cuando se usa la biblioteca de serialización de CLR. En este caso, C4996 es un error, no una advertencia. El error se produce cuando se usa [marshal_as](../../dotnet/marshal-as.md) para convertir entre dos tipos de datos que requieren una [clase marshal_context](../../dotnet/marshal-context-class.md). También puede recibir este error cuando la biblioteca de serialización no admite una conversión. Para obtener más información sobre la biblioteca de cálculo de referencias, vea [información general C++sobre el cálculo de referencias en ](../../dotnet/overview-of-marshaling-in-cpp.md).

En este ejemplo se genera C4996 porque la biblioteca de cálculo de referencias requiere un contexto para convertir de un `System::String` a un `const char *`.

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

## <a name="example-user-defined-deprecated-function"></a>Ejemplo: función desusada definida por el usuario

Puede usar el atributo deprecated en su propio código para avisar a los autores de las llamadas cuando ya no se recomienda el uso de determinadas funciones. En este ejemplo, C4996 se genera en dos lugares: uno para la línea en la que se declara la función en desuso y otro para la línea en la que se usa la función.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
