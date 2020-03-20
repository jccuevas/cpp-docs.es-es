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
ms.openlocfilehash: d26fbefd87b3ba6d6ca7e183be78608777f383b5
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "79545424"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Utilizar la interoperabilidad de C++ (PInvoke implícito)

A diferencia de otros lenguajes de C++ .net, visual tiene compatibilidad de interoperabilidad que permite que el código administrado y no administrado exista en la misma aplicación e incluso en el mismo archivo (con las pragmas [administradas y no administradas](../preprocessor/managed-unmanaged.md) ). De este modo, los desarrolladores de Visual C++ pueden integrar la funcionalidad de .NET en las aplicaciones de Visual C++ existentes sin que esto afecte al resto de la aplicación.

También puede llamar a funciones no administradas desde una operación de compilación administrada mediante [dllexport, DllImport](../cpp/dllexport-dllimport.md).

PInvoke implícito es útil cuando no es necesario especificar cómo se van a calcular las referencias de los parámetros de una función ni cualquiera de los otros detalles que se pueden especificar cuando se llama explícitamente a DllImportAttribute.

Visual C++ proporciona dos formas de interoperabilidad para las funciones administradas y no administradas:

- [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

.NET Framework admite PInvoke explícito, que está disponible en la mayoría de los lenguajes de .NET. Pero, como su propio nombre indica, la interoperabilidad de C++ es específica de Visual C++.

## <a name="c-interop"></a>Interoperabilidad de C++

C++La interoperabilidad proporciona una mejor seguridad de tipos y suele ser menos tediosa de implementar. Sin embargo C++ , la interoperabilidad no es una opción si el código fuente no administrado no está disponible o para proyectos multiplataforma.

## <a name="c-com-interop"></a>Interoperabilidad COM de C++

Las características de interoperabilidad admitidas por Visual C++ ofrecen una ventaja concreta con respecto a otros lenguajes de .NET en lo que se refiere a la interoperabilidad con componentes COM. En lugar de limitarse a las restricciones del .NET Framework [Tlbimp. exe (importador de la biblioteca de tipos)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), como la compatibilidad limitada con los tipos de datos y la exposición obligatoria de cada miembro de cada C++ interfaz com, la interoperabilidad permite tener acceso a los componentes com en y no requiere ensamblados de interoperabilidad independientes. A diferencia de Visual Basic C#y, C++ visual puede usar objetos com directamente mediante los mecanismos de com habituales (como **CoCreateInstance** y **QueryInterface**). Esto es posible debido a C++ las características de interoperabilidad que hacen que el compilador inserte automáticamente el código de transición para pasar de funciones administradas a no administradas y viceversa.

Mediante C++ la interoperabilidad, los componentes com se pueden usar tal como se usan normalmente o se C++ pueden ajustar dentro de las clases. Estas clases contenedoras se denominan contenedores personalizados a los que se puede llamar en tiempo de ejecución, o CRCWs, y tienen dos ventajas sobre el uso de COM directamente en el código de la aplicación:

- La clase resultante se puede usar desde lenguajes distintos de C++visual.

- Los detalles de la interfaz COM se pueden ocultar desde el código de cliente administrado. Los tipos de datos de .NET se pueden usar en lugar de tipos nativos y los detalles del cálculo de referencias de datos se pueden realizar de forma transparente dentro de CRCW.

Independientemente de si COM se usa directamente o a través de un CRCW, se deben calcular las referencias de tipos de argumento distintos de simple.

## <a name="blittable-types"></a>Tipos que pueden transferirse en bloque de bits

En el caso de las API no administradas que usan tipos intrínsecos simples (vea tipos que no pueden transferirse en [bytes y sin](/dotnet/framework/interop/blittable-and-non-blittable-types)bits), no se requiere ninguna codificación especial porque estos tipos de datos tienen la misma representación en la memoria, pero los tipos de datos más complejos requieren un cálculo de referencias de datos explícito. Para obtener un ejemplo, vea [Cómo: llamar a archivos DLL nativos desde el código administrado mediante PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

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

- [Cómo: detectar la compilación/CLR](../dotnet/how-to-detect-clr-compilation.md)

- [Cómo: Realizar la conversión entre System::Guid y _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Cómo: Especificar un parámetro out](../dotnet/how-to-specify-an-out-parameter.md)

- [Cómo: usar un tipo nativo en una compilación/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Cómo: Declarar controladores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md)

- [Cómo: Envolver una clase nativa para usarla en C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Para obtener información sobre el uso de delegados en un escenario de interoperabilidad, vea [Delegate (C++ extensiones de componentes)](../extensions/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Consulte también

- [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)
