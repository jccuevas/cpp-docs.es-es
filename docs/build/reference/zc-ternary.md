---
title: /Zc:ternary (Exigir reglas de operador condicionales)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 5c38a09b92b4173ca962412a413abc283db590ff
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927505"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (Exigir reglas de operador condicionales)

Habilitar la aplicación C++ de reglas estándar para los tipos y la calificación const o volatile (CV) de los operandos segundo y tercero en una expresión de operador condicional.

## <a name="syntax"></a>Sintaxis

> **/Zc: ternario** [ **-** ]

## <a name="remarks"></a>Comentarios

A partir de Visual Studio 2017, el compilador admite C++ el comportamiento de *operador condicional* estándar ( **?:** ). También se conoce como el *operador ternario*. El C++ estándar requiere operandos ternarios que cumplan una de estas tres condiciones: Los operandos deben ser del mismo tipo y de una calificación **const** o **volatile** (la calificación CV), o solo un operando debe ser convertible de forma no ambigua al mismo tipo y a la clasificación CV que el otro. O bien, uno o ambos operandos deben ser una expresión Throw. En las versiones anteriores a Visual Studio 2017 versión 15,5, el compilador permitía conversiones que el estándar considera ambiguas.

Cuando se especifica la opción **/Zc: ternario** , el compilador se ajusta al estándar. Rechaza el código que no cumple las reglas de los tipos coincidentes y la calificación CV de los operandos segundo y tercero.

La opción **/Zc: ternaria** está desactivada de forma predeterminada en Visual Studio 2017. Use **/Zc: ternario** para habilitar el comportamiento de ajuste, o **/Zc: ternario** para especificar explícitamente el comportamiento anterior del compilador no compatible. La opción [/permissive-](permissive-standards-conformance.md) habilita implícitamente esta opción, pero se puede invalidar mediante **/Zc: ternaria-** .

### <a name="examples"></a>Ejemplos

Este ejemplo muestra cómo una clase que proporciona la inicialización no explícita desde un tipo y la conversión a un tipo, puede conducir a conversiones ambiguas. El compilador acepta este código de forma predeterminada, pero se rechaza cuando se especifica **/Zc: ternario** o **/permissive-** .

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

Para corregir este código, realice una conversión explícita al tipo común preferido o Evite una dirección de conversión de tipos. Puede evitar que el compilador coincida con una conversión de tipos haciendo que la conversión sea explícita.

Una excepción importante a este patrón común es cuando el tipo de los operandos es uno de los tipos de cadena terminada en null, como `const char*`, `const char16_t*`, etc. También puede reproducir el efecto con tipos de matriz y los tipos de puntero en los que se decaigan. El comportamiento cuando el segundo o el tercer operando `?:` real es un literal de cadena del tipo correspondiente depende del estándar del lenguaje utilizado. En este caso, c++ 17 ha cambiado la semántica de C++ 14. Como resultado, el compilador acepta el código del ejemplo siguiente en el **/STD predeterminado: c++ 14**, pero lo rechaza cuando se especifica **/STD: c++ 17**.

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

En **/Zc: ternario**, el compilador rechaza los operadores condicionales en los que uno de los argumentos es de tipo **void**y el otro no es una expresión Throw. Un uso común de este patrón es en macros similares a las de ASERCIÓN:

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

La solución típica es reemplazar el argumento no void por `void()`.

Este ejemplo muestra el código que genera un error en las dos opciones **/Zc: ternaria** y **/Zc: ternario-** :

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

Este código dio este error anteriormente:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Con **/Zc: ternario**, el motivo del error se vuelve más claro. Se puede utilizar cualquiera de las distintas convenciones de llamada definidas por la implementación para generar cada expresión lambda. Sin embargo, el compilador no tiene ninguna regla de preferencias para eliminar la ambigüedad de las posibles firmas lambda. La nueva salida tiene el siguiente aspecto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Una fuente común de problemas encontrados por **/Zc: ternario** procede de los operadores condicionales usados en la Metaprogramación de la plantilla. Algunos de los tipos de resultados cambian en este modificador. En el ejemplo siguiente se muestran dos casos en los que **/Zc: ternaria** cambia el tipo de resultado de una expresión condicional en un contexto que no es de Metaprogramación:

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

La solución típica es aplicar un `std::remove_reference` rasgo en el tipo de resultado, donde sea necesario para conservar el comportamiento anterior.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **Línea de comandos**.

1. Modifique la propiedad **opciones adicionales** para incluir **/Zc: ternario** o **/Zc: ternario** y, después, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)
