---
title: /Zc:ternary (exigir reglas de operador condicional) | Documentos de Microsoft
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
ms.openlocfilehash: 613381795fb962e1f10ec01598748b617b7543aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (exigir reglas de operador condicional)

Habilite el cumplimiento de reglas estándar de C++ para los tipos y const o volatile calificación (cv) de los operandos segundo y terceros de una expresión de operador condicional.

## <a name="syntax"></a>Sintaxis

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>Comentarios

Visual Studio versión 15.3 habilita la compatibilidad del compilador de C++ estándar condicional (o ternario) (operador) (**?:**) comportamiento. El estándar de C++ requiere operandos sea del mismo tipo y cv-calificación, o para un solo operando que inequívocamente convertir en el mismo tipo y cv-calificación que el otro o para uno o ambos operandos ser una expresión throw. En las versiones anteriores de Visual Studio versión 15,5, el compilador permite que las conversiones que se consideran ambiguas por el estándar. Cuando el **/Zc:ternary** se especifica la opción, el compilador se ajusta al estándar y rechaza el código que no cumple las reglas para tipos coincidentes y cv-calificación de los operandos segundo y tercero.

El **/Zc:ternary** opción está desactivada de forma predeterminada. Use **/Zc:ternary** para habilitar el comportamiento conforme, o **/Zc:ternary-** para especificar explícitamente el comportamiento del compilador que no cumple las especificaciones anteriores. El [/ permisivo-](permissive-standards-conformance.md) opción habilita esta opción de forma implícita, pero se puede invalidar usando **/Zc:ternary-**.

### <a name="examples"></a>Ejemplos

Este ejemplo muestra cómo puede producir una clase que proporciona ambos inicialización no explícita de un tipo y la conversión a un tipo conversiones ambiguas. Este código es aceptado por el compilador de forma predeterminada, pero rechazó cuando **/Zc:ternary** o **/ permisivo-** se especifica.

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

La solución requerida consiste en realizar una conversión explícita al tipo de common preferido o impedir que una dirección de conversión de participación en la búsqueda de compilador para una coincidencia de tipo mediante la realización de la conversión explícita.

Una excepción importante a este patrón común es cuando el tipo de los operandos es uno de los tipos de cadena terminada en null, como `const char*`, `const char16_t*`, y así sucesivamente. También puede reproducir con tipos de matriz y Decay () para los tipos de puntero. El comportamiento cuando el segundo o tercer operando real a?: es un literal de cadena de tipo correspondiente depende de la norma del lenguaje que se utiliza. C ++ 17 ha cambiado la semántica para este caso de C ++ 14. Como resultado, el código en el ejemplo siguiente se acepta en **/std:c ++ 14** (el valor predeterminado del compilador), pero es rechazado cuando **/std:c ++ 17** se especifica.

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

Para corregir este código, convertir explícitamente uno de los operandos.

En **/Zc:ternary**, los operadores condicionales de compilador rechaza donde uno de los argumentos es del tipo void y el otro no es una expresión de throw. Un uso común de ellos es en macros de aserción similar:

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

La solución típica es simplemente reemplazar el argumento distinto de void por void().

Este ejemplo muestra código que genera un error en ambos **/Zc:ternary** y **/Zc:ternary-**:

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

Este código que proporcionó anteriormente este error:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Con **/Zc:ternary** el motivo del error se vuelve más claro; en las arquitecturas que cualquiera de varias convenciones de llamada definido por la implementación podría usarse para generar cada expresión lambda, el compilador no expresa ninguna preferencia entre ellas que puede eliminar la ambigüedad de las firmas de lambda posibles. La nueva salida tiene el siguiente aspecto:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Una causa común de problemas relacionados con la adopción de **/Zc:ternary** proceden el uso del operador condicional en plantilla metaprogramación, como cambiar algunos de los tipos de resultado de este conmutador. El ejemplo siguiente muestra dos casos donde **/Zc:ternary** cambia el tipo de resultado de la expresión condicional en un contexto de programación que no son de metadatos:

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

La solución típica en estos casos es aplicar un `std::remove_reference` rasgo en el resultado de tipo cuando sea necesario con el fin de conservar el comportamiento anterior.

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc:ternary** o **/Zc:ternary-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)  
