---
title: "Utilizar la interoperabilidad de C++ (PInvoke impl&#237;cito) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET [C++], trasladar C++ nativo"
  - "tipos que pueden transferirse en bloque de bits [C++]"
  - "interoperabilidad COM de C++"
  - "interoperabilidad de C++"
  - "C++, interoperabilidad"
  - "interfaces COM [C++]"
  - "cálculo de referencias de datos [C++], características de interoperabilidad de C++"
  - "ejemplos [C++], interoperabilidad"
  - "invocación implícita de plataforma"
  - "interoperabilidad [C++], características"
  - "interoperabilidad [C++]"
  - "interoperabilidad [C++], PInvoke implícito"
  - "calcular las referencias [C++], características de interoperabilidad de C++"
  - "invocación de plataforma [C++], ejemplos"
  - "invocación de plataforma [C++], implícita"
  - "trasladar [C++], C++ nativo a .NET"
  - "tipos [C++], tipo que puede transferirse en bloque de bits"
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar la interoperabilidad de C++ (PInvoke impl&#237;cito)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A diferencia de otros lenguajes de .NET, Visual C\+\+ cuenta con compatibilidad de interoperabilidad que permite que haya código administrado y no administrado en la misma aplicación, e incluso en el mismo archivo \(con las directivas pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md)\).  De este modo, los desarrolladores de Visual C\+\+ pueden integrar la funcionalidad de .NET en las aplicaciones de Visual C\+\+ existentes sin que esto afecte al resto de la aplicación.  
  
 También se puede llamar a funciones no administradas desde una operación de compilación administrada mediante [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
 PInvoke implícito es útil cuando no es necesario especificar cómo se van a calcular las referencias de los parámetros de una función ni cualquiera de los otros detalles que se pueden especificar cuando se llama explícitamente a DllImportAttribute.  
  
 Visual C\+\+ proporciona dos formas de interoperabilidad para las funciones administradas y no administradas:  
  
-   [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 .NET Framework admite PInvoke explícito, que está disponible en la mayoría de los lenguajes de .NET.  Pero, como su propio nombre indica, la interoperabilidad de C\+\+ es específica de Visual C\+\+.  
  
## Interoperabilidad de C\+\+  
 La interoperabilidad de C\+\+ es preferible a PInvoke explícito porque proporciona mejor seguridad de tipos, suele ser menos tediosa de implementar, es más tolerante a las modificaciones de la API no administrada y permite mejoras en el rendimiento que no son posibles con PInvoke explícito.  Sin embargo, la interoperabilidad de C\+\+ no es posible si el código fuente no administrado no está disponible o cuando se compila con **\/clr:safe** \(vea [Código puro y comprobable](../dotnet/pure-and-verifiable-code-cpp-cli.md) para obtener más información\).  
  
## Interoperabilidad COM de C\+\+  
 Las características de interoperabilidad admitidas por Visual C\+\+ ofrecen una ventaja concreta con respecto a otros lenguajes de .NET en lo que se refiere a la interoperabilidad con componentes COM.  En lugar de limitarse a las restricciones del [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) de .NET Framework, como la compatibilidad limitada para tipos de datos y la exposición obligatoria de cada miembro de cada interfaz COM, la interoperabilidad de C\+\+ permite el acceso a voluntad a componentes COM y no requiere ensamblados de interoperabilidad independientes.  Para obtener más información, vea [Using COM from .NET](http://msdn.microsoft.com/es-es/03976661-6278-4227-a6c1-3b3315502c15).  
  
## Tipos que pueden transferirse en bloque de bits  
 Para las API no administradas que usan tipos intrínsecos simples \(vea [Blittable and Non\-Blittable Types](../Topic/Blittable%20and%20Non-Blittable%20Types.md)\), no se requiere una codificación especial porque estos tipos de datos tienen la misma representación en memoria, pero los tipos de datos más complejos requieren el cálculo de referencias de datos explícito.  Para obtener un ejemplo, vea [Cómo: Llamar a archivos DLL nativos desde el código administrado mediante PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).  
  
## Ejemplo  
  
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
  
  **Sonido de inicio**  
**Listo**   
## En esta sección  
  
-   [Cómo: Calcular las referencias de cadenas ANSI mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de cadenas Unicode mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de cadenas COM mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de estructuras mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de matrices mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de devoluciones de llamadas y delegados mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de punteros incrustados mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [Cómo: Tener acceso a caracteres en un objeto System::String](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [Cómo: Convertir char \* String en una matriz System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [Cómo: Convertir System::String en wchar\_t\* o char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [Cómo: Convertir System::String en cadenas estándar](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [Cómo: Convertir cadenas estándar en System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [Cómo: Obtener un puntero a una matriz de bytes](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [Cómo: Cargar recursos no administrados en una matriz de bytes](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [Cómo: Modificar la clase de referencia en una función nativa](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [Cómo: Determinar si una imagen es nativa o CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [Cómo: Agregar un archivo DLL nativo a la memoria caché global de ensamblados](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [Cómo: Mantener la referencia a un tipo de valor en un tipo nativo](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [Cómo: Mantener una referencia a objeto en la memoria no administrada](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [Cómo: Detectar la compilación de \/clr](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [Cómo: Realizar la conversión entre System::Guid y \_GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [Cómo: Especificar un parámetro out](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [Cómo: Utilizar un tipo nativo en una compilación con \/clr](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [Cómo: Declarar controladores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [Cómo: Envolver una clase nativa para utilizarla en C\#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 Para obtener información sobre cómo utilizar delegados en un escenario de interoperabilidad, vea [delegado](../windows/delegate-cpp-component-extensions.md).  
  
## Vea también  
 [Llamar a funciones nativas desde código administrado](../dotnet/calling-native-functions-from-managed-code.md)