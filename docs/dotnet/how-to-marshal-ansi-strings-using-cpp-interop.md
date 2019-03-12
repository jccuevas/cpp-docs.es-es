---
title: Filtrar Serializar cadenas ANSI mediante la interoperabilidad de C++
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: b73d8ed403ab0bbad7703f66f0d8d4ac23bb7766
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748039"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Filtrar Serializar cadenas ANSI mediante la interoperabilidad de C++

Este tema muestra cómo cadenas ANSI se pueden pasar mediante la interoperabilidad de C++, pero .NET Framework <xref:System.String> representa cadenas en formato Unicode, por lo que la conversión a ANSI es un paso adicional. Para interoperar con otros tipos de cadena, vea los temas siguientes:

- [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

Uso de ejemplos de código siguiente el [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma para implementar administrados y las funciones en el mismo archivo, pero estas funciones interoperan de la misma manera, si se definen en archivos independientes. Dado que no es necesario que los archivos que contienen solo las funciones no administradas se compilan con [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md), pueden conservar sus características de rendimiento.

## <a name="example"></a>Ejemplo

En el ejemplo se muestra cómo pasar una cadena ANSI de administrado a una función no administrada mediante <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Este método asigna memoria en el montón no administrado y devuelve la dirección después de realizar la conversión. Esto significa que no es necesario fijar (porque la memoria del montón GC no se pasa a la función no administrada) y que el IntPtr devuelto desde <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> debe liberarse de manera explícita o una memoria perder los resultados.

```
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

El ejemplo siguiente muestra el cálculo de referencias de datos necesarios para tener acceso a una cadena ANSI en una función administrada que llama a una función no administrada. La función administrada, al recibir la cadena nativa, puede usarla directamente o convertirla en una cadena administrada mediante el <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> método, como se muestra.

```
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

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
