---
title: Del compilador (nivel 3) de la advertencia C4996
ms.date: 11/17/2017
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: cbb93bdba5853ed47bc3326d47bbb3c65ad7ce41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472181"
---
# <a name="compiler-warning-level-3-c4996"></a>Del compilador (nivel 3) de la advertencia C4996

El compilador encontró una declaración en desuso. **Esta advertencia siempre es un mensaje deliberado del autor de la biblioteca o el archivo de encabezado incluido que no debe utilizar el símbolo en desuso sin entender las consecuencias.** El mensaje de advertencia real se especifica mediante el modificador de degradación o el atributo en el sitio de la declaración.

Estos son algunos mensajes de advertencia C4996 comunes generados por la biblioteca en tiempo de ejecución de C y la biblioteca estándar, pero no es una lista exhaustiva. Siga los vínculos o siga leyendo para que ver formas de solucionar el problema o para desactivar la advertencia.

- [El nombre POSIX de este elemento está en desuso. En su lugar, use el nombre conforme a ISO C y C++: *new_name*. Consulte la ayuda en línea para obtener información detallada.](#posix-function-names)

- [Esta función o variable puede no ser seguro. Considere el uso de *safe_version* en su lugar. Para deshabilitar el desuso, utilice \_CRT\_SECURE\_n\_advertencias.  Consulte la ayuda en línea para obtener información detallada.](#unsafe-crt-library-functions)

- [' std::*function_name*::\_Unchecked\_iteradores::\_Deprecate' llamar a std::*nombre_función*con parámetros que pueden ser seguros; esta llamada se basa en el llamador para comprobar que los valores pasados son correctos. Para deshabilitar esta advertencia, utilice -D_SCL_SECURE_NO_WARNINGS. Consulte la documentación sobre cómo usar Visual C++ 'Iteradores activados'](#unsafe-standard-library-functions)

- [Esta función o variable se ha sustituido por nuevas funcionalidades del sistema operativo o biblioteca. Considere el uso de *new_item* en su lugar. Consulte la ayuda en línea para obtener información detallada.](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>Motivo

Advertencia C4996 se produce cuando el compilador encuentra una función o variable que está marcado como [en desuso](../../cpp/deprecated-cpp.md) mediante el uso de un `__declspec(deprecated)` modificador, o cuando se intenta tener acceso a una función, un miembro de clase o un typedef que contenga la C ++ 14 [ \[ \[en desuso\] \] ](../../cpp/attributes.md) atributo. Puede usar el `__declspec(deprecated)` modificador o `[[deprecated]]` usted mismo atributo en sus bibliotecas o archivos de encabezado para advertir a los clientes sobre definiciones de tipos, miembros, variables o funciones en desuso.

## <a name="remarks"></a>Comentarios

Muchas funciones, funciones miembro, funciones de plantilla y variables globales en las bibliotecas en Visual Studio se marcan como *en desuso*. Estas funciones están en desuso porque es posible que tiene un nombre preferido distinto, pueden ser seguras o tener una variante más segura, o puede ser obsoleto. Muchos de los mensajes de desuso incluyen un reemplazo sugerido para la función en desuso o una variable global.

Para corregir este problema, generalmente recomendamos que cambiar el código para usar las funciones de más seguras o actualizadas sugeridas y variables globales en su lugar. Si necesita utilizar las funciones existentes o las variables por motivos de portabilidad, se puede desactivar la advertencia.

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>Para desactivar la advertencia sin corregir el problema

Puede desactivar la advertencia para una línea de código específica mediante la [advertencia](../../preprocessor/warning.md) pragma, `#pragma warning(suppress : 4996)`. También puede desactivar la advertencia dentro de un archivo mediante el uso de la directiva pragma warning, `#pragma warning(disable : 4996)`.

Puede desactivar la advertencia globalmente en las compilaciones de línea de comandos mediante el uso de la **/wd4996** opción de línea de comandos.

Para desactivar la advertencia de todo un proyecto en el IDE de Visual Studio:

- Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener información sobre cómo usar el cuadro de diálogo páginas de propiedades, vea [páginas de propiedades](../../ide/property-pages-visual-cpp.md).
- Seleccione el **propiedades de configuración**, **C o C++**, **avanzadas** página.
- Editar el **deshabilitar advertencias específicas** propiedad va a agregar `4996`. Elija **Aceptar** para aplicar los cambios.

También puede usar macros de preprocesador para desactivar determinadas clases específicas de las advertencias sobre desuso utilizadas en las bibliotecas. Estas macros se describen a continuación.

Para definir una macro de preprocesador en Visual Studio:

- Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener información sobre cómo usar el cuadro de diálogo páginas de propiedades, vea [páginas de propiedades](../../ide/property-pages-visual-cpp.md).
- Expanda **propiedades de configuración > C/C ++ > preprocesador**.
- En el **definiciones del preprocesador** propiedad, agregue el nombre de macro. Seleccione **Aceptar** para guardar y, luego, vuelva a generar el proyecto.

Para definir una macro sólo en los archivos de origen específico, agregue una línea como `#define EXAMPLE_MACRO_NAME` antes de cualquier línea que incluye un archivo de encabezado.

## <a name="specific-c4996-messages"></a>Mensajes de advertencia C4996 específicos

Estas son algunas de las fuentes comunes de errores y advertencias C4996.

### <a name="posix-function-names"></a>Nombres de función POSIX

**El nombre POSIX de este elemento está en desuso. En su lugar, use el nombre conforme a ISO C y C++:** *new_name*. **Consulte la Ayuda en línea para obtener más información.**

Microsoft ha cambiado el nombre de algunas funciones POSIX en CRT para ajustarse a C99 y C ++ 03 reglas para los nombres de funciones globales definidos en la implementación. Solo los nombres POSIX originales están en desuso, no las propias funciones. En la mayoría de casos, se agregó un carácter de subrayado inicial al nombre de función POSIX para crear un nombre conforme al estándar. El compilador emite una advertencia de desuso para el nombre de función original y sugiere el nombre preferido.

Para corregir este problema, generalmente recomendamos que cambiar el código para usar los nombres de función sugeridos en su lugar. Sin embargo, los nombres actualizados son específicas de Microsoft. Si tiene que usar los nombres de función existente por motivos de portabilidad, puede desactivar estas advertencias. Las funciones POSIX siguen estando disponibles en la biblioteca en sus nombres originales.

Para desactivar las advertencias sobre desuso para estas funciones, defina la macro de preprocesador  **\_CRT\_NONSTDC\_NO\_advertencias**. Puede definir esta macro en la línea de comandos si incluye la opción `/D_CRT_NONSTDC_NO_WARNINGS`.

### <a name="unsafe-crt-library-functions"></a>Funciones de biblioteca de CRT no seguras

**Esta función o variable puede no ser seguro. Considere el uso de** *safe_version* **en su lugar. Para deshabilitar el desuso, utilice \_CRT\_SECURE\_n\_advertencias.  Consulte la ayuda en línea para obtener información detallada.**

Microsoft ha desusado algunas funciones de biblioteca estándar de C++ y CRT y variables globales en favor de versiones más seguras. En la mayoría de los casos, las funciones en desuso permiten unchecked acceso de lectura o escritura a los búferes, lo que puede provocar serios problemas de seguridad. El compilador emite una advertencia de desuso para estas funciones y sugiere la función preferida.

Para corregir este problema, se recomienda usar la función o variable *safe_version* en su lugar. Si ha comprobado que no es posible que una sobrescritura de búfer o overread que se produzca en el código y no puede cambiar el código por motivos de portabilidad, puede desactivar la advertencia.

Para desactivar las advertencias sobre desuso para estas funciones de CRT, defina  **\_CRT\_SECURE\_NO\_advertencias**. Para desactivar las advertencias sobre variables globales en desuso, defina  **\_CRT\_SECURE\_NO\_advertencias\_GLOBALS**. Para obtener más información acerca de estas funciones en desuso y variables globales, consulte [características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md) y [bibliotecas seguras: biblioteca estándar de C++](../../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="unsafe-standard-library-functions"></a>Funciones de biblioteca estándar no seguras

__' std::__*function_name*__::\_Unchecked\_iteradores::\_Deprecate' llamar a std::__*function_name* **con parámetros que pueden ser seguros; esta llamada depende del llamador para comprobar que los valores pasados son correctos. Para deshabilitar esta advertencia, use -D\_SCL\_SECURE\_n\_advertencias. Consulte la documentación sobre cómo usar Visual C++ 'Iteradores activados'**

Esta advertencia aparece en las compilaciones de depuración porque algunas funciones de plantilla de la biblioteca estándar de C++ no comprueban los parámetros son correctos. En la mayoría de los casos, esto es porque no hay suficiente información disponible para la función para comprobar los límites del contenedor, o porque se pueden usar incorrectamente los iteradores con la función. Esta advertencia ayuda a identificar estos usos de la función, ya que pueden ser una fuente de vulnerabilidades de seguridad grave en el programa. Para obtener más información, consulta [Checked Iterators](../../standard-library/checked-iterators.md).

Por ejemplo, esta advertencia aparece en modo de depuración si se pasa un puntero de elemento a `std::copy` en lugar de una matriz sin formato. Para corregir este problema, utilice una matriz declarada de forma adecuada, para que pueda comprobar las extensiones de la matriz y realizar la comprobación de límites de la biblioteca.

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

Varios algoritmos de la biblioteca estándar se actualizaron para tener versiones "rango dual" en C ++ 14. Si usa las versiones de rango dual, el segundo intervalo proporciona la comprobación de límites necesarios:

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

Este ejemplo muestra más formas de la biblioteca estándar que puede utilizarse para comprobar el uso de iterador, y cuando uso unchecked puede ser peligrosa:

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

Si ha comprobado que el código no puede tener un búfer de saturación del error en las funciones de biblioteca estándar que desencadenan esta advertencia, es posible que desee desactivar esta advertencia. Para desactivar las advertencias para estas funciones, defina  **\_SCL\_SECURE\_NO\_advertencias**.

### <a name="checked-iterators-enabled"></a>Iteradores comprobados habilitados

Advertencia C4996 también puede producirse si no usa un iterador comprobado al compilar con `_ITERATOR_DEBUG_LEVEL` definido como 1 o 2. Se establece en 2 de forma predeterminada para compilaciones de modo de depuración y en 0 para las compilaciones comerciales. Vea [Checked Iterators](../../standard-library/checked-iterators.md) para obtener más información.

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

### <a name="unsafe-mfc-or-atl-code"></a>Código no seguro MFC o ATL

Advertencia C4996 también puede producirse si usa funciones MFC o ATL que quedaron desusadas por razones de seguridad.

Para corregir este problema, se recomienda encarecidamente que cambiar el código para usar las funciones actualizadas en su lugar.

Para obtener información sobre cómo suprimir estas advertencias, vea [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

### <a name="obsolete-crt-functions-and-variables"></a>Las variables y funciones de CRT obsoletas

**Esta función o variable se ha sustituido por nuevas funcionalidades del sistema operativo o biblioteca. Considere el uso de** *new_item* **en su lugar. Consulte la ayuda en línea para obtener información detallada.**

Algunas variables globales y funciones de la biblioteca están en desuso por estar obsoletas. Es posible que estas funciones y variables se quiten en una versión futura de la biblioteca. El compilador emite una advertencia de desuso para estos elementos y sugiere la alternativa preferida.

Para corregir este problema, se recomienda que cambiar el código para usar la función sugerido o variable.

Para desactivar las advertencias sobre desuso para estos elementos, defina  **\_CRT\_obsoleto\_NO\_advertencias**. Para más información, consulte la documentación de la variable o función en desuso.

### <a name="marshalling-errors-in-clr-code"></a>Cálculo de referencias de errores en código CLR

Advertencia C4996 también puede producirse cuando se usa la biblioteca de cálculo de referencias de CLR. En este caso, C4996 es un error y no una advertencia. Este error se produce cuando se usa [serializar_as](../../dotnet/marshal-as.md) para convertir entre dos tipos de datos que requieren un [marshal_context Class](../../dotnet/marshal-context-class.md). También puede recibir este error cuando la biblioteca de serialización no es compatible con una conversión. Para más información sobre la biblioteca de cálculo de referencias, vea [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md).

En este ejemplo genera la advertencia C4996 porque la biblioteca de serialización requiere un contexto para convertir un `System::String` a un `const char *`.

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

## <a name="example-user-defined-deprecated-function"></a>Ejemplo: Función desusada definido por el usuario

Puede usar el atributo desusado en su propio código para advertir a los autores de llamadas cuando ya no se recomienda el uso de ciertas funciones. En este ejemplo, se genera C4996 para la línea en la que se declara la función en desuso y la línea en el que se usa la función.

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
