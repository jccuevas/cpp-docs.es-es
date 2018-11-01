---
title: Utilizar la interoperabilidad de C++ (PInvoke implícito)
ms.date: 11/04/2016
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
ms.openlocfilehash: ffe4aaeecc3e0f65851a87840cd21f81c4806fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464596"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Utilizar la interoperabilidad de C++ (PInvoke implícito)

A diferencia de otros lenguajes. NET, Visual C++ tiene compatibilidad de interoperabilidad que permite que exista código administrado y en la misma aplicación e incluso en el mismo archivo (con el [managed, unmanaged](../preprocessor/managed-unmanaged.md) pragmas). De este modo, los desarrolladores de Visual C++ pueden integrar la funcionalidad de .NET en las aplicaciones de Visual C++ existentes sin que esto afecte al resto de la aplicación.

También puede llamar a funciones no administradas desde una operación de compilación administrada mediante [dllexport, dllimport](../cpp/dllexport-dllimport.md).

PInvoke implícito es útil cuando no es necesario especificar cómo se van a calcular las referencias de los parámetros de una función ni cualquiera de los otros detalles que se pueden especificar cuando se llama explícitamente a DllImportAttribute.

Visual C++ proporciona dos formas de interoperabilidad para las funciones administradas y no administradas:

- [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

.NET Framework admite PInvoke explícito, que está disponible en la mayoría de los lenguajes de .NET. Pero, como su propio nombre indica, la interoperabilidad de C++ es específica de Visual C++.

## <a name="c-interop"></a>Interoperabilidad de C++

La interoperabilidad de C++ es preferible a PInvoke explícito porque proporciona mejor seguridad de tipos, suele ser menos tediosa de implementar, es más tolerante a las modificaciones de la API no administrada y permite mejoras en el rendimiento que no son posibles con PInvoke explícito. Sin embargo, la interoperabilidad de C++ no es posible si el código fuente no administrado no está disponible.

## <a name="c-com-interop"></a>Interoperabilidad COM de C++

Las características de interoperabilidad admitidas por Visual C++ ofrecen una ventaja concreta con respecto a otros lenguajes de .NET en lo que se refiere a la interoperabilidad con componentes COM. En lugar de limitarse a las restricciones de .NET Framework [Tlbimp.exe (importador de biblioteca)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), como la compatibilidad limitada para tipos de datos y la exposición obligatoria de todos los miembros de cada interfaz COM, interoperabilidad de C++ permite que COM acceder a los componentes se y no requiere ensamblados de interoperabilidad independientes. A diferencia de Visual Basic y C#, Visual C++ puede utilizar objetos COM directamente mediante los mecanismos de COM habituales (como **CoCreateInstance** y **QueryInterface**). Esto es posible debido a las características de interoperabilidad de C++ que hacen que el compilador insertar automáticamente el código de transición para mover de administrado los funciones y viceversa.

Mediante la interoperabilidad de C++, componentes COM pueden utilizarse como normalmente se usan o pueden colocarse dentro de las clases de C++. Estas clases contenedoras se denominan contenedores RCW personalizado o CRCW y tienen dos ventajas con respecto a COM directamente en el código de aplicación:

- La clase resultante se puede utilizar en lenguajes distintos de Visual C++.

- Pueden ocultar los detalles de la interfaz COM desde el código de cliente administrado. Tipos de datos de .NET pueden usarse en lugar de tipos nativos y los detalles de la serialización de datos pueden realizarse de forma transparente dentro de CRCW.

Independientemente de si se usa COM directamente o a través de CRCW, se deben serializar los tipos de argumento que no sean de tipos simples.

## <a name="blittable-types"></a>Tipos que pueden transferirse en bloque de bits

Para las API no administradas que usan tipos intrínsecos simples (vea [Non-bits/bytes tipos](/dotnet/framework/interop/blittable-and-non-blittable-types)), no se requiere ninguna codificación especial porque estos tipos de datos tienen la misma representación en memoria, pero requieren tipos de datos más complejos serialización de datos explícitos. Para obtener un ejemplo, vea [Cómo: llamar a archivos DLL nativos desde administrado código Using PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

## <a name="example"></a>Ejemplo

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>En esta sección

- [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [Cómo: Serializar estructuras mediante la interoperabilidad de C++](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [Cómo: Serializar matrices mediante la interoperabilidad de C++](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [Cómo: Serializar devoluciones de llamadas y delegados mediante la interoperabilidad de C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [Cómo: Serializar punteros insertados mediante la interoperabilidad de C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [Cómo: Tener acceso a caracteres en un objeto System::String](../dotnet/how-to-access-characters-in-a-system-string.md)

- [Cómo: Convertir char * String en una matriz System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [Cómo: convertir System:: String en wchar_t * o char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Cómo: Convertir System::String en cadenas estándar](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Cómo: Convertir cadenas estándar en System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Cómo: Obtener un puntero a una matriz de bytes](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Cómo: Cargar recursos no administrados en una matriz de bytes](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Cómo: Modificar la clase de referencia en una función nativa](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Cómo: Determinar si una imagen es nativa o CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Cómo: Agregar un archivo DLL nativo a la memoria caché global de ensamblados](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Cómo: Mantener la referencia a un tipo de valor en un tipo nativo](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Cómo: Mantener una referencia a objeto en la memoria no administrada](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Cómo: detectar la compilación de /clr](../dotnet/how-to-detect-clr-compilation.md)

- [Cómo: Realizar la conversión entre System::Guid y _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Cómo: Especificar un parámetro out](../dotnet/how-to-specify-an-out-parameter.md)

- [Cómo: usar un tipo nativo en una compilación con /clr](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Cómo: Declarar controladores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md)

- [Cómo: Envolver una clase nativa para usarla en C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Para obtener información sobre el uso de delegados en un escenario de interoperabilidad, vea [delegate (extensiones de componentes de C++)](../windows/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Vea también

- [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)
