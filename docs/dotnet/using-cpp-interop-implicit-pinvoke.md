---
title: "Mediante la interoperabilidad de C++ (PInvoke implícito) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 78d104a41f052f994a19ebe359c8d3e557274783
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="using-c-interop-implicit-pinvoke"></a>Utilizar la interoperabilidad de C++ (PInvoke implícito)
A diferencia de otros lenguajes. NET, Visual C++ tiene compatibilidad con esta interoperabilidad que permite que el código administrado y que existe en la misma aplicación e incluso en el mismo archivo (con la [managed, unmanaged](../preprocessor/managed-unmanaged.md) pragma (directivas)). De este modo, los desarrolladores de Visual C++ pueden integrar la funcionalidad de .NET en las aplicaciones de Visual C++ existentes sin que esto afecte al resto de la aplicación.  
  
 También puede llamar a funciones no administradas desde una operación de compilación administrada mediante [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
 PInvoke implícito es útil cuando no es necesario especificar cómo se van a calcular las referencias de los parámetros de una función ni cualquiera de los otros detalles que se pueden especificar cuando se llama explícitamente a DllImportAttribute.  
  
 Visual C++ proporciona dos formas de interoperabilidad para las funciones administradas y no administradas:  
  
-   [Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 .NET Framework admite PInvoke explícito, que está disponible en la mayoría de los lenguajes de .NET. Pero, como su propio nombre indica, la interoperabilidad de C++ es específica de Visual C++.  
  
## <a name="c-interop"></a>Interoperabilidad de C++  
 La interoperabilidad de C++ es preferible a PInvoke explícito porque proporciona mejor seguridad de tipos, suele ser menos tediosa de implementar, es más tolerante a las modificaciones de la API no administrada y permite mejoras en el rendimiento que no son posibles con PInvoke explícito. Sin embargo, la interoperabilidad de C++ no es posible si el código fuente no administrado no está disponible.  
  
## <a name="c-com-interop"></a>Interoperabilidad COM de C++  
 Las características de interoperabilidad admitidas por Visual C++ ofrecen una ventaja concreta con respecto a otros lenguajes de .NET en lo que se refiere a la interoperabilidad con componentes COM. En lugar de limitarse a las restricciones de .NET Framework [Tlbimp.exe (importador de la biblioteca de tipos)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), como la compatibilidad limitada para los tipos de datos y la exposición obligada de cada miembro de cada interfaz COM, la interoperabilidad de C++ permite COM componentes para acceder a él creará y no requiere ensamblados de interoperabilidad independientes. Para obtener más información, consulte [Using COM desde .NET](http://msdn.microsoft.com/en-us/03976661-6278-4227-a6c1-3b3315502c15).  
  
## <a name="blittable-types"></a>Tipos que pueden transferirse en bloque de bits  
 Para las API no administradas que usan tipos intrínsecos simples (vea [bits/bytes y tipos no](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3)), no se requiere ninguna codificación especial porque estos tipos de datos tienen la misma representación en memoria, pero requieren tipos de datos más complejos serialización de datos explícitos. Para obtener un ejemplo, vea [Cómo: llamar a DLL nativas de PInvoke de uso de código administrado](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
-   [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [Cómo: Serializar estructuras mediante la interoperabilidad de C++](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [Cómo: Serializar matrices mediante la interoperabilidad de C++](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [Cómo: Serializar devoluciones de llamadas y delegados mediante la interoperabilidad de C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [Cómo: Serializar punteros insertados mediante la interoperabilidad de C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [Cómo: Tener acceso a caracteres en un objeto System::String](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [Cómo: Convertir char * String en una matriz System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [Cómo: convertir System:: String en wchar_t * o char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [Cómo: Convertir System::String en cadenas estándar](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [Cómo: Convertir cadenas estándar en System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [Cómo: Obtener un puntero a una matriz de bytes](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [Cómo: Cargar recursos no administrados en una matriz de bytes](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [Cómo: Modificar la clase de referencia en una función nativa](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [Cómo: Determinar si una imagen es nativa o CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [Cómo: Agregar un archivo DLL nativo a la memoria caché global de ensamblados](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [Cómo: Mantener la referencia a un tipo de valor en un tipo nativo](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [Cómo: Mantener una referencia a objeto en la memoria no administrada](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [Cómo: detectar la compilación de /clr](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [Cómo: Realizar la conversión entre System::Guid y _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [Cómo: Especificar un parámetro out](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [Cómo: usar un tipo nativo en una compilación con /clr](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [Cómo: Declarar controladores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [Cómo: Envolver una clase nativa para usarla en C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 Para obtener información sobre cómo usar delegados en un escenario de interoperabilidad, consulte [delegate (extensiones de componentes de C++)](../windows/delegate-cpp-component-extensions.md).  
  
## <a name="see-also"></a>Vea también  
 [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)