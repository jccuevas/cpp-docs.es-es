---
title: 'Cómo: serializar cadenas ANSI mediante la interoperabilidad de C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: 6987b23311354cfe6fd095e0e811d043e9b9692e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545256"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Cómo: serializar cadenas ANSI mediante la interoperabilidad de C++

En este tema se muestra cómo se pueden pasar cadenas C++ ANSI mediante la interoperabilidad, pero el .NET Framework <xref:System.String> representa cadenas en formato Unicode, por lo que la conversión a ANSI es un paso adicional. Para interoperar con otros tipos de cadena, vea los temas siguientes:

- [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

En los siguientes ejemplos de código se usan las directivas de #pragma [administradas y no administradas](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero estas funciones interoperan de la misma manera si se definen en archivos independientes. Dado que los archivos que contienen solo funciones no administradas no necesitan compilarse con [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), pueden conservar sus características de rendimiento.

## <a name="example"></a>Ejemplo

En el ejemplo se muestra cómo pasar una cadena ANSI desde una función administrada a una función no administrada mediante <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Este método asigna memoria en el montón no administrado y devuelve la dirección después de realizar la conversión. Esto significa que no se requiere ningún anclaje (dado que la memoria del montón GC no se pasa a la función no administrada) y que el IntPtr devuelto de <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> se debe liberar explícitamente o que se produzca una pérdida de memoria.

```cpp
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el cálculo de referencias de datos necesario para tener acceso a una cadena ANSI en una función administrada a la que llama una función no administrada. La función administrada, al recibir la cadena nativa, puede usarla directamente o convertirla en una cadena administrada mediante el método <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>, como se muestra.

```cpp
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
