---
title: '/ Zc: ternary (exigir reglas de operador condicional) | Microsoft Docs'
ms.date: 3/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:ternary
dev_langs:
- C++
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
author: corob-msft
ms.author: corob
ms.openlocfilehash: a8cd0a4034b07d170bc9ca531d60cce508681a2a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717828"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/ Zc: ternary (exigir reglas de operador condicional)

Habilite el cumplimiento de normas estándar de C++ para los tipos y const o volatile calificación (VC) de los operandos segundo y terceros de una expresión de operador condicional.

## <a name="syntax"></a>Sintaxis

> **/ Zc: ternary**[**-**]

## <a name="remarks"></a>Comentarios

Versión 15.3 de Visual Studio permite la compatibilidad del compilador para el operador condicional (o ternario) estándar del C++ (**?:**) comportamiento. El estándar de C++ requiere operandos que ser del mismo tipo y cv-calificación o para un solo operando inequívocamente convertible en el mismo tipo y la calificación de VC como el otro para uno o ambos operandos sea una expresión throw. En las versiones anteriores de la versión 15.5 de Visual Studio, el compilador permitía las conversiones que se consideran ambiguas por el estándar. Cuando el **/Zc: ternary** se especifica la opción, el compilador se ajusta al estándar y rechaza el código que no cumple las reglas de los tipos coincidentes y cv-calificación de los operandos segundo y terceros.

El **/Zc: ternary** opción está desactivada de forma predeterminada. Use **/Zc: ternary** para habilitar el comportamiento que cumplen las especificaciones, o **/Zc:ternary-** especificar explícitamente el comportamiento del compilador anterior no es conforme. El [/ permissive-](permissive-standards-conformance.md) opción habilita esta opción de forma implícita, pero se pueden invalidar utilizando **/Zc:ternary-**.

### <a name="examples"></a>Ejemplos

Este ejemplo muestra cómo puede producir una clase que proporciona ambos inicialización no explícita de un tipo y la conversión a un tipo conversiones ambiguas. Este código está aceptado por el compilador de forma predeterminada, pero se rechaza cuando **/Zc: ternary** o **/ permissive-** se especifica.

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

La corrección necesaria es realizar una conversión explícita al tipo de common preferido o evitar que una dirección de la conversión de la participación en la búsqueda del compilador para una coincidencia de tipo mediante la realización de la conversión explícita.

Una excepción importante a este patrón común es cuando el tipo de los operandos es uno de los tipos de cadena terminada en null, como `const char*`, `const char16_t*`, y así sucesivamente. También puede reproducir con tipos de matriz y los tipos de puntero que decaer a. El comportamiento cuando el segundo o tercer operando real para?: es el estándar del lenguaje utilizado depende de un literal de cadena del tipo correspondiente. C ++ 17 ha cambiado la semántica para este caso de C ++ 14. Como resultado, el código en el ejemplo siguiente se acepta en **/std: c ++ 14** (el valor predeterminado del compilador), pero es rechazado cuando **/std: c ++ 17** se especifica.

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

Para corregir este código, convierta explícitamente uno de los operandos.

En **/Zc: ternary**, el compilador rechaza los operadores condicionales donde uno de los argumentos es de tipo void y el otro no es una expresión throw. Un uso común de estos es en las macros de aserción similar:

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

La solución típica consiste en simplemente reemplace el argumento distinto de void void().

En este ejemplo se muestra código que genera un error en ambos **/Zc: ternary** y **/Zc:ternary-**:

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

Este código previamente concedió este error:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Con **/Zc: ternary** se vuelve más claro el motivo del error; en las arquitecturas que cualquiera de las varias convenciones de llamada definido por la implementación podría usarse para generar cada lambda, el compilador no expresa ninguna preferencia entre ellos que pudo eliminar la ambigüedad de las firmas posibles lambda. La nueva salida tendrá este aspecto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Una fuente de problemas comunes relacionados con la adopción de **/Zc: ternary** procede el uso del operador condicional en la plantilla de metaprogramación, como cambiar algunos de los tipos de resultado de este conmutador. El ejemplo siguiente muestra dos casos donde **/Zc: ternary** cambia el tipo de resultado de la expresión condicional en un contexto de programación que no son de metadatos:

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

La resolución estándar en estos casos es aplicar un `std::remove_reference` rasgo en el resultado de tipo cuando sea necesario para conservar el comportamiento anterior.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: ternary** o **/Zc:ternary-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)
