---
title: /Zc:ternary (Exigir reglas de operador condicionales)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 7c95f061e195ccf7fef8a6a21d193b257baa5f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335678"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (Exigir reglas de operador condicionales)

Habilite la aplicación de las reglas estándar de C++ para los tipos y la calificación const o volatile (cv) del segundo y tercer operando en una expresión de operador condicional.

## <a name="syntax"></a>Sintaxis

> **/Zc:ternario****-**[ ]

## <a name="remarks"></a>Observaciones

A partir de Visual Studio 2017, el compilador admite el comportamiento del *operador condicional* estándar C++ (**?:**). También se conoce como el *operador ternario.* El estándar C++ requiere que los operandos ternarios cumplan una de tres condiciones: los operandos deben ser del mismo tipo y **const** o **calificación volátil** (calificación cv), o sólo un operando debe ser inequívocamente convertible al mismo tipo y cv-calificación que el otro. O bien, uno o ambos operandos deben ser una expresión throw. En versiones anteriores a Visual Studio 2017 versión 15.5, el compilador permitía conversiones que el estándar considera ambiguas.

Cuando se especifica la opción **/Zc:ternary,** el compilador se ajusta al estándar. Rechaza el código que no cumple las reglas para los tipos coincidentes y la calificación cv del segundo y tercer operando.

La opción **/Zc:ternary** está desactivada de forma predeterminada en Visual Studio 2017. Use **/Zc:ternary** para habilitar el comportamiento conforme o **/Zc:ternary-** para especificar explícitamente el comportamiento del compilador no conforme anterior. La opción [/permissive-](permissive-standards-conformance.md) habilita implícitamente esta opción, pero se puede invalidar mediante **/Zc:ternary-**.

### <a name="examples"></a>Ejemplos

En este ejemplo se muestra cómo una clase que proporciona la inicialización no explícita de un tipo y la conversión a un tipo puede dar lugar a conversiones ambiguas. Este código es aceptado por el compilador de forma predeterminada, pero rechazado cuando se especifica **/Zc:ternary** o **/permissive-.**

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

Para corregir este código, realice una conversión explícita al tipo común preferido o impida una dirección de conversión de tipos. Puede evitar que el compilador coincida con una conversión de tipos haciendo que la conversión sea explícita.

Una excepción importante a este patrón común es cuando el tipo de los `const char*`operandos es uno de los tipos de cadena terminadas en null, como , `const char16_t*`, etc. También puede reproducir el efecto con tipos de matriz y los tipos de puntero a los que se descomponen. El comportamiento cuando el segundo `?:` o tercer operando real es un literal de cadena de tipo correspondiente depende del estándar de lenguaje utilizado. C++17 ha cambiado la semántica para este caso de C++14. Como resultado, el compilador acepta el código del ejemplo siguiente en el valor predeterminado **/std:c++14**, pero lo rechaza al especificar **/std:c++17**.

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

Para corregir este código, convierta uno de los operandos explícitamente.

En **/Zc:ternary**, el compilador rechaza los operadores condicionales donde uno de los argumentos es de tipo **void**y el otro no es una expresión throw. Un uso común de este patrón es en macros similares a ASSERT:

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

La solución típica es reemplazar el `void()`argumento non-void por .

Este ejemplo muestra código que genera un error en **/Zc:ternary** y **/Zc:ternary-**:

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

Este código anteriormente daba este error:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Con **/Zc:ternary**, la razón del error se vuelve más clara. Se podría usar cualquiera de varias convenciones de llamada definidas por la implementación para generar cada lambda. Sin embargo, el compilador no tiene ninguna regla de preferencia para desambiguar las posibles firmas lambda. La nueva salida tiene este aspecto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Una fuente común de problemas encontrados por **/Zc:ternary** proviene de operadores condicionales utilizados en la metaprogramación de plantillas. Algunos de los tipos de resultados cambian bajo este Switch. En el ejemplo siguiente se muestran dos casos en los que **/Zc:ternary** cambia el tipo de resultado de una expresión condicional en un contexto que no es de programación meta:

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

La solución típica `std::remove_reference` es aplicar un rasgo en el tipo de resultado, donde sea necesario para conservar el comportamiento anterior.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de**propiedades** **De propiedades** > de configuración**C/C++.** > 

1. Modifique la propiedad **Opciones adicionales** para incluir **/Zc:ternary** o **/Zc:ternary-** y, a continuación, elija **OK**.

## <a name="see-also"></a>Consulte también

[/Zc (Ajuste)](zc-conformance.md)
